# Revisão da Aula 4 — 08/10/2026

## Cobertura e fontes

Vídeo: [caminho local omitido] 4.mp4, duração 04:00:00,06. Transcrição: Supravizio-Estudos/estudo-materiais/transcricoes/Aula 4.txt, 319 linhas; última fala em 03:54:36. Leitura de todo o conteúdo transcrito, em blocos, excetuados trechos de autenticação. Quadros de exemplos examinados por amostragem, não visualização contínua de todas as imagens. Nenhum script foi executado e nenhum comportamento foi validado por mim na instalação da empresa. Originais preservados.

Consultas cruzadas na cópia local do manual: GUIA-SUPRAVIZIO.md, iniciador_por_temporizador.md, iniciador_por_regra.md, db_executedatatable.md, db_executescalar.md, data_obj_aprovacao.md e propriedades/mensagens de eventos. A documentação e a aula podem descrever versões/configurações diferentes.

Após as despedidas, o áudio apresenta silêncio detectado entre 03:54:42,48 e 04:00:00,06, com limiar -40 dB e duração mínima de cinco segundos. Dois quadros finais mostram a reunião sem conteúdo técnico adicional.

## 00:00–00:11 — Aprovação conjunta, hierarquia e mínimo

Com Cliente e Gestor na hierarquia Única, ambos recebem a aprovação; a primeira decisão favorável não encerra a solicitação. Após a segunda, o fluxo avança para a chamada de fornecedor.

Com Cliente na etapa inicial e Gestor na final, a OS pode mostrar ambas as pessoas como participantes, mas a aprovação só fica disponível para a segunda depois que a primeira aprova. O quadro de 00:07:50 confirma etapas 1 e 2; a execução demonstrada confirma a disponibilidade sequencial. Isso complementa a Aula 3, na qual a hierarquia ficou apenas anunciada.

Ao voltar à hierarquia Única e definir Mínimo aprovadores=1, a decisão favorável de uma das duas pessoas permite avançar. O quadro de 00:09:20 confirma o mínimo 1 e a propriedade Reprovar imediatamente.

O instrutor explica Reprovar imediatamente=True: uma reprovação encerra negativamente a solicitação, mesmo havendo mínimo configurado. O cenário de reprovação não foi executado nesta demonstração. Correção pela documentação: com False, não basta dizer que sempre espera o segundo; a reprovação total ocorre quando já não é possível atingir o mínimo restante. Mínimo trata pessoas aprovadoras, não quantidade de nomes de papéis.

## 00:11–00:21 — Chamada e sincronização de cancelamento

Com Chamada assíncrona=False, a principal aguarda a filha. A filha 117.1 termina suas atividades; ao fechar/atualizar, o pai avança automaticamente.

Com Chamada assíncrona=True, a filha 118.1 fica aberta enquanto a principal segue até o final. Não confundir o nome desta propriedade com a frase contraditória da transcrição sobre chamada síncrona.

Sincronizar cancelamento=True permite propagação entre pai e filha. O primeiro teste não cancela o pai já finalizado; não generalizar a propagação para qualquer situação de ocorrência encerrada. Em novo teste com pai aberto, cancelar a filha apresenta aviso de que a OS 120 também será cancelada (quadro 00:19:00). O sentido pai→filha também é demonstrado. Reabertura associada é comentada, mas suas condições não foram detalhadas o suficiente para prometer equivalência em toda versão.

Aplicar sincronismo apenas quando o requisito pedir cancelamento conjunto. Relacionar processos não implica que cancelamento de um deva invalidar o outro.

## 00:21–00:45 — Modelos e mensagens de abertura

O cadastro Modelo de Comunicado é utilizado na interface Web da demonstração. Ele define o corpo da comunicação, com texto e componentes dinâmicos de OS e link de consulta. Em Tipo de Evento → Abertura, configurar mensagem: descrição, modelo, papel destinatário e processo alvo. A listagem pode incluir destinatários fixos separados por ponto e vírgula; temporalidade é retenção, não prazo de envio.

O papel Cliente recupera o cliente da OS. Isso não garante recuperar a pessoa que efetivamente abriu quando alguém abre em nome de outro.

Na aula, abrir no Workspace para si mesmo não gera o comunicado de abertura para o próprio cliente; mudar o cliente gera. O instrutor diz que o Portal tem comportamento diferente. Tratar como comportamento observado/explicado do ambiente de treinamento, verificando as regras da instalação antes de prometer uma regra universal.

