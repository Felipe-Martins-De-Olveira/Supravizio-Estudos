# Estudo do manual do Supravizio

Revisão em 07/10/2026 para apoiar Felipe na construção e revisão de fluxos. Fonte principal: [manual oficial](https://help.supravizio.com/Supravizio.htm?tutorial06_desenho_do_fluxo.htm). Fonte textual de apoio: cópia local do repositório Documenta-ao-SUPRA fornecido pelo usuário. Complementos: aulas e XML PBEE já analisados.

## Cobertura e limites verificáveis

- O site foi aberto no navegador e o tutorial 6 foi lido, incluindo a revisão visual de uma figura do fluxo. O livro Guia para Solucionadores foi expandido no índice oficial.
- Foi feita revisão geral das áreas dos nove livros e leitura de tópicos centrais, com maior profundidade no Editor de Processos. Não foi feita leitura detalhada integral de cada página do manual, nem conferência visual de todas as imagens.
- O catálogo local contém **3.228 tópicos**, além de `_INDICE.md` (3.229 arquivos Markdown). Ele foi construído por leitura programática dos arquivos, caminhos, títulos e seções. Isso é indexação, não comprovação de aprendizado de cada método ou campo.
- **2.681 tópicos** pertencem a Customização, incluindo tabelas, objetos, propriedades, métodos e enumerações. Essas referências devem ser consultadas pelo nome exato quando forem necessárias; não são 2.681 tutoriais completos de desenho.
- Os textos locais não foram todos comparados com o site atual. Podem perder imagens, estrutura de tabelas e indentação. Alguns capítulos têm instruções antigas ou inconsistentes.
- Não foi acessada nem testada a instalação da empresa, e nenhum exemplo de comando do manual foi executado nela. Os exemplos são conteúdo de estudo, não autorização para executar operações.

## Os nove livros do índice

| Livro no site | Entendimento consolidado | Cobertura nesta revisão |
|---|---|---|
| Apresentação | Supravizio integra modelagem, execução por OS, indicadores e melhoria/versionamento, no ciclo PDCA. | Visão geral e relações entre módulos. |
| Interface com o Usuário | Portal atende solicitantes e aprovadores; Web e Windows disponibilizam ambientes com funções diferentes. | Visão geral, Worklist e Workspace; não pressupor que todo recurso exista em todas as interfaces. |
| Guia para Solucionadores | Atendimento de OS, campos, pendências, encaminhamentos, aprovações, comunicados e consulta. | Worklist, Workspace, atualização de aprovadores e relação com Dashboard/Base de Conhecimento. |
| Guia para Administradores | Cadastros, processos, Editor, papéis, formulários, prazos, Portal, relatórios e dashboards. | Principal área de aprofundamento: modelagem e configuração de fluxos, visão geral dos 15 tutoriais e demais editores. |
| Relatórios | Consultas com filtros/períodos, indicadores operacionais, pendências e histórico. | Pendências de aprovação, resumo de aprovações, melhorias, tabelas dinâmicas e ANO; outros relatórios catalogados. |
| Janelas | Referência de telas, campos, inclusão/edição/remoção e vínculos. | Organização de Ativos/Processo/Recurso/Utilitários e exemplos de Tipo de Subprocesso e Modelo de Comunicado. |
| Recursos Avançados | IronPython/.NET, DB, diretórios, WebServices, PowerShell, utilitários e jobs. | Conceitos, interfaces principais e pontos de execução; não auditados todos os métodos. |
| Customização | Modelo relacional e modelo de objetos do mecanismo de scripts. | Organização, herança OrdemServico/Ocorrencia e vínculos entre tabelas; referências individuais catalogadas. |
| Suporte Técnico | Canal de suporte do fornecedor. | Página de suporte consultada; horários e canais precisam ser reconfirmados antes de uso operacional. |

**Correspondência do índice:** o Guia para Solucionadores no site reúne Worklist, Workspace, Dashboard e Base de Conhecimento. A cópia local também os lista sob Interface com o Usuário. Não tratar essa repetição como dois conjuntos independentes de aulas. O caminho “Papéis” aparece isoladamente em uma página da cópia local.

## Como construir um fluxo no Editor

1. Identificar Macroprocesso, Processo, versão em edição e Subprocesso. O Subprocesso é o fluxo desenhado; Tipo de Subprocesso reúne características que persistem entre versões.
2. Definir os serviços que podem ser utilizados, as formas de início e as autorizações de abertura.
3. Inserir eventos e tarefas pela Toolbox: clicar no elemento e depois no local do desenho. Data Objects exigem clique no elemento ao qual serão associados.
4. Para conectar elementos, selecionar Fluxo, partir de um conector e arrastar até o conector do destino. Portanto, inserção de objeto e criação de ligação usam gestos diferentes.
5. Configurar responsável de cada atividade por Papel; conferir quem a regra recupera em uma OS real, em vez de preencher apenas um nome visual.
6. Associar os Data Objects com campos, anexos e aprovações nas etapas corretas.
7. Configurar alternativas dos desvios, scripts, mensagens e ANS/ANO que tenham sido pedidos no requisito.
8. Salvar e Validar Versão. A ativação também executa validação e não aceita configuração inválida. A validação estrutural não substitui testes dos cenários de negócio.
9. Em ambiente apropriado de teste, verificar abertura, avanço, aprovação/reprovação, devolução, cancelamento e encerramento, além de permissões e comunicados.

## Regras importantes para os próximos desenhos

### Tarefas e responsabilidades

- Uma tarefa pode ser manual ou automatizada. Responsável é um Papel recuperado no contexto da OS.
- A responsabilidade por si só não garante restrição de execução: existe a propriedade **Permissão restrita Papel responsável**. Quando desativada, o manual descreve registro de não conformidade se outra pessoa executa.
- **Permite voltar** controla a possibilidade de retorno no assistente. Um caminho de devolução desenhado e a ação de voltar não devem ser confundidos.
- Raias com apenas Texto organizam visualmente. Com Papel também podem determinar responsabilidades, com exceções documentadas para Sistema e filas.
- Papéis podem usar pessoas/filas, grupos, áreas, pessoa relacionada na OS, item associado, composição, script ou execução anterior. Seleção final pode envolver carga, fila ou todas as pessoas. Prioridades menores numericamente têm precedência no exemplo documentado.
- Serviço ou Item de Configuração pode redefinir um Papel. Para revisão, conferir também esses cadastros e a justificativa em Pessoas Envolvidas.
- Cliente, favorecido, responsável e pessoa que efetivamente abriu a solicitação não devem ser equiparados sem conferência. Um campo ligado a Pessoas pode servir de origem para um papel com seleção por hierarquia.

### Formulários e documentos

- Entrada de Dados define regras para campos nativos/customizados na atividade, iniciador ou finalizador. Campos configurados aparecem no assistente e na abertura, conforme a interface.
- Obrigatório bloqueia por pendência; Opcional recomendado produz aviso, não pendência impeditiva.
- Nome técnico do campo é diferente do rótulo/Descrição resumida. Tipo, controle visual e regra de preenchimento também são configurações diferentes.
- Coluna organiza o layout; Listagem de Registros/Grid permite colunas e múltiplas linhas, com modos de edição no formulário, na própria linha ou popup.
- Data Object de Item de Configuração pode associar um registro existente ou produzir um novo. Arquivos são Artefatos configurados como arquivos, com tipo e regras próprias.
- **Requerido inicialização** e **Produzido ao término** indicam entrada/saída. Não basta desenhar um ícone de documento para tornar o anexo obrigatório.
- Data Object Genérico pode documentar ou criar botão/hyperlink na Web; não equivale à regra de geração/associação de um arquivo.

### Aprovações

- Aprovação é um Data Object associado a uma **Tarefa**, com Papéis de aprovadores e dados sujeitos a aprovação.
- Campos para Aprovação determinam o que será analisado. Campos para Preenchimento coletam informações do aprovador e podem ser obrigatórios ao aprovar, reprovar, em ambas as ações ou sem obrigatoriedade.
- O comportamento padrão requer todas as aprovações e reprova com uma rejeição. Mínimo aprovadores e Reprovar imediatamente alteram o comportamento; conferir a configuração exata.
- Campos aprovados normalmente ficam bloqueados. O manual documenta cancelamento/nova versão da aprovação ou **Permitir modificação após aprovação**. Considerar o impacto sobre a evidência aprovada.
- Solicitação de aprovação é normalmente iniciada ao entrar na tarefa. **Iniciar automaticamente** pode alterar isso.
- Pré-aprovação pode reutilizar aprovação anterior ou identidade do solicitante, com condições e limites. Não habilitar automaticamente por conveniência.
- É possível mudar o rótulo dos botões, mas isso não cria, por si só, um terceiro estado de aprovação. Devolver e rejeitar definitivamente precisam de uma distinção de dados/rotas coerente.
- Relatório pode ser publicado na aprovação, tanto para Workspace quanto Portal, com parâmetros preenchidos a partir da OS.

### Desvios, subprocessos e eventos

- Desvio por Evento faz uma pergunta ao solucionador. Texto, motivo obrigatório e publicação da resposta são configuráveis por alternativa.
- Desvio Exclusivo seleciona uma alternativa pelo resultado da fórmula IronPython; o Valor comparação deve ter representação compatível com o resultado. Após aprovação, pode usar **Regra de Desvio** apontando a tarefa correspondente.
- Paralelo gera solicitações filhas nas saídas, sem condição. Inclusivo gera as alternativas cujas expressões forem verdadeiras. A documentação apresenta elementos de junção para reunir os fluxos.
- Chamada de Subprocesso pode passar parâmetros de entrada e receber parâmetros de saída. Chamada assíncrona e regras de sincronismo determinam o que a OS principal aguarda. Não representar como simples tarefa sem configurar esses efeitos.
- Iniciador manual tem visibilidade por aplicação e regras de Clientes Autorizados. Um iniciador somente Workspace pode preencher Cliente com usuário conectado, conforme configuração.
- Timer define ciclos; **Responsável é requerido para geração**. Fluxo com apenas timer não fica disponível para abertura manual no Portal/Workspace.
- Ciclo do timer é diferente do ciclo do job **Máquina de Processos**. O job verifica eventos; a regra do iniciador pode retornar lógico, DataTable, array ou lista, gerando OS conforme o retorno.
- Iniciador por Mensagem admite email e WebService; email pode determinar cliente pelo remetente cadastrado. A documentação informa remoção dos emails processados: não executar esse exemplo numa caixa real durante estudo.
- Um evento intermediário por regra pode aguardar condição no fluxo ou estar associado a uma atividade. Timer intermediário usa prazo a partir da entrada na atividade.
- Finalizador com sucesso e por cancelamento têm efeitos diferentes; cancelamento exige motivo. Link Final pode gerar/associar outra OS.

### Comunicados, prazos e scripts

- Evento intermediário de Mensagem usa Modelo de Comunicado, destinatários por Papel e/ou listagem fixa, assunto e regras de anexos. Descrição do evento participa do assunto da mensagem.
- O manual orienta editar Modelos de Comunicados pela Web. O modelo suporta campos dinâmicos.
- ANS representa compromisso de atendimento, levando em conta regras aplicáveis, serviços, calendários, horários e interrupções. ANO controla tarefa/agrupamento e pode usar minutos, percentual de ANS ou esforço apontado.
- Reexecuções de tarefa podem acumular tempo de ANO. Uma suspensão do ANS também paralisa ANO quando calculado em função do ANS, conforme o manual.
- Script Início prepara/automatiza; Validação pode impedir avanço por pendências; Fim complementa o encerramento; Volta trata retorno. Conferir a opção de executar validação na finalização do processo.
- Formulário Carregado, Modificado e eventos de Grid têm contextos próprios. Não trocar Formulario, OrdemServico e FormularioRegistro sem verificar onde o código será executado.
- Bibliotecas evitam repetir funções. A importação de XML preserva scripts, que podem continuar dependentes de IDs, campos e cadastros do ambiente de origem.
- DB.ExecuteDataTable, ExecuteScalar e ExecuteNonQuery têm finalidades diferentes. Assinaturas, SGBD e objetos .NET precisam ser conferidos na referência antes de escrever um script.

## Aparência para futuros desenhos

Aulas e figura do tutorial mostram início verde (timer com relógio), tarefas brancas com borda escura arredondada e ligações com setas. As amostras das aulas também mostram desvios amarelos, finalizadores rosados, Entrada de Dados laranja e Aprovação verde. Os Data Objects aparecem ligados às atividades e podem exibir os campos dentro do desenho. Essas observações são de telas específicas, não garantia de aparência idêntica em toda versão.

Nos próximos pedidos de desenho, representar o diagrama e entregar a configuração correspondente: elemento, Papel, campos, anexos, aprovação, fórmula/alternativas, mensagens e finalização. Seguir as referências visuais do Editor e identificar hipóteses que dependam da instalação da empresa.

## Consulta futura

- `CATALOGO-MANUAL.md`: navegação por livros e links para os textos locais.
- `CATALOGO-MANUAL.json`: título, caminho, URL, seções, tamanho e hash das cópias.
- `../../Supravizio-Estudos/estudo-materiais/CADERNO-TREINAMENTO.md`: aulas e tempos.
- `../../Supravizio-Estudos/estudo-materiais/ANALISE-PBEE.md`: exemplo XML estático.
- `../estudo-aulas/REVISAO-DAS-AULAS.md`: revisão visual amostrada.

O aprofundamento ainda pendente inclui leitura detalhada de todos os campos/métodos, todos os passos dos tutoriais de integração e todas as imagens. Nenhuma dessas partes deve ser declarada concluída pela existência do catálogo.
