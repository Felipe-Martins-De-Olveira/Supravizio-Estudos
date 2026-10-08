# Revisão da Aula 6 — Supravizio

Revisão em 08/10/2026. Fonte: gravação Aula 6.mp4, treinamento de 22/12/2020, versão 11.1.2. As interfaces históricas não comprovam o comportamento da instalação atual.

## Cobertura

Duração do arquivo: 03:59:48,54. Última fala transcrita: 03:58:00. Leitura de toda a transcrição em nove blocos sequenciais (linhas 1–32, 33–65, 66–100, 101–135, 136–170, 171–205, 206–240, 241–275 e 276–fim). Conferência visual de 29 quadros distribuídos pelos exemplos e encerramento, com ampliação individual dos scripts e propriedades críticos. Não houve reprodução contínua de cada segundo, nem execução dos scripts no software da empresa. As instruções do treinamento foram interpretadas como conteúdo documental; não foram executadas em sistemas reais.

Fontes adicionais consultadas na cópia local: GUIA-SUPRAVIZIO.md, pesquisas_de_satisfacao.md, prop_classepesquisasatisfacao_percentualenvio.md, db_executedatatable.md, relatorios_em_comunicados.md e controle_combobox.md. Correção técnica sobre views conferida na documentação da Microsoft, vinculada abaixo.

## 00:00–00:02 — Pendências da Aula 5

A OS de um participante pede seleção do responsável ao voltar: o instrutor explica que o papel é recalculado. A avaliação deste caso é favorável. Outro participante informa que ainda não realizou o exercício; portanto, não houve resolução de todas as pendências anteriores. Não considerar todos os fluxos dos alunos corrigidos só porque o treinamento terminou.

## 00:02–00:11 — Evento intermediário de mensagem

No processo Adquirir suprimentos, uma nova versão substitui a notificação de abertura cadastrada no Tipo de Evento por um Evento Intermediário por Mensagem colocado após o início. Configurar descrição, modelo de comunicado e papel destinatário (Cliente no exemplo). Validar, ativar e iniciar uma OS nova.

Salvar no iniciador não equivale a executar o evento: a mensagem é produzida quando o fluxo passa por ele. A aba Comunicados contém também mensagens de encaminhamento já configuradas, o que confundiu a primeira inspeção. O instrutor remove o evento redundante para isolar a demonstração. Evitar duas configurações enviando a mesma notificação.

Sobre e-mail inválido, o instrutor afirma que falha de envio pode deixar indicação de erro e ainda permitir avançar. Ele discute erro de Script Evento como situação distinta, mas não conclui um teste deliberado com exceção. Não afirmar que qualquer falha de mensagem é sempre não bloqueante em todas as versões.

O Script Evento mostrado adiciona comentário:

```python
OrdemServico.AdicionaComentario("Deu certo!", False)
```

O segundo argumento controla publicação no Portal; False deixa o comentário fora do Portal. A gravação mostra o comentário após atravessar o evento. IronPython permite usar objetos .NET; a expressão falada não é tipado deve ser entendida como tipagem dinâmica, não ausência de tipos.

## 00:11–00:27 — Relatório como anexo e repetição

Um relatório Lista de pessoas usa consulta SQL com nome, e-mail e telefone. O procedimento testa a consulta em Execução de Comandos SQL, cria o relatório e o layout, configura os dados e organiza a seção de detalhe e os cabeçalhos. Títulos no detalhe repetiriam a cada registro; o exemplo separa os cabeçalhos.

No evento de mensagem, Relatórios que serão anexados recebe formato PDF e o relatório cadastrado. Parâmetros devem existir e ser usados na consulta do relatório; informar um valor na configuração não cria sozinho o filtro SQL. A aula gera a mensagem, acessa o anexo e abre o PDF. Isso evidencia geração e disponibilidade do arquivo no comunicado; não houve conferência independente de entrega na caixa de e-mail externa.

A documentação confirma parâmetros e informa DestinatarioMensagem para relatórios individualizados. O dashboard é apresentado como recurso de gestão visual, enquanto o relatório pode integrar comunicados do processo. Não houve treinamento completo de dashboards.