É necessário e-mail no cadastro da pessoa. A rotina de envio de comunicados não estava configurada para entrega real: registros na aba Comunicados comprovam geração interna, não entrega na caixa de e-mail. O quadro de 01:57:20 mostra Envio e redirecionamento de Comunicados suspenso.

Uma base copiada mantinha URL de outra instalação. O link levou ao ambiente errado; alterar a configuração não corrigiu links já registrados. Gerar nova comunicação e conferir URL é diferente de apenas atualizar a tela.

O processo alvo é Administrativo, que contém Adquirir suprimentos e Cadastrar fornecedor; por isso o mesmo comunicado foi gerado para ambos. Para restringir a um subprocesso, a aula usa a sigla de ClasseSubProcesso e cancela somente a mensagem dos demais.

Estrutura normalizada do exemplo (substituir SUP pela sigla realmente cadastrada):

```python
if OrdemServico.ClasseSubProcesso.Sigla != "SUP":
    Mensagem.Cancelar = True
```

Contexto: script da Mensagem Evento. Não cancela a OS. A sigla é obtida em Tipo de Subprocesso ou nas propriedades do fundo do desenho. Verificar sintaxe não comprova sigla correta, destinatário correto nem execução funcional. O quadro 00:41:10 confirma nomes e condição; capturas durante digitação não devem ser copiadas como versões finais.

## 00:45–01:10 — Exercício e diagnóstico de comunicação

Procedimento repetido: criar modelo no Web; cadastrar mensagem no evento Abertura; definir destinatário/processo; salvar; abrir OS de teste e conferir Comunicados.

Diagnóstico: verificar e-mail da pessoa, resolução do papel Cliente, processo que contém o subprocesso e filtro por sigla. Em um caso, o script estava sem if e com estrutura incorreta após copiar/colar. Corrigir if e indentação permitiu gerar a mensagem. O quadro 01:05:40 registra uma versão quebrada em edição, não um código aprovado para reutilização.

Cadastros de comunicação utilizados no teste não exigiram nova versão do desenho. Isso não implica que qualquer mudança em processo ativo seja segura ou dispensável de versionamento.

## 01:10–01:32 — Aviso ao iniciar a aprovação

Para notificar sobre pendência, usar evento Início Aprovação. Evento Aprovação representa a decisão favorável e só disparou após aprovar, no teste dos alunos. Reprovação é outro evento.

O nome sugestivo Aprovador de um papel não garante que ele resolva os aprovadores atuais. Conferir sua definição e compará-la aos papéis da operação verde: Cliente/Gestor no exemplo.

Um script já cadastrado gerava um corpo próprio em Mensagem.Corpo, causando aparente divergência com o modelo escolhido. O quadro 01:23:40 mostra essa personalização e um link para localhost; é configuração prévia de treinamento, não modelo adequado para o ambiente da empresa. Conferir mensagens existentes e scripts antes de atribuir o resultado apenas ao cadastro novo. O instrutor remove a configuração de teste para isolar o caso; não transportar essa exclusão para produção.

Quando a aprovação já foi iniciada, mudar o evento não reproduz automaticamente o início anterior. Cancelar a versão da aprovação e criar nova versão, ou abrir outra OS de teste, foi usado para gerar o evento novamente. Cancelar aprovação não é reprovar, nem cancelar OS, nem mudar versão do processo.

Intervalo: aproximadamente 01:32:07–01:49:47.

## 01:49–02:04 — Iniciador por Timer

Foi criado Folha de pagamento: Evento Inicial por Timer → Folha de pagamento → Calcular folha de pagamento → Final. Alinhamento dos elementos é ajustado pelos comandos da barra do editor.

Configuração demonstrada: ciclo diário, segunda a sexta, 08:00 e serviço inicial. Também são apresentadas opções semanal, mensal e anual. Último dia do mês evita pressupor que todos tenham dia 30/31.

A Máquina de Processos em Utilitários → Gerenciamento de Ambiente verifica os eventos. Repetir solicita nova execução; conferir data de última execução e relatório antes de afirmar geração. O ciclo do job é diferente do ciclo do evento Timer. Não interpretar o exemplo como garantia de pontualidade de oito horas exatas.

