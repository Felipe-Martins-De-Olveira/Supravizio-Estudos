# Conhecimento de scripts Supravizio

Publicado em 09/10/2026, com base no estudo local de 08/10/2026 e nas consultas posteriores. Esta é uma síntese para continuidade e orientação de outras IAs. Nomes de cadastros, esquemas, dados operacionais e código empresarial foram generalizados; os originais permanecem locais.

## Cobertura real

| Medida | Quantidade | Limite |
|---|---:|---|
| Corpos distintos de scripts e expressões | 1.447 | Não é quantidade de arquivos XML |
| Análise estática estruturada | 1.447 | Não comprova execução ou leitura literal integral |
| Leitura direta do corpo executável registrada | 983 | Alguns lotes omitem comentários, cabeçalhos e autenticação |
| Sem leitura literal integral registrada | 464 | Perfis estruturados revisados; não anunciar auditoria integral |
| Unidades distintas de função/classe com perfil revisado | 319 | Deduplicação estrutural não elimina diferenças de contexto e globais |
| Nomes de bibliotecas / variantes exportadas | 69 / 109 | Presença na exportação não comprova uso pelo fluxo |
| Observações conferidas nesta rodada | 32 | Possíveis problemas e cenários; não são falhas comprovadas em produção |
| Corpos aceitos pelo parser / falhas | 1.440 / 7 | Parser CPython não valida compatibilidade IronPython |
| Execuções de scripts no Supravizio | 0 | Validação funcional depende de acesso ao ambiente de testes |

Os relatórios antigos são históricos. Não somar seus achados aos desta rodada como se não houvesse sobreposição. A revisão literal e a validação funcional continuam parciais.

## Escolher o contexto antes de escrever

| Local | Papel observado | Conferência necessária |
|---|---|---|
| ScriptInicio | Preparar dados/atividade e eventualmente solicitar avanço | Reentrada, gravação e efeitos repetidos |
| ScriptFormCarregado | Preparar controles e listas | Alguns exemplos também alteram/salvam a OS |
| ScriptModificado | Reagir à alteração de campo | Vazio, None, tipo e dependências entre controles |
| LookupScript | Produzir Itens para opções | Identificador armazenado, rótulo exibido e retorno vazio |
| ScriptSelecaoAtores | Selecionar pessoas para papel/atividade | Pessoa versus fila/órgão; zero e múltiplos resultados |
| ScriptEvento | Preparar mensagem ou dados do evento | Momento, destinatários e configuração do fluxo |
| Expressões de gateway | Selecionar saída | Código, comparador, alternativa e destino |
| Source de biblioteca | Disponibilizar auxiliares | Import, assinatura, variante e contexto do host |

Uma comparação isolada é esperada em uma propriedade de expressão. Em um script operacional, comparar um campo com um texto não atribui esse texto ao campo. O contexto evita esse falso diagnóstico.

## Formulários, registros e OS

- `Formulario` representa controles do formulário; `FormularioRegistro` representa controles de uma linha/registro.
- `.Valor`, `.Visivel`, `.Habilitado` e `.Itens` têm responsabilidades distintas. Ocultar não limpa automaticamente; limpar pode apagar informação relevante.
- `OrdemServico.GetCustom` e `SetCustom` acessam dados customizados. Não confundir o controle exibido com o favorecido/cliente/responsável nativo.
- Lookups com DataTable normalmente armazenam a primeira coluna e exibem a segunda, conforme a documentação local. Confirmar o contrato de listas e tabelas com mais colunas na instalação.
- Grids são percorridos por `.Rows` nos exemplos correspondentes. Conferir None, tabela vazia, DBNull, tipos e nomes técnicos das colunas.
- Uma variável definida somente dentro de um laço pode ficar sem definição com zero linhas. Adicionar registros sem limpeza ou chave de duplicidade pode repetir dados na reentrada.
- Valores de opção, IDs de pessoa, matrícula, número de OS, ID de ocorrência e sigla de órgão não são intercambiáveis.

## Aprovação e validação

Responsável da tarefa, aprovadores e quantidade de aprovações são configurações diferentes. O gateway interpreta o resultado de aprovação; a solicitação de avanço da tarefa pertence ao contexto apropriado. Consultar também [Toolbox, aprovação e scripts](../../estudo-chm/TOOLBOX-APROVACAO-SCRIPTS.md).

Os exemplos contêm `AvancaProximaAtividade = True` em ScriptInicio. Isso não realiza uma aprovação nem garante conclusão do processo. Reprovação e aprovação pendente não são equivalentes. Motivos e cancelamento de rodada dependem dos códigos reais da tarefa/gateway.