Voltar e avançar novamente reexecuta o elemento e produz comunicações repetidas. Quantidade máxima de execuções=1 é configurada e testada numa nova OS; a aba Comunicados confirma uma mensagem após as tentativas de retorno. Aplicar esse limite quando o requisito for um único envio; não usar indiscriminadamente em notificações que devem ocorrer a cada nova revisão ou aprovação.

## 00:27–01:00 — Arquivos e Item de Configuração azul

O objeto azul representa Item de Configuração. Para solicitar um arquivo, criar em Ativos > Tipos de Itens de Configuração um tipo como Folha de pagamento, com sigla própria, supertipo Artefato, situação Anexado e artefato do tipo Arquivo. Conferir forma de acesso, visibilidade no Portal e tamanho máximo (10 MB é o exemplo, não limite universal).

Associar o tipo ao objeto azul pelo atalho Configurar > Associação de arquivo. Na OS salva, o usuário pode fazer upload e incluir arquivos. A descrição da associação merece nome claro para facilitar manutenção.

Reutilizar um tipo é possível, mas altera-se um cadastro compartilhado: mudar tamanho, natureza ou nome pode afetar outros processos. A coleção de associação é apresentada para mais de um tipo. O atalho substitui a associação atual, não acrescenta novos tipos a cada seleção. Diferenciar múltiplos arquivos de um mesmo tipo e múltiplos tipos de arquivo.

A tentativa de múltiplos tipos na mesma coleção falha na base do instrutor. Um quadro mostra erro SQL por valor NULL na coluna INC_ASSINATURA da tabela mencionada no diálogo. O instrutor contorna usando objetos azuis separados. A causa da falha não foi diagnosticada conclusivamente; explicações sobre base suja/versão/assinatura são hipóteses. O erro de associação de outro aluno permanece sem solução durante a aula. Não prometer que estará resolvido em outra instalação.

Para enviar os uploads, Tipo de arquivos anexados no evento de mensagem recebe o tipo desejado. O exemplo reclassifica uma OS da versão 8 para 9 e inspeciona os anexos. Isso é demonstração de treinamento, não garantia de migração sem efeitos para toda OS existente. Confirmar etapa, dados e comportamento na nova versão.

## 01:00–01:31 — Pesquisa de satisfação

Associar a classe de pesquisa à propriedade Pesquisa de satisfação do finalizador. A pesquisa é gerada na finalização da OS correspondente; pai e filha podem possuir configurações diferentes. A gravação responde no Portal e observa o estado no Workspace e os relatórios. O Workspace mostra o resultado, mas a resposta foi feita no Portal.

A chamada de fornecedor inicialmente espera a filha. A fala chama incorretamente esse estado de assíncrono; o quadro de 01:03:20 mostra Chamada assíncrona=False. O instrutor muda para True para permitir continuar sem esperar a conclusão da filha. Preservar essa distinção já registrada nas aulas anteriores.

Cadastro da pesquisa:

1. Grupo de questões, com opções de escore.
2. Questões de pesquisa, cada uma associada ao grupo.
3. Classe de pesquisa, ativa, contendo as questões.
4. Associação da classe ao finalizador do subprocesso.

O exemplo Questões gerais usa sequência 0–4 e pesos Péssimo=-2, Ruim=-1, Regular=0, Bom=1, Ótimo=2. Sequência e valor são propriedades distintas. Mudanças experimentais para valores 9 e 10 não demonstram fórmula geral de cálculo; não adotar a hipótese de eixo cartesiano como implementação documentada.

Correção importante: a tela mostra Percentual envio=100. A documentação define probabilidade de envio entre 0 e 100; zero não envia e cem sempre envia, sujeito às demais configurações aplicáveis. Não representa quantidade de cem envios, nem valor obrigatório em qualquer pesquisa. A documentação também distingue Favorecido e Cliente: o favorecido é o avaliador e, por padrão, corresponde ao cliente.

