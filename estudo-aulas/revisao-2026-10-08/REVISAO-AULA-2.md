# Aula 2 — revisão até o encerramento

Data: 08/10/2026. Fonte: Aula 2.mp4 em Downloads e transcrição local Aula 2.txt. Vídeo catalogado: 03:51:47,39; última fala transcrita: 03:51:22. Leitura sequencial de todos os trechos da transcrição, com saídas de autenticação omitidas. Conferência visual de 20 quadros selecionados do vídeo. Não representa reprodução contínua de todos os quadros, validação no sistema da empresa ou auditoria de código. Originais preservados.

## 00:00–00:40 — criar e disponibilizar o primeiro processo
- Estrutura: macroprocesso Tecnologia da Informação > processo Administrativo > subprocesso Adquirir suprimentos. Não confundir a hierarquia de cadastros com atividades do desenho.
- Toolbox: clicar no elemento e depois no local do desenho; a inclusão do elemento não é arrastar da paleta. Conectar pelo item Fluxo e pontos dos elementos, respeitando a direção início > tarefa > fim. O exercício corrige ligação invertida entre tarefa e final.
- Fixar a Toolbox evita recolhimento. Zoom auxilia a seleção dos pontos de conexão. Quadro 00:06:20 mostra a paleta e propriedades do início; 00:18:30 mostra o fluxo básico completo.
- Papel do exercício: Comprador de nível, tipo Relação de Pessoas e filas, coleção com usuário do participante. Quadro 00:09:40 confirma tipo e critério Todas as pessoas recuperadas pela regra. Não adotar menor carga como configuração realmente usada só porque aparece no tutorial.
- Papel existente com nome similar tinha tipo Relação de Grupos de Trabalho; o instrutor escolheu outro papel para o exercício. Conferir tipo, coleção, seleção final e associação à tarefa, não apenas nome.
- Responsável da tarefa recebe um papel. Criar papel sem salvar ou sem preencher pessoa/fila causa configuração incompleta. Atualizar a listagem de Responsável é distinto de salvar o cadastro.
- Validar subprocesso e validar versão são operações com alcance diferente. Aprovação da validação estrutural não comprova requisitos de negócio ou execução correta.
- Para abrir OS via Workspace: versão ativada, pessoa/solucionador adequado, grupo envolvido no macroprocesso e opções do menu atualizadas. Validar não é ativar.
- O problema demonstrado com o usuário interno Administrador é diferente de uma pessoa configurada com perfil Administrador. A conta técnica não tinha lotação adequada para criar OS; não concluir que o perfil Administrador impede toda abertura de OS.

## 00:40–01:20 — execução, versões e formulário inicial
- Abertura por Workspace e Portal executa o mesmo processo, com etapas/interface diferentes. No cliente, dados iniciais precedem os campos do formulário, que aparecem após salvar no exemplo. No Portal, campos do início compõem a abertura.
- Novas OS exigiram atualização da listagem no exemplo, sem atualização automática observada.
- Alterar campos obrigatórios na versão já usada por OS pode bloquear avanço por dados não preenchidos em etapas anteriores. A demonstração mostra impacto real no treinamento e inconsistência visual do desenho após alterações.
- Criar nova versão, abrir seu subprocesso com duplo clique e conferir número na aba ANTES de editar. Criar versão não muda automaticamente a aba aberta. Quadros 00:54:05 e 00:55:20 mostram versões distintas no Editor e OS ainda na versão 1.
- Histórico de versões permite consultar versões anteriores. Ativar nova versão não deve ser confundido com migrar todas as OS existentes.
- Reclassificação foi apresentada como alternativa para uma OS existente, mas a própria demonstração não retornou ao início como o instrutor inicialmente esperava. Não garantir retorno automático ao iniciador, migração sem impacto ou preservação universal de dados.
- O instrutor admite correção de script na versão usada pela OS. Isso é orientação do treinamento, não licença para considerar mudanças de script sempre sem risco. Conferir evento, dados e efeitos antes de alterar versão ativa.
- Campo nativo Assunto precisa integrar a Entrada de Dados do início para edição no Portal desse exemplo. A ordem da coleção determina a ordem mostrada. Quadro 01:17:00 mostra Descrição detalhada antes de Assunto, antes da reorganização.
- Ativar em um ambiente já disponibiliza aquela versão aos usuários autorizados. Exercícios são no ambiente de treinamento; a aula recomenda separar desenvolvimento, homologação e produção, com transferência por XML.

