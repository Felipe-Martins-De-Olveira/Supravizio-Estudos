# Revisão da Aula 1 — 08/10/2026

## Método e alcance
Revisão em blocos de 20 minutos da transcrição, acompanhada de quadros selecionados do vídeo original. Não equivale a assistir continuamente todo o vídeo. Originais preservados. Trechos de autenticação omitidos da saída de leitura; não considerados revisados integralmente. Nenhuma configuração ou script foi executado no ambiente da empresa.

Nesta rodada: conteúdo transcrito da Aula 1 revisado até o encerramento em 03:37:09. Conferência visual amostrada: 21 quadros examinados no acumulado. O arquivo tem duração catalogada de 04:00:00; análise de silêncio a partir de 03:37:10 identifica silêncio abaixo de -40 dB desde aproximadamente 03:37:14 até o fim. Quadros finais mostram participante e tela escura. Não equivale a assistir todos os quadros continuamente. As revisões das demais aulas estão nos relatórios individuais desta pasta.

## 00:00–00:20 — acesso, Workspace e ausências
- A distinção entre Portal, Workspace e Editor envolve funções e permissões. Ter acesso como solucionador não comprova permissão para modelar processos.
- Selecionar campos no grid muda a visualização; não é alteração de responsável ou encaminhamento. Quadro 00:08:05 confirma o menu.
- Filtros de responsável, aprovador, pessoa envolvida, situação e paginação podem explicar uma OS não aparecer. A opção Todos não comprova acesso irrestrito.
- Cancelamento é diferente de encerramento com sucesso. Quadro 00:15:55 mostra o assistente solicitando motivo de cancelamento.
- Ausências: período, substituto e três permissões independentes. Quadro 00:19:45 confirma modificar OS, redirecionar encaminhamentos e realizar aprovações em nome do titular. Não pressupor que escolher substituto habilita todas.
- O problema de acesso a arquivo descrito no início da aula não diagnostica o erro de referência nula observado no teste local com Wine.

## 00:20–00:40 — integrações e operação do ambiente
- Conexão nomeada com banco externo pode servir para consultas e alimentação de campos. Escrita depende de permissões e da configuração da conexão; a explicação não oferece uma implementação pronta nem demonstra um conector nativo do Power Automate.
- Rotinas de mensagens e máquina de processo fazem parte da operação. Registrar uma mensagem não prova que foi enviada. Quadro 00:28:40 mostra situação Pendente; a fala explica que a rotina de envio não foi configurada no treinamento.
- A fala informa que um recurso antigo de apuração de indicadores foi descontinuado naquele contexto. Isso não é evidência sobre a versão atual, nem sobre o fluxo empresarial solicitado pelo usuário.
- Perfis de acesso controlam autorizações a recursos e relatórios. Diferenciar configuração de acesso de grupo de trabalho e responsabilidade de tarefa.
- Cadastro de pessoa inclui área e cultura no exemplo, seguido de Configurar Solucionador. Detalhes de autenticação foram omitidos nesta leitura.

## 00:40–01:00 — cadastros, prazos e customização
- Quadro 00:40:30 confirma cadastro de Pessoa e comando Configurar Solucionador; não confirma sozinho todos os perfis disponíveis. Parte da fala nesse ponto foi omitida por autenticação.
- A seleção de Administrador é exercício do ambiente de treinamento; não é requisito universal para colaboradores de um fluxo.
- Pesquisa com % apresentou falhas no próprio exercício. A hipótese de cache é do instrutor, sem diagnóstico comprovado; não tratá-la como causa garantida.
- Prazos dependem do acordo, calendário, feriados e interrupções configurados. Aguardar cliente não pausa automaticamente SLA pela simples existência dessa espera.
- Perfis de cliente podem influenciar atendimento/ANS; não são sinônimo de perfil de acesso. Consulta de apoio: referencia-documentacao-supra/docs/dados_perfil_cliente.md.
- Dicionário de classe permite propriedades customizadas em cadastros. O exemplo mostra um checkbox Medição no contrato (quadro 00:52:35). Transcrição alterna medicação/medição e data de missão/admissão: conferir nome visual antes de usar em código.
- Cadastro de contrato e propriedades de classe são distintos dos campos de formulário de uma atividade.
- Apontamentos registram intervalo e descrição de trabalho. A aula começa um exemplo ao fim do bloco; conclusão ainda pendente.

## Evidências visuais locais
Quadros em aula-1/frame-275.jpg, frame-485.jpg, frame-955.jpg, frame-1185.jpg, frame-1720.jpg, frame-2430.jpg e frame-3155.jpg. Contêm telas e participantes do treinamento; mantidos localmente.

