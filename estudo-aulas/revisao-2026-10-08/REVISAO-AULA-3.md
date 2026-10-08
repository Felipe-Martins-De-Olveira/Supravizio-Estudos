# Revisão da Aula 3 — 08/10/2026

## Cobertura

Vídeo original: [caminho local omitido] 3.mp4, duração 03:48:26,24. Transcrição original: Supravizio-Estudos/estudo-materiais/transcricoes/Aula 3.txt. Todo o conteúdo transcrito foi lido sequencialmente até a última fala, 03:47:53, excetuados trechos de autenticação. Foram examinados 16 quadros. Revisão visual amostrada, sem assistir continuamente cada imagem e sem validar execução no software da empresa. Originais preservados; imagens mantidas localmente.

## 00:00–00:15 — Importação

O exemplo importa Adquirir suprimentos em outro processo. Versão 3 da origem aparece em versão 1 no destino; a importação não transporta necessariamente todo o histórico. Números diferentes entre ambientes dos alunos e instrutor não impedem desenhos equivalentes.

Em 00:09:38–00:13:11, Comprador de nível foi importado como papel, mas ficou sem uma pessoa válida porque a pessoa da origem não existia no destino. Corrigiu-se atribuindo uma pessoa local, salvando e validando. Importar o papel não garante importar seus participantes.

## 00:15–00:42 — Aprovação nativa

Realizar aprovação é tarefa; Aprovação é Data Object verde associado à tarefa. Entrada de Dados é Data Object laranja associado ao elemento de preenchimento. Não transformar esses objetos em tarefas adicionais nem usar linha de sequência comum como ligação do formulário.

Um objeto de entrada órfão foi corrigido copiando-o e colando-o sobre o destinatário; uma tentativa anterior com a ferramenta Fluxo não passou na validação.

A tarefa recebe código identificador no contexto do processo. O gateway exclusivo usa Tipo de desvio = Dados ou fórmula e Regra de desvio = Aprovação em Realizar aprovação, confirmado na tela de 00:21:20. Código da tarefa e código do gateway são diferentes.

Campos para Aprovação podem vir da entrada ou de coleção explícita, por exemplo selecionando somente parte dos campos. Campos para Preenchimento e Campos para Aprovação têm funções diferentes. Escolher aprovadores não substitui escolher dados submetidos.

Responsável ficou vazio numa demonstração, mas isso não é regra universal para tarefas de aprovação. Cliente/solicitante cadastrado também não identifica necessariamente quem abriu a OS; consultar Dados da execução. Portal e Workspace apresentam aprovações em locais diferentes.

## 00:42–01:13 — Investigação

Aprovação aprovada não garante alternativa válida no gateway. A aula tenta retorno, reclassificação, nova aprovação, nova edição e salvamento. Cache, rede e edição em versão usada foram hipóteses, não causas comprovadas de todos os erros. Em um caso, a propriedade precisou ser reconfigurada e salva.

SQL e limpeza/flush foram mencionados, sem execução nesta revisão. Não adotar exclusão ou limpeza como procedimento rotineiro. Separar ambientes de desenvolvimento, homologação e produção; a fala sobre a ordem desses ambientes é inconsistente.

## 01:13–01:28 — Chamada entre subprocessos

Cadastrar fornecedor é criado com Evento Inicial por Mensagem verde, Cadastro de certidões, Cadastrar fornecedor e Evento Final. No chamador, aprovado segue por Atividade Chamada amarela.

Cadastrar associação com chamador, invocado, nome único, frases direta/inversa e cardinalidade. O exemplo usa 1:1 e separador ponto, formando uma identificação como 103.1. Frases são descrições da relação, não comandos que geram a filha.

Configurar a associação na chamada e sua leitura inversa no Evento Inicial por Mensagem do invocado. Salvar, validar os subprocessos da edição e ativar. Expansão da atividade navega no desenho; Associadas navega nas ocorrências.

Correção da transcrição: a propriedade é Chamada assíncrona. A tela de 01:27:00 mostra False; a documentação referencia-documentacao-supra/docs/subprocessos.md confirma que False exige concluir as ocorrências filhas antes de avançar a chamada. True permite avanço sem essa conclusão, sujeito às restrições de sincronismo configuradas. Não ensinar o nome como Chamada síncrona=False.

A documentação também apresenta sincronização de cancelamentos, parâmetros, passagem/retorno de itens e restrições de chamadas assíncronas. Nem todos foram configurados nesta aula.

Intervalo aproximado: 01:28:18–01:50:34.