## 01:20–02:00 — serviços e exercício
- Cadastrar tipo de serviço, cadastrar serviço ligado ao tipo e associar serviços disponíveis ao tipo de subprocesso são operações distintas.
- Quadro 01:21:20 confirma descrição, descrição cliente, nome abreviado, solucionador responsável, responsável da área de negócio, tipo de serviço e Permite abertura via Portal de Processos.
- A escolha de qualquer solucionador é simplificação DO EXERCÍCIO. Solucionador responsável do serviço não é automaticamente aprovador. A informação pode ser utilizada por regras de papel.
- O instrutor primeiro descreve serviço como simples requisito de cadastro, mas depois explica impactos em papéis e SLA. Não considerar o campo irrelevante em processos reais.
- Sem restrição de serviços, o exemplo lista o catálogo disponível. Associar serviço limita a escolha. Prazo por serviço/perfil de cliente foi apenas introduzido; os valores citados são exemplos e não regras para novos fluxos.
- Há intervalo entre aproximadamente 01:33:57 e 01:54:43 sem novas falas transcritas; não contar como conteúdo técnico.
- Exercício: Meus Processos > Lista de Atividades > Atividade 01, com tarefas Dados da solicitação, Tempo de disponibilidade e Anexar arquivos. Responsável nas duas primeiras, Cliente na última; tipo de serviço Atividades e serviço Atividade 01. São nomes de tarefas, não instrução para criar campos nem substituir a tarefa de disponibilidade por timer.

## 02:00–02:40 — restrições e correção do exercício
- Serviços disponíveis são configurados em Modificar subprocesso > Tipo de subprocesso, não nas propriedades de evento ou tarefa. Quadro 02:05:30 confirma o diálogo de restrição com tipo e serviço.
- Um único serviço pode fazer o Portal pular sua seleção; com dois serviços, o passo reaparece. Logo, número do passo do formulário depende da configuração.
- O instrutor usa Flush.aspx para atualizar cache do ambiente de treinamento. Nome da rota na transcrição tem erros. Não executar limpeza num ambiente real sem conferir implementação, escopo e necessidade.
- Ações ANO não é a propriedade Responsável da tarefa. A configuração foi removida e o exercício continuou funcionando. Não adicioná-la como remédio geral para erro de papel.
- A comparação percentual da fala é imprecisa: 10% de uma hora são 6 minutos, não 10. Nenhuma fórmula de SLA foi implementada nessa discussão.
- Layout vertical não foi considerado inválido; esquerda > direita é preferência de organização citada pelo instrutor.
- Quadro 02:37:15 mostra objeto de documento usado pelo aluno, que o instrutor remove do exercício. Anexo estruturado foi associado verbalmente à folhinha azul Item de Configuração; não confundir com o objeto Documento.
- Papel Cliente/Responsável deve ser inspecionado antes de inferir identidade. O uso desses nomes no exercício não prova que ambos representam sempre a pessoa que abriu a OS.

## 02:40–03:20 — persistência, exportação e importação
- Nomes abreviados/siglas duplicados provocam erros de gravação. O instrutor corrige sua sugestão de underscore e recomenda identificadores sem espaços, acentuação ou caracteres especiais neste exercício. Não extrapolar para todos os nomes técnicos de campos: MENSAGEM_RETORNO, por exemplo, aparece com underscore em outras telas.
- O exercício teve dificuldade de persistência e recriação de cadastros. Hipóteses de cache/constraint não foram diagnóstico definitivo. Conferir mensagem completa, registro afetado e gravação; reiniciar pode descartar alterações não salvas.
- Salvar em etapas permite detectar cedo erros de gravação. Exclusões e reconstrução observadas são procedimentos do ambiente de treinamento, não recomendação automática para produção.
- Exportar é acionado no subprocesso e produz XML; importar é feito no destino em edição após salvar alterações. A aula usa outro aluno como fonte para recuperar o exercício.
- O exemplo de importação permite selecionar subprocessos e atualizar configuração de papéis. Quadro 03:20:20 confirma checkbox Atualizar configuração de papéis MARCADO. Isso é uma decisão de importação com possível efeito sobre papéis no destino.

