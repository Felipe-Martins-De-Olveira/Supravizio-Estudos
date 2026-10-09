# Imports, DGCO, Excel e CSV

Atualização: 09/10/2026. Explicações generalizadas do estudo dos XMLs, sem reproduzir scripts ou cadastros internos. Os fragmentos de código são didáticos; não foram executados no Supravizio.

## Imports encontrados

Nos 1.440 corpos aceitos pelo parser foram contadas **4.472 declarações de importação**, com **33 módulos distintos**, distribuídas em **1.385 corpos com imports**. Separadamente, houve **870 chamadas AddReference**, citando **6 assemblies distintos**. Os sete corpos com falha de parse não estão incluídos nessa contagem.

Exemplos de módulos encontrados: `clr`, `System`, `System.Data`, `System.Text`, `System.Net.Http`, `System.Net.Http.Headers`, `Newtonsoft.Json`, `Newtonsoft.Json.Linq`, `re`, `datetime` e namespaces customizados do Supravizio.

Imports Python e referências a assemblies .NET não são a mesma medida. Repetição de import não significa biblioteca diferente. Alguns cabeçalhos são gerados pelo editor; não removê-los nem classificá-los automaticamente como erro.

Fragmento didático para consulta e serialização, exigindo configuração do host:

```python
import clr
clr.AddReference("System.Data")
clr.AddReference("Newtonsoft.Json")
from Newtonsoft.Json import JsonConvert

# DB é fornecido pelo contexto correspondente do Supravizio.
# consulta_resultado representa uma DataTable já obtida nesse contexto.
# texto_json = JsonConvert.SerializeObject(consulta_resultado)
```

## DGCO

A busca sem distinção de maiúsculas encontrou **53 corpos distintos contendo DGCO**: 5 LookupScript, 20 Source, 12 ScriptFormCarregado, 6 ScriptModificado, 9 ScriptInicio e 1 ScriptValidacao. Com a grafia exata DCGO, não houve ocorrência.

Foram identificadas funções de consulta, consulta de detalhes e solicitação de reserva. Elas são auxiliares exportadas, não APIs nativas garantidas pelo nome. A assinatura, variante e efeitos devem ser conferidos antes de chamar.

O exemplo de consulta estudado recebe número da OS, consulta o identificador vinculado e serializa a DataTable em JSON. Em exceção, retorna texto de erro. É importante distinguir JSON de sucesso e texto de erro no consumidor.

Representação didática desse contrato, sem consulta ou esquema empresarial:

```python
# Esboço conceitual: não é código pronto nem assinatura nativa.
# 1. Validar o número da OS conforme seu tipo real.
# 2. Consultar a fonte autorizada configurada no ambiente.
# 3. Tratar resultado vazio e múltiplas linhas.
# 4. Serializar o resultado, ou retornar erro distinguível.
# 5. Não criar reserva nem avançar atividade durante uma mera consulta.
```

Uma função de reserva pode criar OS, preencher dados, salvar e solicitar transição; sua reutilização exige conferir serviço/modelo, pessoas, permissões, falhas parciais e duplicidade. Consulta e reserva são operações diferentes.

## Excel

Foram encontrados **dois ScriptModificado com referência explícita a Excel**, usando `Microsoft.ACE.OLEDB.12.0`. O padrão de leitura de um deles é:

1. Verificar acionamento do controle e existência do anexo.
2. Resolver o arquivo no repositório configurado.
3. Abrir conexão OleDb com propriedades Excel.
4. Consultar a aba com cabeçalhos e filtrar linhas relevantes.
5. Tratar None/DBNull, texto, classificação e data.
6. Adicionar linhas ao grid da OS.
7. Fechar conexão e apresentar resumo de lidas, adicionadas e erros.

Fragmento generalizado da técnica de leitura, que depende dos assemblies e do provider instalado:

```python
import clr
clr.AddReference("System.Data")
from System.Data import DataSet
from System.Data.OleDb import OleDbConnection, OleDbDataAdapter
from System import String

# caminho_arquivo deve ser resolvido e validado no ambiente real.
# Nomes da aba e colunas são exemplos, não os cadastros da empresa.
conexao_texto = String.Format(
    "Provider=Microsoft.ACE.OLEDB.12.0;Data Source={0};"
    "Extended Properties='Excel 12.0 Xml;HDR=YES;IMEX=1';",
    caminho_arquivo
)
conexao = OleDbConnection(conexao_texto)
adapter = OleDbDataAdapter(
    "SELECT [CODIGO], [CLASSIFICACAO], [DATA] FROM [DADOS$] "
    "WHERE [CODIGO] IS NOT NULL",
    conexao
)
dados = DataSet()
try:
    conexao.Open()
    adapter.Fill(dados)
    # Tratar dados.Tables[0].Rows e mapear para o grid real.
finally:
    conexao.Close()
```

Este fragmento não inclui resolução de anexo, validação completa, adição ao grid, persistência ou descarte de todos os recursos. Não colar em produção como rotina pronta. O driver instalado e sua arquitetura precisam ser compatíveis com o processo que executa o script; esta dependência não foi testada.

Conferir especialmente:

- Código textual com zeros à esquerda e inferência de tipo do OleDb.
- Datas tipadas versus texto e formato/cultura.
- Aba inexistente, cabeçalho diferente, planilha vazia e anexo ausente.
- Linha inválida e comportamento de importação parcial.
- Duplicação ao acionar a importação novamente.
- Regras particulares fixas da versão, que não devem ser generalizadas.
- Resumo de conclusão que não esconda falha total ou contabilize como busca algo que não foi feito.

## CSV

A busca por referências explícitas a CSV não encontrou exemplo na coleção examinada. Isso não prova ausência de todas as rotinas que poderiam tratar texto delimitado: uma delas pode não usar a palavra CSV.

Não apresentar o leitor OleDb de Excel como leitor CSV. Uma implementação nova exige definir separador, encoding/BOM, aspas, cabeçalhos, datas, decimais, linhas inválidas e contrato do grid, além de confirmar bibliotecas disponíveis no IronPython do ambiente.
