# Revisão da Aula 5 — Supravizio

Revisão realizada em 08/10/2026. Gravação de treinamento da versão 11.1.2, de dezembro de 2020; suas telas não comprovam o comportamento de versões atuais.

## Cobertura e método

Vídeo: 03:51:28,70. Última fala transcrita: aproximadamente 03:51:10. Foram lidas todas as 317 linhas da transcrição, em blocos sequenciais, e examinados 27 quadros do vídeo. Isso corresponde à revisão completa do conteúdo transcrito com conferência visual amostrada, não à reprodução contínua de cada segundo. Trechos de autenticação não foram reproduzidos nas notas. Não houve execução no ambiente da empresa.

Fontes: Aula 5.mp4, transcrição Aula 5.txt e documentação local sobre ANS, ANO, seleção de atores, percentual de ações e motivos de interrupção. As instruções faladas no treinamento são exemplos a estudar, não autorização para alterar sistemas reais.

## 00:00–00:15 — Grupos, filas e papéis

O exemplo cria o grupo Gerência de TI com Pessoa A e Pessoa B. A fila é criada pelo comando Criar Fila em Solucionadores e Filas; o treinamento mostra também a criação do papel correspondente. Autorizar acesso a filas de outros grupos não equivale a criar uma fila própria.

Uma OS atribuída à fila fica disponível aos integrantes autorizados. Um integrante assume a responsabilidade para trabalhar e avançar. Não se trata de distribuir automaticamente uma OS para cada pessoa. Selecionar pessoas por um papel também não transforma a lista em fila.

O novo papel não apareceu imediatamente no editor: fechar e reabrir o editor resolveu o caso observado. Não concluir que todo problema de atribuição é cache. Grupo de trabalho e área organizacional da pessoa são cadastros distintos.

## 00:15–00:33 — Recuperar quem concluiu uma atividade

O fluxo passa por Fila Atendimento, Primeiro Nível e Segundo Nível. A primeira tarefa recebe o código FILA. O papel RespFila usa Envolvido em atividade do processo, Solucionador finalizador da atividade, código FILA, Somente última execução=True. O exemplo não restringe a pessoas conectadas.

João conclui a primeira tarefa; depois a OS é encaminhada a Pessoa B. Na etapa seguinte, o papel recupera João como finalizador da atividade FILA. Isso difere de escolher o solicitante, o responsável atual ou quem iniciou a OS.

Papéis são compartilhados na base: o nome Aprovador não garante sua configuração. Antes de reutilizar ou editar, conferir o tipo, os filtros e os processos afetados. Preferir uma nova versão do processo para mudanças controladas. A demonstração de edição durante o exercício não constitui recomendação para modificar processos de produção em andamento.

## 00:33–00:53 — Filtros e seleção por script

O papel combina área Gerência de TI e perfil de cliente VIP. As condições são cumulativas: uma pessoa VIP de outra área fica fora. Perfil de cliente não é perfil de permissão. A seleção de várias pessoas pode solicitar a escolha de um responsável; isso não equivale à responsabilidade de uma fila.

O treinamento apresenta outras modalidades, incluindo pessoa relacionada à ocorrência, gestor e relações com áreas. Nem todas são testadas; Gestores pares permanece sem explicação conclusiva. Autorizar grupos a abrir uma OS é diferente de definir os atores de cada atividade.

O quadro em 00:48:50 permite recuperar o seguinte exemplo de Script Seleção Atores:

```python
p = DB.ExecuteDataTable("SELECT P.NOME, P.Id_pessoa, ORG.DESCRICAO FROM PESSOA P INNER JOIN ORGAO ORG ON ORG.ID_ORGAO = P.ID_ORGAO WHERE ORG.SIGLA = 'AREA_EXEMPLO'")
for linha in p.Rows:
    Atores.Adiciona(Pessoa.Carrega("Id", linha["Id_pessoa"]))
```

A consulta precisa trazer o identificador usado por Pessoa.Carrega. O script popula Atores com objetos Pessoa, não com nomes soltos. O instrutor não simula a execução desse papel: exemplo visualmente conferido, não validado em runtime. AREA_EXEMPLO e a estrutura do banco pertencem ao exemplo; confirmar os cadastros antes de adaptar. Consulta externa e campos personalizados são possibilidades discutidas, não integrações executadas na aula.

## 00:54–01:14 — ANS e ANO