As perguntas aparecem em ordem alfabética no exemplo; não houve exame completo dos critérios de ordenação. Ícones cinza/verde/amarelo/vermelho acompanham situação e respostas, mas não bastam para deduzir a fórmula de agregação. Relatórios nativos detalham as respostas. Não confundir uma amostra minúscula demonstrativa com desempenho real de atendimento.

Intervalo entre aproximadamente 01:31:55 e 01:49:32.

## 01:49–02:34 — Formulários customizados

Campos mostrados: Fornecedor (texto alfanumérico), Contrato (combobox com lista fixa), Área responsável (combobox por consulta), Lista de contratos (grid/lista de registros), Data de abertura (Data e hora com controle que exibe só data) e Observações (alfanumérico com controle Memo).

Distinguir descrição/rótulo, nome técnico, coluna de armazenamento, tipo de dado e controle visual. Nomes técnicos não devem receber acentos ou caracteres especiais do rótulo. A largura do controle não é o mesmo que comprimento máximo do texto. Não confundir o campo customizado chamado Data de abertura com o campo nativo da OS só por compartilhar uma descrição.

Combobox por script: preencher Itens com o DataTable retornado por DB.ExecuteDataTable. Para um campo inteiro, a primeira coluna traz o identificador armazenado e as seguintes fornecem o descritivo exibido. Na documentação, listagem fixa é separada por ponto e vírgula. Os quadros mostram a mudança de Alfanumérico para Inteiro no campo Área responsável.

DB.ExecuteDataTable possui assinatura com consulta e identificador de conexão opcional; sem conexão indicada, consulta a base do Supravizio. A aula simula cadastro de conexão externa, mas o teste falha porque a conexão é genérica. Não demonstrou integração real com SharePoint. Consulta SQL a uma base externa e acesso a uma lista SharePoint são mecanismos que precisam ser definidos para a fonte real.

