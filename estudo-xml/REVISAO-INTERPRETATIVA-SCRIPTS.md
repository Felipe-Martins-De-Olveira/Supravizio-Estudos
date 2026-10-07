# Revisão interpretativa dos scripts exportados

Até 07/10/2026: 294 de 1447 corpos executáveis examinados individualmente; 1153 ainda pendentes. Todos os 1447 tiveram auditoria estática automatizada. Nenhum foi executado no Supravizio.

As constatações descrevem o código exportado. Um módulo global presente no XML não comprova que seja chamado pelo fluxo. Compatibilidade com CPython 3 não comprova compatibilidade com IronPython. Comentários e linhas de autenticação foram omitidos da leitura dos corpos; este documento não certifica segurança integral.

## Achados e testes futuros

### Condição de grade vazia impossível


- Evidência: Rows.Count < 0 nunca identifica uma grade vazia, pois a contagem é não negativa.
- Validação futura: Testar grade com zero e uma linha; conferir a regra esperada.

### Limite de caracteres divergente


- Evidência: Código exige 150 caracteres; mensagem informa 100.
- Validação futura: Testar textos com 99, 100, 149 e 150 caracteres e definir o limite correto.

### Expressão de grade com or


- Evidência: A expressão retorna o primeiro valor verdadeiro e pode acessar até Rows[10] sem conferir quantidade de linhas.
- Validação futura: Testar zero, uma e onze linhas, incluindo valores vazios; verificar objetivo da decisão.

### Biblioteca integração A: except vazio


- Evidência: O bloco except contém somente comentários; lst também é usado com a atribuição comentada.
- Validação futura: Confirmar uso da biblioteca e escopo de lst; corrigir em cópia antes de carregar.

### Variante integração A: except vazio


- Evidência: Mesma falha de bloco vazio e variável lst da outra variante.
- Validação futura: Comparar versões e identificar qual biblioteca está ativa.

### Biblioteca integração B: instruções concatenadas


- Evidência: Chamadas e import foram unidos na mesma linha sem separador válido.
- Validação futura: Confirmar versão usada e compilar a cópia no interpretador do produto.

### Biblioteca integração HTTP: estrutura inválida


- Evidência: Indentação inesperada e return fora de função; há referência a assuntoGuia sem definição local.
- Validação futura: Definir a função pretendida e verificar contrato HTTP sem executar a amostra exportada.

### Biblioteca integração de faturamento: estrutura e contratos


- Evidência: Indentação interrompe try; retorno de login muda de tupla para string; anexo incluído sem chave exigida; montagem de erro contém fechamento JSON extra.
- Validação futura: Testar payload inválido, login com falha e primeiro faturamento numa cópia isolada; verificar rollback e arquivos.

### Lookup lista de períodos: placeholders literais


- Evidência: URL usa {dgcoContrato} e item usa {ano}/{periodo}/{meses} sem interpolação; há mistura de indentação.
- Validação futura: Verificar valores enviados e apresentados; validar indentação no IronPython.

### Lookup lista de categorias: conteúdo de lista


- Evidência: Conteúdo é uma lista semicolonada sem aspas, em campo LookupScript.
- Validação futura: Conferir se deveria estar configurado como lista de opções antes de concluir impacto no produto.

### Confirmação de cadastro: Cancela sem atribuição


- Evidência: Referência isolada a Cancela não altera seu valor; pode não impedir confirmação.
- Validação futura: Testar fornecedor sem endereço e conferir variável de cancelamento do evento.

### Numeração por MAX + 1


- Evidência: Consulta seguida de gravação pode gerar o mesmo número em execuções concorrentes.
- Validação futura: Abrir duas solicitações simultâneas em teste e verificar unicidade/transação.

### Seleção hierárquica: contador não incrementado


- Evidência: countLoop permanece zero no laço; o limite de seis não limita a travessia.
- Validação futura: Testar hierarquia sem aprovador, pai ausente e ciclo em dados de teste.

### Seleção hierárquica: outra variante


- Evidência: Contador sem incremento e condição com or que pode contornar o limite.
- Validação futura: Conferir precedência e proteção da hierarquia.

### Seleção de gerente: contador sem incremento


- Evidência: O limite aparente do laço não progride; acesso aos pais ocorre antes de verificar existência.
- Validação futura: Testar hierarquia curta e sem perfil esperado.

### Seleção de gerente do favorecido


- Evidência: Variante também mantém countLoop em zero.
- Validação futura: Testar favorecido que é seu próprio gestor e ausência de pai.

### Seleção por consulta vazia


- Evidência: Rows.Count != 0 or Rows.Count != None é verdadeiro para contagem zero; id_gestor só recebe valor dentro do for.
- Validação futura: Consulta sem linhas pode acessar id_gestor não definido; testar zero, uma e várias linhas.

### Consulta de aprovadores repetida


- Evidência: Executa a mesma consulta até cinco vezes e adiciona os mesmos atores sem interrupção por sucesso.
- Validação futura: Verificar deduplicação da coleção e necessidade de repetição.

### Condições de cargo e órgão


- Evidência: Mistura and/or permite órgãos seguintes independentemente do cargo.
- Validação futura: Testar cada órgão com cargo previsto e diferente; confirmar agrupamento desejado.

### Condições e ramo duplicado


- Evidência: Mesma precedência ambígua e condição de órgão repetida que torna um ramo posterior inacessível.
- Validação futura: Revisar matriz de aprovadores da versão correspondente.

### UF verificada em texto


- Evidência: Membership em string faz comparação por trecho; string vazia também pertence à string.
- Validação futura: Testar UF vazia, abreviada, nome completo e inexistente.

### Vale-transporte: janela e ramos


- Evidência: Datas fixas em 2025; chamado fica em zero e ramos chamado > 0 não são alcançados; contagem acessada antes da verificação de nulo.
- Validação futura: Confirmar campanha da versão; testar ausência de grade e caminhos de recadastro.

### Uniforme: pedido no mesmo dia


- Evidência: Regra exclui diferença zero de dias, podendo liberar outro pedido no mesmo dia.
- Validação futura: Distinguir a própria OS de outra OS e testar intervalo de zero e 180 dias.

### Obrigatoriedade indicada como aviso


- Evidência: Trecho usa AdicionaAviso apesar de descrever anexo obrigatório.
- Validação futura: Confirmar se o evento deve bloquear e testar confirmação sem anexo.