## 01:00–01:20 — perfis, relatórios e Worklist
- A explicação inicial de que o perfil mais amplo sobrescreve o menor é refinada pelo instrutor: autorizações de perfis customizados podem complementar as dos nativos. Não assumir que Administrador visualiza automaticamente qualquer relatório recém-criado.
- Relatórios: conferir autorização de perfil e disponibilização no menu. Quadro 01:11:20 confirma comando Disponibilizar menu no Editor de Relatórios; a demonstração subsequente alterna usuários para conferir visibilidade.
- Não generalizar visibilidade no menu como prova de isolamento de dados em todos os caminhos de acesso. A demonstração é sobre publicação e acesso pelo perfil.
- Portal, Worklist e Workspace têm funções distintas. Segundo a aula, Worklist também consome licença; a explicação de licenciamento é histórica e precisa ser confirmada no contrato/versão atual antes de orientar contratação.
- Modo Worklist é uma configuração do ambiente, distinta do perfil atribuído à pessoa. Quadro 01:17:10 mostra Ativados para todos.

## 01:20–01:40 — Portal e intervalo
- Aula explica que acesso pelo Portal continua consumindo recursos de servidor, mesmo no cenário descrito sem consumo de licença de solucionador. Não interpretar como capacidade ilimitada.
- Entre aproximadamente 01:21:16 e 01:39:14 há intervalo sem novas falas na transcrição. Não contabilizar esse tempo como conteúdo técnico nem afirmar conferência contínua do vídeo.

## 01:40–02:00 — autorização e encerramento de sessão
- Configuração geral do Worklist pode ser desativada, ativada para todos ou somente para pessoas autorizadas. Quadro 01:43:15 confirma Somente pessoas autorizadas; neste modo, a aula orienta conferir também a autorização individual.
- Endereço do Workspace não substitui endereço do Portal para uma pessoa configurada apenas para autoatendimento.
- Remoção de configuração de solucionador envolve conferir demandas atribuídas e autorização individual. Não executar esse procedimento nos usuários reais sem analisar responsabilidades e acesso.
- A afirmação inicial de perda de tudo ao encerrar sessão é corrigida na demonstração: alguns dados foram preservados nos testes. O próprio instrutor descreve comportamento intermitente e não garante recuperação. Portanto, não recomendar encerramento de sessão como salvamento automático.
- Pesquisa por número nativo difere da pesquisa textual em campos. Pesquisa textual altera o modo de navegação; sair do modo de filtro restaura a interação habitual. Quadro 01:54:05 estava em carregamento e não confirma o resultado da gravação: evidência desse resultado nesta rodada é textual.
- Número customizado/protocolo em um campo não é necessariamente o identificador nativo da OS; distinguir os dois ao escrever consultas e scripts.

## 02:00–02:20 — grupos de trabalho e consultas
- Órgão/área, grupo de trabalho, fila e papel são conceitos distintos. O nome semelhante não cria associação automática entre grupo e órgão. Confirmado em dados_grupo_trabalho.md.
- Para localizar a lotação de uma pessoa, a aula usa Pessoas > Configurar Solucionador, evitando abrir todos os grupos.
- A demonstração SQL retorna coordenadores, embora a pergunta original fosse sobre participantes. Não reutilizar essa consulta como lista de membros.
- Modelo documentado: GRUPO_TRABALHO.ID_COORDENADOR liga-se a PESSOA.ID_PESSOA; membros passam por TECNICO.ID_GRUPO_TRABALHO e TECNICO.ID_PESSOA. Conferir associação ativa, domínio e esquema da instalação antes de produzir relatório real. A consulta desta rodada foi documental, sem conexão a banco.
- TECNICO documenta somente uma lotação ativa por solucionador em dado momento. Histórico de associações não equivale a múltiplas lotações atuais.
- Regras de operação de um grupo (cancelar, encaminhar, classificar, reabrir, interromper ANS e priorizar) são descritas como não recursivas aos níveis inferiores. Não inferir herança de autorização pela simples hierarquia.
- Uma OS que parece ter perdido campos pode estar numa aba secundária, como SLA. Conferir aba e filtros antes de atribuir a falha ao formulário.

Fontes de apoio lidas nesta rodada: referencia-documentacao-supra/docs/dados_grupo_trabalho.md e dados_tecnico.md. Quadros adicionais: frame-4280.jpg, frame-4630.jpg, frame-6195.jpg e frame-6845.jpg. Próximo bloco: personalização da visão e operações de grupo, a partir de 02:20.

## 02:20–02:40 — filas e responsabilidades
- Criar Fila aparece em Grupo de Trabalho > Solucionadores e Filas. Quadro 02:24:35 confirma nome, e-mail opcional e opção Alertar Solucionadores do Grupo. Isso informa como criar Fila de exemplo no fluxo de peças 3D; vínculo com código de unidade de exemplo deve ser configurado conforme o cadastro real, não presumido pelo nome.
- Encaminhar para fila compartilhada e assumir responsabilidade são momentos distintos. Assumir retira a demanda da responsabilidade da fila e atribui ao usuário, conforme a demonstração narrada.
- Autorizações em filas de outros grupos permite acesso a filas sem uma segunda lotação ativa. Quadro 02:28:10 mostra a fila de suprimentos na árvore do grupo corporativo.
- Regras de operação do grupo são independentes do processo executado naquele contexto. Conferir também permissões específicas e versão, sem inferir que uma opção visual habilita operação.
- Instância de processo neste treinamento corresponde à execução/OS, não à instância de banco ou instalação.