Divergências importantes com o manual local:

- Aula gera retroativamente no mesmo dia uma OS marcada para 08:00 após ativação à tarde; manual diz que a ativação só gera para data/hora maior ou igual à corrente.
- Aula gera OS atribuída a Sistema apesar do aviso de responsável ausente; manual diz que sem responsável o iniciador é desconsiderado.

Não conciliar essas diferenças inventando uma regra. Configurar serviço e responsável reais e verificar o comportamento na versão instalada. O exemplo genérico não é uma configuração pronta para produção. O manual também informa que fluxo com somente iniciadores Timer não aparece para abertura manual no Portal/Workspace.

## 02:04–02:15 — Regra, conexão externa e tipo de retorno

A pergunta sobre uma data de outro sistema é respondida com Evento Inicial por Regra e consulta via conexão externa cadastrada. Nome da conexão identifica a base; sem segundo argumento, DB utiliza a base do Supravizio. Conexão real não foi validada nesta revisão.

A primeira explicação diz que a regra deve retornar lógico; posteriormente a aula e o manual demonstram que pode retornar DataTable. Ambos são possíveis: lógico habilita geração; DataTable gera uma OS por linha, lista/array por item.

DB.ExecuteScalar retorna a primeira coluna da primeira linha, não uma linha inteira nem uma contagem automática. Para avaliar existência com >0, a consulta precisa retornar uma contagem ou número compatível; comparar uma data/nome retornado pelo exemplo com zero não é uma solução completa. DB.ExecuteDataTable retorna uma tabela, e suas linhas são acessadas por Rows.

No Script Evento, dados da linha podem preencher a OS via Regra. Se várias linhas forem percorridas atribuindo o mesmo campo simples, o último valor pode sobrescrever os anteriores. Grid é necessário quando o requisito pede armazenar várias linhas numa única OS.

## 02:15–02:34 — Encontrar ocorrências e modelo de dados

O relatório da última execução do job pode já ter sido substituído por outra execução. Ausência ali não prova que a OS não foi gerada. Consultar fila do responsável, pesquisar o número ou usar tabela dinâmica do elemento.

No treinamento, uma tela de remoção de OS também foi aberta apenas para localizar números. Ela tem botão destrutivo: não é o método recomendado para consulta. Não foi removida nenhuma OS nesta revisão.

Timer também pode ter Regra, avaliada no ciclo do Timer; iniciador por Regra é avaliado no ciclo do job.

Tabelas discutidas: OCORRENCIA, ORDEM_SERVICO, CLASSE_SUBPROCESSO e CP_ORDEM_SERVICO. A demonstração relaciona customizados à CP e campos nativos a tabelas específicas, por exemplo Descrição detalhada em ORDEM_SERVICO. Não presumir que todo campo de toda classe esteja em CP_ORDEM_SERVICO. Conferir chaves, classe e armazenamento no modelo real.

## 02:34–03:26 — Exercício Eventos/Cronograma

Enunciado visual conferido em 02:37:20; apesar do título do bloco de notas dizer exercício aula 3, ele faz parte do arquivo Aula 4.

Dentro de Lista de atividades, criar Eventos: preencher Descrição detalhada, Data início previsto e Data fim previsto; análise pelo comitê com Cliente e Gestor do cliente; aprovado chama Cronograma, reprovado cancela. Cronograma tem Dados do evento com os mesmos três campos e Disponibilidade dos instrutores com Justificativa, depois final. Os aprovadores devem ser avisados a cada nova aprovação.

A recorrência mensal no texto não foi imposta como Timer obrigatório pelo instrutor. Forma de hierarquia/mínimo foi deixada para o exercício, não fixada como requisito universal.

Na Atividade Chamada, Parâmetros de entrada passam os campos do pai ao filho. Nativos são selecionados como Propriedade, customizados na opção correspondente. Para visualizar os dados, incluir os campos na Entrada de Dados do filho; passagem não é desenho automático do formulário.

Aprovação sem dados configurados gera pendência; Complementar a partir de ou coleção Campos para Aprovação foi a correção. Dois papéis resolvendo a mesma pessoa não cumpriram mínimo de duas pessoas: corrigir participantes, depois recriar a aprovação/OS de teste. Um destinatário sem e-mail não recebeu a comunicação gerada.