`Formulario.ExibeMensagem` é aviso de interface; não anunciar como pendência impeditiva sem confirmar a API de validação e o contexto. Não inventar assinatura de método pelo nome de uma biblioteca auxiliar.

## Bibliotecas e integrações

O estudo encontrou famílias de consulta de solicitações, contratos, fornecedores, reserva de identificadores, notas fiscais, RH, calendário, deslocamento, acesso, incidentes e pagamentos. Algumas apenas consultam; outras criam OS, atualizam banco, anexam arquivos e solicitam transições.

Antes de reutilizar uma função, ler sua implementação e consumidores. Verificar entradas, saída, configuração de ambiente, efeitos e tratamento de falha. Uma função pode retornar objeto/JSON em sucesso e texto em erro; o consumidor precisa distinguir os casos. Nome como teste não garante ausência de efeitos.

HTTP: `.Wait()` e timeout não comprovam sucesso; verificar status, resposta vazia, JSON inválido e falha de rede. Falhas parciais e chamadas repetidas precisam de contrato de idempotência. O helper que retorna False só protege se o chamador tratar esse retorno.

Anexos: preservar bytes de arquivos binários antes de Base64, conferir nome de arquivo, diretório e concorrência. Ler PDF como texto e recodificar pode alterar o conteúdo. Nome temporário fixo pode causar sobreposição entre solicitações.

Calendários e cálculos: conferir intervalo inclusivo, feriado no fim de semana, horas limite, datas vazias/invertidas e Decimal. Tarifas fixas encontradas são históricas da exportação, não prova de política vigente. Funções com mesma estrutura podem usar globais diferentes.

## Banco e SQL

`DB.ExecuteDataTable` retorna tabela; `ExecuteScalar` retorna escalar; `ExecuteNonQuery` é operação de gravação com quantidade de linhas afetadas, conforme documentação. A conexão precisa corresponder ao cadastro real. Não executar comandos durante o estudo documental.

Examinar cardinalidade, ordenação, joins por identificador versus nome, vigência e precedência AND/OR. Consulta efetiva por data pode precisar excluir registros futuros. Concatenação de valores exige cuidado com aspas e tipos; confirmar suporte de parametrização antes de propor assinatura.

Há scripts que obtêm texto SQL de um parâmetro no banco e depois o executam. O XML mostra essa dependência, mas não contém necessariamente a consulta guardada no servidor. Stored procedures e globais externos também exigem fontes adicionais.

## Padrões de problema conferidos

1. Comparação em vez de atribuição a campo.
2. Referência a método sem parênteses, sem invocação.
3. Teste de valor diferente de vazio OU diferente de None que aceita ausência.
4. OR contendo texto não vazio em lugar de outra comparação.
5. Dois if que desfazem a alteração de visibilidade no mesmo evento.
6. Variável ou URL usada com nome diferente da inicialização/parâmetro.
7. Contador que soma a si mesmo em lugar de incrementar um.
8. Acesso à primeira linha sem conferir resultado.
9. Acúmulo de linhas ou texto ao reexecutar a atividade.
10. Carga do formulário limpando indiscriminadamente controles.
11. Gravações separadas sem transação explícita no corpo e retorno de sucesso sem ação.
12. Token misturado com string JSON de erro; falha de anexo ignorada antes do avanço.
13. Faixa etária obtida por posição de um split de texto; cultura decimal indefinida.
14. Feriado de fim de semana entrando em duas parcelas do cálculo.
15. Indentação, código concatenado ou bloco except sem corpo executável.

Esses padrões são evidência estática de trechos específicos, não diagnóstico universal de todos os scripts. Imports gerados pelo editor, comparações de gateway e proteções de tabela None podem ser legítimos. Conferir contexto antes de classificar.

## Roteiro para outra IA

1. Ler README, AGENTS, guia do produto, aulas e este documento.
2. Localizar serviço, versão, atividade/operação, controle e campo técnico da demanda.
3. Separar documentação, evidência do XML, inferência e teste realmente executado.
4. Consultar a fonte local completa do caso antes de entregar código adaptado.
5. Explicar entradas, efeitos, retorno e onde colocar o script.
6. Conferir aprovação/reprovação, vazio, None/DBNull, zero/múltiplas linhas, reentrada, falhas HTTP e anexos no ambiente autorizado.
7. Preservar originais e registrar o resultado, sem alegar validação apenas por leitura ou parse.

Veja [imports, DGCO, Excel e CSV](EXEMPLOS-DGCO-EXCEL-IMPORTS.md) e [cobertura agregada](COBERTURA.json).