## 02:40–03:00 — interface e acesso real
- Opções da tela de edição e opções da tela de Workspace são conjuntos diferentes, ambos alterados no cadastro do grupo e com efeito para seus membros.
- O instrutor corrige sua associação inicial de Exibe classificação: mostrar dados de classificação não equivale necessariamente a autorizar reclassificar. O funcionamento exato dessa opção ficou pendente na aula.
- A alteração de visualização de grupos apresentou erro quando um item que seria ocultado estava selecionado. O instrutor reproduziu e contornou selecionando item do próprio grupo. Trata-se de ocorrência dessa versão, não prova de defeito atual.
- Ocultar grupo/aba não bloqueia por si só acesso direto pelo número da OS. A aula demonstra ajuste de regra de visualização do subprocesso e desmarca Acesso total para usuários com perfil administrador.
- Quadro 02:59:50 confirma Acesso Restrito e texto que permite ao responsável E SEUS COORDENADORES visualizar conteúdo. Essa tela refina a fala simplificada de somente responsável: não prometer exclusão de coordenadores.
- Organização do Editor: macroprocesso > processo > subprocesso; a modelagem é no nível demonstrado do subprocesso.

## 03:00–03:20 — comunicação e campos
- Worklist é ilustrado como visão simplificada de execução, não só um Workspace com abas escondidas. Quadro 03:04:05 confirma listagem própria.
- Início por e-mail exige caixa, rotina de mensagens e evento configurados; é possibilidade explicada, sem implantação demonstrada nesta aula.
- Modelos de comunicado no contexto da aula são editados pela interface Web, com valores dinâmicos da OS e dos campos. Não copiar a sintaxe pronunciada como expressão executável sem conferir o editor/modelo.
- Notificação por evento de abertura/encaminhamento difere de mensagem prevista no desenho. Registro de comunicado não prova envio; conferir situação e rotina.
- Atualização de demandas na tela é manual no exemplo apresentado; não generalizar para toda versão atual.
- Quadro 03:16:30 confirma propriedades do campo MENSAGEM_RETORNO: descrição resumida Retorno para o solicitante, coluna MENSAGEM_RETORNO, tabela CP_ORDEM_SERVICO, controle Memo e Permitir inclusão em listagens inicialmente False. Nome técnico, rótulo e descrição resumida têm usos diferentes.
- O instrutor altera inclusão em listagens e depois procura a descrição resumida no seletor do grid. Não inferir que todo campo se torna coluna sem essa configuração.
- Quantidades máximas de colunas SQL Server/Oracle citadas de memória são incertas e não adotadas como referência técnica.

## 03:20–encerramento — armazenamento, Toolbox e serviços
- Campos podem usar tabela customizada de armazenamento; não presumir sempre CP_ORDEM_SERVICO. O instrutor apresenta criação pela ferramenta, sem CREATE TABLE manual. Verificar configuração efetiva do campo antes de montar SQL.
- Quadros 03:25:00 e 03:26:45 mostram diagrama nativo: início verde, tarefa branca, gateway exclusivo amarelo com X, evento de mensagem com envelope, cancelamento rosa com X, final normal rosa e Entrada de Dados laranja associada por traço pontilhado. Entrada laranja aparece no início, tarefa e final. Não transformar automaticamente cada conjunto de campos em tarefa adicional.
- Os mesmos quadros mostram temporizadores associados a tarefas e ramificações de aviso por mensagem. Aparência sozinha não revela toda regra de tempo/repetição; configuração precisa ser conferida em aula específica.
- Pesquisa de satisfação pode ser associada ao finalizador, após cadastro da pesquisa/questões. A consulta de relatório ficou sem dados; não houve resultados de pesquisa demonstrados nesta aula.
- Tipo de serviço, serviço e associação ao subprocesso são etapas de cadastro relacionadas à abertura da OS. Aprofundar na aula de criação, sem inventar valores para o fluxo do usuário.
- Cadastro Web do tipo de subprocesso permite ajustes administrativos mostrados; a modelagem nesta versão é pelo cliente Windows. Não afirmar inexistência de modelador Web em outras versões.
- Integração de inventário OCS foi explicada como possibilidade, não executada. Comentários sobre uso de computador pessoal referem-se ao treinamento e não autorizam acessar a base corporativa.

## Conclusão desta aula
Revisão textual concluída até a despedida, com autenticação omitida nas saídas; revisão visual permanece amostrada. Não foi feita execução no software da empresa, nem validação de scripts. Esta aula é predominantemente visão geral; não é evidência de domínio completo de Toolbox, APIs ou scripts. A revisão da Aula 2 está no relatório individual desta pasta.