Outra falha de avanço foi corrigida selecionando novamente regra do gateway. A causa interna de perda da configuração não foi comprovada.

Para devolver Justificativa, configurar Parâmetros de saída no subprocesso invocado Cronograma, não no pai Eventos. O retorno é demonstrado ao concluir o filho; o pai exibe a Justificativa. Campo de entrada opcional evita exigir antecipadamente um resultado ainda não devolvido. É possível associar Entrada de Dados ao finalizador, como mostrado, sem inventar uma tarefa extra apenas para o desenho.

A tela de 03:22:30 mostra uma solução de aluno com Responsável e Gestor na aprovação, diferente do Cliente e Gestor do cliente do enunciado. Distinguir adaptação do exercício e requisito original.

## 03:27–03:54:36 — Regra com SQL, campos e criação em lote

Criado/reutilizado campo NOME_FUNCIONARIO e criado AREA, alfanumérico/TextBox. Nome técnico vai para coluna e difere de rótulo/descrição; largura de 400 pixels é apresentação, não comprimento máximo de texto.

A consulta relaciona PESSOA, CP_PESSOA e depois ORGAO. DATA_ADMISSAO é customizado nesse ambiente. IS NULL/IS NOT NULL muda o conjunto selecionado; não copiar o filtro de uma etapa intermediária como regra final. Tabelas Z de listas/grids têm nome específico por definição; não presumir próximo número ou mesmo identificador em outra base.

Regra com DB.ExecuteDataTable cria OS por registro. Script Evento preenche os campos com valores de Regra. Em 03:41–03:43, a primeira tentativa falha por serviço ausente; depois de configurar serviço são geradas duas OS. Falta de deduplicação faz o mesmo conjunto elegível gerar novas OS em próximas execuções. Desativar o iniciador interrompe o teste; uma solução real precisa definir como identificar/retirar registros já processados.

Depois a consulta é ampliada para trazer área; o instrutor esquece de atualizar a consulta usada no iniciador e gera mais OS que o esperado. O quadro 03:48:30 confirma várias ocorrências. Os campos nome e área são vistos preenchidos, mas isso não torna o mecanismo de lote pronto para produção.

Atribuições observadas no Script Evento:

```python
OrdemServico["NOME_FUNCIONARIO"] = Regra["NOME"]
OrdemServico["AREA"] = Regra["AREA"]
```

São exemplos dependentes de campos existentes e aliases da consulta. Se a coluna vier como DESCRICAO, o acesso deve corresponder a esse nome ou a um alias explicitamente definido.

## Correções do exemplo final de grid

O instrutor explica a alternativa de uma só OS com várias pessoas num grid, mas não conclui execução desse exemplo. O quadro 03:52:50 contém código incompleto: ExecuteScalar seguido de pessoas.Rows, for in linha pessoas.Rows e chamada AdicionaLinhaRegistro parcialmente preenchida. Portanto não é script reutilizável tal como aparece.

Correção conceitual: consulta de várias linhas deve retornar DataTable; iteração é for linha in pessoas.Rows; nome do campo grid, nomes de colunas e valores devem existir e estar alinhados. O método apresentado é OrdemServico.AdicionaLinhaRegistro, mas assinatura/tipos precisam ser conferidos no ambiente antes de produzir um script final. Não anunciar sucesso da execução do grid. A regra lógica para uma OS com grid também precisa evitar criação repetida a cada job.

## Aplicação futura

Conferir pessoas distintas e quantidade/hierarquia; evento de comunicação correto; papel destinatário e e-mail; geração interna versus envio; associação e sincronismo; serviço/responsável de iniciador; tipo de retorno da regra; campos e aliases; parâmetros de entrada/saída; registros já processados. Testes futuros devem incluir aprovação conjunta/sequencial/mínima, reprovação, cancelamento pai/filho, retorno de parâmetros e repetição do job.

## Evidências visuais

25 quadros examinados nos segundos: 420, 470, 560, 620, 850, 1140, 1660, 2410, 2470, 3940, 5020, 6890, 7040, 7110, 7800, 9440, 11520, 12150, 13190, 13270, 13560, 13710, 13970, 14110 e 14370. Nem todos mostram uma configuração concluída: 11520 é autenticação sem estudo de credenciais; 420 carregamento; 2410/3940/7800/13190/13270 são edição intermediária; 14110/14370 são reunião no final. Quadros não publicados.