Correção sobre banco externo: a fala afirma que uma view não admite alterações. Isso não é uma garantia geral: SQL Server permite modificar dados por views atualizáveis. A restrição de acesso deve ser estabelecida pelas permissões da conexão, e não presumida pelo uso de uma view. Fonte: [Microsoft — Modify Data Through a View](https://learn.microsoft.com/en-us/sql/relational-databases/views/modify-data-through-a-view?view=sql-server-ver17).

O grid recebe colunas Descrição e Dono; pode combinar diferentes controles. Permitir inclusão, edição e exclusão são configurações independentes. Copiar a Entrada de Dados para outra atividade preserva referência ao mesmo campo: mostra os dados da mesma OS, não cria uma tabela vazia independente. Para dados diferentes, usar campos distintos. A demonstração de avanço após cópia sofre com a conexão; não foi concluída nesse momento.

Rótulo para entrada de dados nomeia os agrupamentos. Coluna, ordenação, largura e altura ajustam o layout. Conferir tanto Portal quanto Workspace, pois o resultado visual pode variar. Memo serve para textos extensos. Cascata, visibilidade e habilitação via script são apontadas na documentação, mas não implementadas na aula.

## 02:34–03:29 — Exercício Lançamento de notas

Tipo de serviço Acadêmico, serviço Lançamento de notas, processo no menu Meus Processos > Lista de Atividades.

- Lançar notas: Professor; lista de alunos com Nome, Nota final, Status; Ano corrente (campo data no exercício).
- Realizar triagem: Auxiliar de gestão, visualizando os mesmos campos.
- Havendo ao menos um reprovado por nota: Comunicar reitoria, Auxiliar de gestão, com E-mail e Quantidade de reprovados; depois Aprovação de segunda instância, papel Reitor.
- Aprovado em segunda instância: Lançar certificado, Auxiliar de gestão, com Data realização e Professor auxiliar; depois fim.
- Reprovado em segunda instância: Comunicar pais; depois fim.

O enunciado exige ANS de três dias e ANO de três horas em Lançar notas. Esclarecer dias corridos versus horas contabilizadas antes de converter o ANS. O ANO constante de três horas corresponde a 180 minutos. Notificação de Início aprovação para aprovador e de Reprovação em segunda instância para professor. Pesquisa de satisfação fica opcional. A descrição detalhada é aceita como simplificação do grid no treinamento.

O caminho sem reprovados não está inteiramente explicitado na fala/enunciado amostrado; decidir com o responsável pelo requisito antes de implementar um fluxo real. Não acrescentar uma aprovação obrigatória à triagem por inferência: o exercício originalmente tem uma aprovação de segunda instância.

## 03:29–03:41 — Eventos, destinatários e status

Um aluno configura Aprovação em vez de Início aprovação. São momentos diferentes: o primeiro comunica a decisão já realizada; o segundo comunica uma nova solicitação pendente. Conferir evento, subprocesso abrangido, destinatário e modelo.

O papel fixo Reitor enviaria todas as mensagens para o mesmo papel mesmo quando houvesse dois grupos diferentes de aprovadores. Responsável atual não significa aprovador do objeto verde. Destinatário vazio não seleciona automaticamente o último responsável. Papéis por atividade, mensagens explícitas em pontos diferentes ou script podem resolver cenários específicos. O instrutor discute cancelamento por código, mas não entrega um script final testado: não converter essa fala em API inventada.

O status lógico exibiria um checkbox. Para escolha textual Aprovado/Reprovado, o aluno muda para alfanumérico, controle Combobox, Listagem de itens, com as duas opções. A triagem visual usa gateway Pergunta e resposta; uma decisão automática requer lógica que examine os registros.

## 03:41–03:54 — Script do grid e gateway automático

Exemplo efetivamente mostrado no Script Fim da tarefa Fila de atendimento:

```python
for linha in OrdemServico["PRODUTOS"].Rows:
    if linha["STATUS"] == "Reprovado":
        OrdemServico["REPROVADO"] = True
        break
```

PRODUTOS é o grid e REPROVADO um campo auxiliar lógico. O break encerra a busca ao encontrar um reprovado. A fórmula do gateway Dados ou fórmula é uma única expressão:

```python
OrdemServico["REPROVADO"]
```

Alternativas: Sim, comparação igual a True; Não, comparação igual a False. Conferir também a conexão de cada saída. Um exemplo com aprovado+reprovado segue o caminho Sim; outra OS, com todos aprovados, segue Não. Esses são testes vistos na gravação, não executados por esta revisão.

Os valores customizados pertencem à OS/instância. A consulta final reúne a tabela de registros, OCORRENCIA e CP_ORDEM_SERVICO por identificadores; nomes como Z012_PRODUTOS são da base do exemplo e não portáveis. Campo sem preenchimento no banco não deve ser confundido indiscriminadamente com False em toda API ou SQL; a documentação especifica default False para acesso lógico por GetCustom, podendo usar None para distinguir ausência de valor.

O exemplo depende do estado inicial do booleano em cada nova OS. Isso não corrige o caso em que a mesma OS volta e troca os status. Adaptação recomendada para recalcular a cada execução, ainda sem teste no ambiente empresarial:

```python
OrdemServico["REPROVADO"] = False
for linha in OrdemServico["PRODUTOS"].Rows:
    if linha["STATUS"] == "Reprovado":
        OrdemServico["REPROVADO"] = True
        break
```

Antes de aplicar: confirmar nomes técnicos, disponibilidade do DataTable, obrigatoriedade/valores do status e o evento de execução. Esse script decide se existe ao menos um reprovado; não conta quantos. Se o campo Quantidade de reprovados precisar ser calculado, percorrer todos os registros e contar, sem parar no primeiro.

## 03:54–encerramento — Implantação e limites

O instrutor encerra sem corrigir todos os exercícios. Sugere separar desenvolvimento, homologação e produção, validar requisitos e testar ponta a ponta antes de exportar/importar e ativar. A conversa final trata também dos certificados do treinamento; não é requisito dos fluxos da empresa.

Pendências para validação prática: tratamento de falha no envio e no Script Evento; conexão externa real; problemas de associação de artefatos; permissões efetivas dos destinatários; retorno na mesma OS e recalculação do booleano; contagem de reprovados; caminho sem reprovados; importação das dependências entre ambientes. Conteúdo transcrito revisado até o encerramento, com conferência visual amostrada.