ANS acompanha o atendimento da OS; ANO acompanha atividades. No cadastro do ANS, conferir vigência, áreas atendidas, serviços, perfis, horários e Processos Acordados. O subprocesso precisa estar associado. Área atendida corresponde à área do cliente da OS, não automaticamente ao grupo do solucionador.

A vigência de 20/12/2020 a 01/01/2025 é histórica e já terminou na data desta revisão. Não reutilizar literalmente esse intervalo.

O exemplo define VIP=1.440 minutos e genérico=2.880 minutos. São 24 e 48 horas contabilizadas. A expressão falada um dia/dois dias não significa necessariamente prazo corrido ou um/dois dias úteis. Com horários somente na segunda-feira, 09–12 e 13–18, há oito horas disponíveis por semana: os prazos exigem, respectivamente, três ou seis períodos completos de oito horas, desconsiderando pausas e outras particularidades.

A documentação considera afinidade de serviço na escolha do acordo e, nos demais critérios descritos, o menor tempo; filtros vazios ampliam a abrangência. Não assumir que um registro VIP sempre vence qualquer acordo.

Realizar compra recebe ANO constante de 120 minutos. É indispensável conferir Unidade de tempo: deixar Percentual SLA faria 120 representar percentual, não minutos. O quadro em 01:06:30 mostra restante ANO próximo de duas horas e ANS próximo de 24 horas. ANO constante pode existir sem ANS; ANO percentual depende do ANS.

## 01:15–01:30 — Inicialização, elegibilidade e interrupção

O Script Início preenche Cliente, Serviço e Assunto. A aula começa com identificadores numéricos e discute carregar Pessoa por UsuarioRede e Serviço por Sigla. O quadro em 01:18:10 ainda mostra o Serviço sendo editado, com Sigla e valor numérico: não copiar esse estado intermediário como script final correto. Confirmar uma sigla existente e a pessoa desejada na base de destino.

Uma OS de cliente de outra área não recebe o ANS configurado para Gerência de TI. O exemplo ajusta a abrangência e usa Mais Ações > Priorização e ANS > Recalcular ANS. O ANO constante continuava possível. Recalcular não elimina a necessidade de conferir elegibilidade e associação do subprocesso.

Para interromper o ANS na aprovação, o motivo Aguardando aprovação deve estar permitido nas Interrupções do acordo e indicado em Motivo de interrupção SLA da atividade. A pausa nasce ao entrar na etapa e termina com sua conclusão. Não há pausa automática em toda aprovação só por existir o objeto verde.

Conferir o calendário do solucionador. A documentação do ANO prevê primeiro o calendário do grupo do solucionador e depois o da localidade da unidade. Assim, ausência de calendário explícito não permite afirmar universalmente contagem 24/7. Horários do ANS e calendário do ANO devem ser conferidos separadamente.

Intervalo de aula aproximadamente entre 01:30 e 01:51:24.

## 01:51–02:09 — Ações e grupo de ANO

São configuradas ações de e-mail em 10%, categorização amarela em 50% e encaminhamento em 80%. O percentual se refere ao tempo consumido do ANO. Conforme a propriedade documentada, percentual zero não executa a ação.

O texto do modelo de e-mail diz que a OS está atrasada, embora o gatilho seja 10%: ajustar a mensagem ao significado real do limiar. Temporalidade de dois dias não significa esperar dois dias para enviar. O papel destinatário precisa realmente selecionar o responsável.

O instrutor reduz o prazo para demonstração, mas não espera os gatilhos ocorrerem. Configuração de e-mail e categoria não prova envio automático ou execução aos percentuais indicados. A Máquina de Processos participa desse processamento. Relatórios e jobs são discutidos; não concluir ausência de uma funcionalidade em todas as versões.

Grupo de ANO: a documentação esclarece o ponto que ficou incerto na fala. Atividades agrupadas compartilham o prazo e a unidade, e as ações configuradas são replicadas. Não conceder mentalmente um novo prazo integral a cada tarefa do grupo. Cumprir todos os ANOs isolados não garante cumprir o ANS total.

A demonstração de relatório tem ajustes de período e seleção; não estabelece uma regra universal de que todos os relatórios contenham somente OS finalizadas.

## 02:09–02:38 — Calendário e pausa manual