## 01:50–02:32 — Associação e exercício

Uma associação apontando acidentalmente para o chamador foi corrigida. Frase inversa não é operação para desfazer cadastro.

Envelope inicial não significa obrigatoriamente e-mail. A tela de 01:20:50 mostra abertura por Subprocesso ou LinkFinal e Mensagem entre Processo.

Atividade 02 foi anunciada em 02:02:17. O quadro de 02:02:30 mostra reunião sem o enunciado; não foi possível recuperar integralmente os requisitos escritos desse quadro. Há lacuna de falas durante o exercício.

O desenho apresentado em 02:41:30 contém início → Analisar Demanda (Responsável) → Realizar Aprovação (Gestor) → gateway. Aprovado → Dados da Solicitação (Responsável) → Sucesso; Reprovado → Cancelamento. Entrada de Dados ligada à análise com Descrição detalhada e Justificativa; Aprovação ligada à tarefa com Gestor. Isso comprova o desenho mostrado, não todo o enunciado original.

## 02:32–02:55 — Alternativas do gateway

Texto da linha é legenda; valor de comparação da alternativa determina o caminho. Em 02:40–02:42 ambas as alternativas estavam configuradas como Reprovado. Corrigir uma para Aprovado permitiu avançar após aprovação. Este é um erro concreto, diferente das hipóteses de cache.

Justificativa pode integrar a coleção seletiva de aprovação. Exportar/importar o exercício numa nova edição corrigiu sua organização. Registros com OS associadas podem impedir remoção; não recomendar apagar dados de produção. DLL/permissão na exportação foram suspeitas não comprovadas; algumas operações terminaram após espera.

## 02:56–03:37 — Tipo versus desenho na versão

Um Tipo de Subprocesso existia no cadastro, mas seu desenho não estava no Process Explorer da edição. Ter tipo cadastrado não garante subprocesso vinculado à versão. Adicionar o existente, completar o desenho e revisar associação foi a correção mostrada.

Conflito de chave em ASSOCIACAO_SUBPROCESSO foi observado, sem demonstrar causa interna nesta revisão. Descrições iguais podem representar tipos distintos; sigla distingue os cadastros. Nome claro ajuda a selecionar o destino correto.

Outro gateway passou a avançar após recriar linhas e selecionar resultados. Isso demonstra a correção, não uma causa interna universal.

Sem separador, o exemplo gerou filha 104 associada à 103. A tela de 03:35:20 confirma a filha em Cadastrar Fornecedor 01. Finalizar filha e atualizar pai libera avanço no exemplo.

## 03:38–03:47:53 — Pré-aprovação e participantes

Reutilizar aprovações anteriores e Utilizar identidade do solicitante são recursos distintos. Reuso depende das condições da aprovação anterior e dos dados, conforme documentação; identidade aproveita quem abriu quando corresponde ao aprovador aplicável. Cliente cadastrado não significa aprovação automática de qualquer participante.

Em 03:41:50, a OS principal mostra pendência porque a filha não foi finalizada. É uma mensagem nativa demonstrada, não código de script apresentado.

Cliente e Gestor foram adicionados como aprovadores. Pré-aprovar um não dispensa a decisão do outro. Sem configuração que altere quantidade mínima, observar a regra conjunta nativa. Tela de 03:46:55 confirma Cliente e Gestor e Utilizar identidade do solicitante=True.

Hierarquia Inicial/Final foi discutida ao final, com demonstração completa adiada. Não foi validada execução hierárquica completa. Mínimo de aprovadores foi mencionado sem teste completo. Um script de preenchimento automático do cliente foi anunciado, mas não apresentado: não inventar seu código.

## Conferência para próximos fluxos

- Associação correta dos Data Objects aos elementos.
- Código da tarefa, regra nativa e valor de cada alternativa do gateway.
- Pessoas válidas nos papéis importados.
- Dois extremos da associação, desenho na versão, cardinalidade e chamada assíncrona.
- Separação entre abertura, cliente, responsável e aprovadores; quantidade e hierarquia definidas pelo requisito.
- Quando houver ambiente de testes: aprovação, reprovação, outro aprovador pendente e conclusão da filha.

## Quadros examinados

Segundos: 605, 1110, 1220, 1280, 1835, 2480, 4850, 5160, 5220, 7350, 9690, 12090, 12690, 12920, 13310, 13615. Quadros 5160 e 7350 mostram carregamento/reunião e não confirmam propriedades. Documentação cruzada: subprocessos.md e associacao_sub.md na cópia local oficial.