## 03:20–encerramento — dependências e aprovação
- Serviço apareceu associado após a importação do exemplo, mas ainda faltou grupo envolvido no macroprocesso. Não inferir que XML garante automaticamente todas as dependências/cadastros/autorização de qualquer ambiente.
- Mudança de grupo do aluno foi feita pelo instrutor para o exercício, NÃO causada pela importação. Corrigir esse ponto antes de diagnosticar XML como causa de lotação alterada.
- Versão 4: inserir tarefa Realizar aprovação, código de tarefa, Data Object Aprovação verde e gateway exclusivo. Diferenciar responsável da tarefa, papel aprovador e regra do gateway.
- Complementar a partir de copia configuração de dados de uma Entrada de Dados para aprovação no exemplo. Quadro 03:42:35 confirma o menu; quadro 03:48:35 confirma Assunto e Descrição detalhada entre os dados da aprovação.
- Gateway: Tipo de desvio Dados ou fórmula > Regra de desvio Aprovação em Realizar aprovação; alternativas Aprovado e Reprovado. Quadro 03:43:50 confirma a escolha nativa disponível. Nesta aula não foi escrito script de comparação; não inventar um script como se estivesse demonstrado.
- Coleção Aprovadores pertence à configuração da aprovação: o quadro 03:44:40 mostra a folhinha verde selecionada com Aprovadores, Iniciar automaticamente True, Obrigatório True e Obrigatoriedade motivo Reprovação. A fala simplifica como propriedade da atividade; consultar o objeto correto.
- Papel Cliente usa Pessoa relacionada na ocorrência, recuperando cliente da OS. Esse aprovador é exemplo do treinamento, não substitui Fila de exemplo/código de unidade de exemplo no fluxo solicitado pelo usuário.
- Aprovação pendente impede avanço no exemplo. Quadro 03:46:50 confirma pendência; 03:47:15 confirma Finalizada com sucesso após aprovação e cadeados em Assunto/Descrição detalhada.
- Cancelar versão de aprovação não equivale a reprovar. Quadro 03:48:35 mostra versão 1 cancelada, versão 2 pendente e diálogo Reprovar exigindo motivo. Nova versão DA APROVAÇÃO não é nova versão DO PROCESSO.
- O caminho Reprovado termina em Cancelamento da OS porque o desenho foi configurado assim. Reprovação não precisa cancelar toda OS em qualquer fluxo; pode orientar outro caminho de negócio.
- Utilizar identidade do solicitante é pré-aprovação distinta de Iniciar automaticamente a solicitação. Segundo a fala e documentação, aproveita identidade de quem abriu a OS; não basta ser qualquer usuário que avançou a tarefa.
- Complemento documental: padrão exige todos os aprovadores, salvo mínimo/configuração; campos aprovados ficam bloqueados salvo configuração específica; pré-aprovação por identidade não se aplica a aprovações incrementais por hierarquia. A aula com um aprovador não valida comportamento de várias pessoas/filas.

## Fontes e limites finais
Lidos como apoio data_obj_aprovacao.md e por_formula.md em referencia-documentacao-supra/docs. Trechos antigos sobre assinatura Java não foram tratados como requisito atualizado. Capturas do treinamento mantidas localmente. Não houve execução no software corporativo, importação real ou edição de XML do usuário. A Aula 2 terminou antes de detalhar mais profundamente as aprovações, retomadas na Aula 3.

## Aplicação nos próximos fluxos
1. Conferir hierarquia, grupo autorizado, serviços e versão ativa.
2. Representar campos no Data Object Entrada de Dados e dados aprovados no Data Object Aprovação.
3. Configurar aprovadores por papel, código da tarefa e desvio nativo da aprovação, quando apropriado.
4. Separar pendência, cancelamento da aprovação, reprovação e encerramento da OS.
5. Testar os caminhos com usuários e papéis adequados no ambiente disponível; a gravação não substitui esse teste.