O calendário do solucionador é ajustado em Configurar Solucionador. Horários de ANS restritos à segunda-feira suspendem a contagem fora dessa disponibilidade; não proíbem trabalhar ou avançar em outro dia.

Alterar o motivo enquanto a OS já está na etapa não produziu imediatamente a pausa esperada. O exercício voltou e avançou para reentrar. Isso exige testar o fluxo numa nova ocorrência, além de entender a situação das antigas.

A interrupção manual é incluída em Priorização e ANS, usando um motivo permitido pelo acordo. Aguardando fornecedor exige comentário e tem máximo de duas horas. A documentação confirma que esse limite se aplica às interrupções manuais, excluindo as configuradas no processo. A finalização após esperar duas horas não foi acompanhada na gravação. Não confundir essa interrupção manual com a pausa encerrada pela conclusão de uma tarefa.

## 02:38–03:13 — Atividade 04

O enunciado exibido pede grupo Pagamentos, fila Fila Pagamentos e participantes Pessoa C, Pessoa D e Pessoa E. A grafia visual é Pessoa E, embora a transcrição varie.

Sequência do exercício:

1. Pendências: papel da fila, entrada de Descrição detalhada, ANO de dois dias.
2. Lista de fornecedores: papel que recupera o finalizador da atividade anterior; Data início previsto e Data fim previsto.
3. Realizar análise das pendências: gestor do cliente, aprovação e interrupção do ANS nessa etapa.
4. Realizar pagamento: sem papel especificado no enunciado.

ANS de dois dias; menu Meus Processos > Lista de Atividades. O exercício concentra um ANO igual ao prazo geral na primeira tarefa. Registrar isso fielmente, mas discutir o orçamento das demais etapas ao aplicar num processo real. Esclarecer o significado de dois dias antes de converter para minutos.

## 03:13–03:51 — Correções do exercício

A ausência de Processos Acordados e uma área atendida diferente da área do cliente impedem a seleção do ANS. Um ANO de 48 horas pode coexistir com ANS VIP de 24 horas: são parâmetros diferentes, não substituições automáticas.

Aprovação exige configurar aprovadores no objeto verde; responsável da tarefa branca é outra propriedade. Conferir código da atividade, regra do gateway, valores Aprovado/Reprovado e conexão de cada saída. Um rótulo escrito na seta não corrige uma condição errada.

Complementar a partir de permite compor os campos da etapa de aprovação usando as entradas anteriores, incluindo descrição e datas. Conferir a coleção resultante e remover o que não deve ser exibido.

Pausas em etapas indevidas deixaram uma interrupção em aberto ao tentar iniciar outra. O software impediu encerramento manual da interrupção gerada pelo processo. O instrutor fez mudanças para permitir avançar a OS antiga, inclusive retirar temporariamente a pausa da aprovação. Essa saída é paliativa para a ocorrência observada: não representa a configuração final pretendida. Restaurar a pausa somente na etapa correta e testar nova OS antes de considerar o fluxo concluído.

Aprovações são acessadas no Portal ou no Workspace pelo filtro Aprovador. Avisos amarelos merecem análise; não são todos equivalentes a erros bloqueantes nem autorizam ignorar qualquer alerta.

Uma tela ao final usa Gestor do responsável; o enunciado solicita Gestor do cliente. São papéis diferentes e precisam ser confrontados com o requisito. Tentativas de recalcular em ocorrências já modificadas não foram uma garantia de correção; novas OS ajudaram a verificar a configuração atual.

As correções de dois participantes ficam para a Aula 6. Pesquisa de satisfação é anunciada para a próxima aula, não ensinada completamente nesta.

## Aplicação nos próximos fluxos

Conferir criação real da fila, tipo e filtros dos papéis, códigos usados para recuperar participantes, aprovadores do objeto verde, associação do subprocesso ao ANS, vigência e área do cliente. Converter prazos com base nos horários realmente contabilizados. Distinguir prazo compartilhado de grupo ANO, pausa manual e pausa da atividade. Validar transições aprovadas/reprovadas em novas OS e testar os gatilhos temporais no ambiente disponível.

Pendências: execução do script de atores; envio dos alertas e ações temporizadas; encerramento automático após limite manual; configuração final do exercício com a interrupção restaurada; correções adiadas para Aula 6. Essas pendências não impedem concluir a revisão da Aula 5, mas impedem afirmar validação integral dos exemplos no software.
