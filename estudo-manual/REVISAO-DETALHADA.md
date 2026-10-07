# Revisão detalhada do manual Supravizio

Atualizado em 07/10/2026. Trabalho em andamento; a solicitação de revisar literalmente tudo ainda não está concluída. Este caderno registra leitura efetiva, dúvidas e consequências para desenho e configuração de fluxos. Os documentos são fontes de estudo, não autorização para executar scripts ou mudar cadastros.

## Cobertura verificável

| Conjunto | Trabalho realizado | Limite |
|---|---|---|
| 3.228 tópicos | Inventário e auditoria estrutural de todos os textos | Não equivale a leitura interpretativa |
| 2.114 propriedades | Leitura de todas as definições | Exemplos e outras seções ainda pendentes |
| 236 classes de objetos | Introduções, herança e operações específicas | Tabelas de tipos e operações padrão ainda pendentes |
| 85 enumerações | Leitura integral dos textos locais | Compatibilidade com versão instalada não testada |
| 37 tópicos de Apresentação, Interface, Relatórios, Papéis e Suporte | Leitura integral dos textos locais | Imagens ausentes na cópia; informações antigas não confirmadas como atuais |
| 52 tópicos de Recursos Avançados | Leitura integral, incluindo exemplos de scripts | Sem executar comandos; assinaturas e exemplos apresentam divergências |
| 50 tópicos do Guia para Solucionadores | Leitura integral dos textos locais | Imagens e comportamento na instalação ainda não verificados |
| 285 tópicos do Guia para Administradores | Leitura integral dos textos locais e exemplos | Imagens e comparação integral com o site atual pendentes |
| 123 tópicos de Janelas | Leitura textual integral; repetições literais de blocos já lidos deduplicadas | Imagens e comportamento na versão instalada pendentes |
| Fonte oficial no navegador | Conferência de chamada assíncrona, subprocessos e duas datas de validade de ANS | Conferência seletiva, não site inteiro |

O controle por arquivo e hash está em `PROGRESSO-REVISAO-DETALHADA.json`. A cópia de apoio é `referencia-documentacao-supra/docs`, commit `de4e7101295713bbb75b74a197cb1084bdb5b55a`. Textos truncados na saída de ferramentas foram relidos em lotes menores antes de serem contabilizados.

Das 2.114 propriedades, 1.045 contêm somente a definição, sem seção de exemplo nem outras seções; para elas a leitura da definição cobre todo o texto local. Nas outras 1.069, exemplos permanecem pendentes individualmente. Foram identificadas seis estruturas genéricas nos blocos de código e lidos representantes de cada uma, o que não equivale a conferir todos os valores e tipos de cada exemplo.

## Divergências que exigem conferência

1. **Chamada assíncrona:** a [propriedade](https://help.supravizio.com/prop_atividade_chamadaassincrona.htm) descreve bloqueio até o término; o [artigo de subprocessos](https://help.supravizio.com/subprocessos.htm) explica que falso aguarda e verdadeiro permite avanço, com restrições de sincronização. A contradição também existe no site consultado. Usar a explicação do artigo como hipótese de configuração, sujeita a teste na versão instalada.
2. **Validade de ANS:** [início](https://help.supravizio.com/prop_acordonivelservico_datainiciovalidade.htm) e [fim](https://help.supravizio.com/prop_acordonivelservico_datafimvalidade.htm) apresentam comparações aparentemente invertidas com a abertura da OS. Não inferir o comportamento executado apenas desses parágrafos.
3. **Calendário e ANS:** as introduções locais de `objetos_calendario` e `objetos_acordonivelservico` parecem trocadas. A definição de `UnidadeNegocio.Calendario` também descreve ANS. Consultar os cadastros e a propriedade efetivamente utilizada.
4. **Gateways:** `enum_tipogateway` lista apenas decisões exclusivas; o tutorial do Editor documenta também inclusivo e paralelo. A enumeração não prova ausência desses recursos.
5. **Eventos iniciais:** `enum_tipoatividade` associa InicialRegra a temporizador e InicialTimer a fórmula, invertendo os conceitos usuais e os rótulos. Verificar a tela e os exemplos específicos antes de gerar código numérico.
6. **Limites de prioridade:** descrição do método e definição do grau diferem entre maior e maior ou igual. Testar valor exatamente no limite.
7. **Métodos:** `ObtemAssociacaoComoFonte` aparece com assinatura de outro nome; `ObtemHorasApontadas` contém grafia divergente na assinatura. Confirmar API da instalação antes de usar.
8. **Exemplos genéricos:** 80 páginas de identificadores automáticos contêm exemplos de atribuição. Isso não autoriza alterar IDs. Exemplos que atribuem `DateTime` como valor são moldes incompletos.
9. **Documentação antiga:** requisitos citam navegadores e plataformas antigas; a tabela de compatibilidade perdeu os marcadores na extração. Não recomendar infraestrutura a partir dela.

A auditoria adicional de sintaxe, referências ausentes e outros sinais está em `PONTOS-DE-CONFERENCIA.md`; esses sinais são suspeitas, não testes de defeito no produto.

## Regras para construir fluxos corretamente

### Desenho e execução

- `Figura` contém posição e dimensões, associadas às entidades semânticas de atividade, gateway e operação. Aparência sozinha não configura execução.
- Códigos de atividade e gateway são únicos dentro da versão de subprocesso. Códigos de atividade participam da correspondência de aprovações ao reclassificar versões.
- Emissores possuem sequência de avaliação; decisões exclusivas dependem da primeira alternativa satisfeita. Não tratar todas as fórmulas como caminhos simultâneos. Saída padrão de gateway inclusivo possui configuração própria.
- Desativar uma operação modifica execução automática e validação. `BloquearPendencia` interfere no avanço. Documentar ambas as escolhas.
- Chamadas de subprocesso precisam indicar abertura, vínculo das OS e sincronização; desenhar apenas um retângulo de subprocesso deixa regras essenciais indefinidas.

### Papéis e autorização

- Cliente, usuário autenticado, favorecido e responsável inicial são referências diferentes. Trocar o cliente no Portal pode alterar regras de aprovação inicial.
- Hierarquia organizacional e hierarquia de grupos de trabalho são estruturas distintas. Nem toda recuperação inclui subgrupos; explicitar quando a consulta é recursiva.
- Calendários influenciam seleção de atores. Ausência de calendário/períodos pode resultar em disponibilidade 24x7. Restrição de unidade pode ser ignorada quando falta o local do cliente.
- Papéis compostos unem pessoas sem duplicidades; papéis inativos são ignorados na seleção de atores.
- Perfis somam acesso a menus, mas restrições de dados são combinadas. Ocultar campo prevalece sobre desabilitar campo.
- Desativar grupo pode desativar seus profissionais. Não confundir ajuste de responsabilidade com simples alteração de aparência.

### Aprovação e formulários

- Assunto, versão, passo e aprovação por pessoa são entidades diferentes; guardar também o aprovador real quando houver substituição.
- As situações de aprovação são Elaboração, Pendente, Aprovado, Reprovado e Cancelado. Elaboração ainda requer iniciar o pedido.
- Campos apresentados para aprovação e campos preenchidos pelo aprovador têm funções distintas. Os controles documentados para preenchimento de aprovação são TextBox, Memo e DropDownList.
- Substituição pode depender da data de acesso atual; não presumir que seja fixada na criação da aprovação.
- `ValidaPendencias*` retorna verdadeiro quando não há pendências. `PossuiAprovacao(codigo)` representa aprovação concluída favoravelmente.
- `LookupScript` de propriedade/coluna deve retornar DataTable com valor armazenado e texto exibido. Fórmulas de colunas calculadas não são necessariamente persistidas para SQL.

### Itens, anexos e efeitos posteriores

- Item requerido no início e produzido no término são alternativas mutuamente exclusivas na classe de anexo.
- Alterações de usuários de itens realizadas na finalização não são automaticamente revertidas por reabertura ou Voltar.
- Adicionar/remover usuários de itens pode mudar responsabilidade ou transferi-la ao gestor. Registrar esses efeitos no projeto do fluxo.
- Métodos `ObtemItem` e equivalentes exigem exatamente um resultado; nenhum ou vários podem provocar erro. `Possui*` tem outro contrato.
- `ModificaSituacao` de item grava imediatamente; não presumir alteração apenas em memória. `AnexaArquivo` possui opção de apagar o original.

### Tempos e indicadores

- ANS mede atendimento e ANO pode medir atividade/grupo. As unidades variam entre propriedades e métodos; não somar dias, minutos e segundos como se fossem uma unidade comum.
- ANO pode usar minutos de calendário, percentual do ANS ou horas apontadas. Apontamentos cancelados não são visíveis aos scripts; confirmação, apropriação e aprovação são estados distintos.
- Interrupção de ANS pendente de aprovação ainda permite incremento de prazo; aprovação e finalização têm efeitos próprios.
- Meta e sentido de melhor desempenho precisam ser tratados juntos. Atualização de meta pode alcançar períodos cuja meta anterior coincida.
- Existência do módulo de indicadores não muda o requisito RVA de registrar/apurar valores. Não inventar cálculo ou automação não exigidos.
- Rotinas automáticas podem parar após erros sucessivos. Projetar tratamento de falha e consulta de histórico quando houver automação.

## Relatórios: consequências da leitura integral

- Definir a data de referência: abertura, finalização, resposta à pesquisa, execução de atividade e reabertura produzem conjuntos diferentes.
- Filtro de finalizadas pode excluir canceladas; Não realizada pode entrar no grupo de cancelamento. Reaberturas podem fazer a mesma OS aparecer em períodos diferentes.
- Relatórios podem aplicar filtro implícito por macroprocessos para usuários sem perfil Administrador. Resultado vazio não comprova ausência de OS.
- Apontamentos respeitam visibilidade por administrador, coordenação com subníveis ou apenas o próprio usuário. Isso afeta comparação de totais.
- Recebidas × Solucionadas trata como não solucionadas também ocorrências encaminhadas a outra pessoa sem solução; não interpretar como fila corrente apenas.
- Pendências acumuladas consideram saldo anterior ao período. Soma simples de aberturas menos finalizações no intervalo pode diferir do acumulado.
- Tabelas dinâmicas têm linhas, colunas, filtro e totalizadores. O filtro continua aplicado mesmo quando não está exibido em linhas/colunas.
- Tabela de itens requer ao menos um tipo de item; campos associados a OS requerem também seleção de subprocesso.
- Tabelas de OS e atividades podem contabilizar atividades canceladas. Definir tratamento delas antes de apresentar indicadores.
- Pesquisa considera escore negativo como menor que zero e positivo como maior ou igual a zero. Zero não é negativo.
- Campos customizados podem ser adicionados à tabela dinâmica de OS; disponibilidade não significa que toda fórmula calculada exista no banco.

## Trabalho ainda necessário para cumprir “literalmente tudo”

Revisar integralmente os textos do Guia para Administradores, Janelas e demais tópicos de Customização; conferir 239 tópicos de tabelas do modelo de dados; revisar exemplos de scripts e tipos de propriedades; comparar a cópia com o índice e páginas atuais; inspecionar capturas/diagramas originais. Testes de comportamento dependem de acesso a uma instalação apropriada, e são uma evidência diferente da leitura do manual.

## Guia para Solucionadores: consequências para o desenho

- Abertura no Workspace exige processo ativo, versão ativa, iniciador manual ativo e disponível, grupo envolvido no macroprocesso e eventual participação no papel restrito. Aqui a inclusão de grupos filhos é expressamente documentada; não generalizar isso para todo método de grupos.
- Salvar campos e avançar são ações diferentes. Worklist documenta Enviar, Salvar e Ocultar, além de salvamento periódico; não confundir isso com gravação em todos os formulários do produto.
- Atualização de aprovadores cancela a versão anterior e gera outra. Pode ocorrer manualmente ou pelo job da máquina de processos; texto anuncia duas formas mas enumera três.
- Retomar responsabilidade após encaminhamento depende de a OS ainda não ter sido lida pelo destinatário e de permanecer autorizado a visualizá-la.
- Agendamento altera situação para Agendada, pode exigir motivo/justificativa de interrupção e respeita limite do ANS. Aviso com zero dias ocorre no dia previsto para retorno.
- Cancelamento pelo Portal pode ser permitido apenas em determinadas atividades. Reabertura tem prazo, permissão de subprocesso, identidade do cliente e restrições de OS iniciada por link.
- Sincronização de cancelamento depende de configuração e associação; o exemplo mostra propagação entre OS chamadora e chamada. Remover uma associação, por sua vez, não cancela nem apaga a OS.
- Link Inicial com abertura pelo Workspace permite criar OS associada sem elemento chamador no fluxo principal; observar cardinalidade. Associação existente pode ser feita manualmente.
- Depois do envio da pesquisa, reclassificação pode ser bloqueada. A frase geral de que classificação pode ser alterada a qualquer momento tem essa exceção no tópico específico.
- Depois de registrar entrega de serviço, não é permitido acrescentar interrupção de ANS sem limpar a data; a nova entrega deve ser posterior às interrupções válidas.
- Comunicado pode parar ANS e encerrar a interrupção após resposta; anexos retornados podem virar artefatos de um tipo escolhido. Não é apenas envio de email.
- Comentário de outra pessoa pode marcar a OS como não lida. Publicação de comentário no Portal é opção própria; comunicados no Portal têm regras por remetente, destinatário e superior.
- Gravação de horas muda de OS encerrando gravação anterior e termina ao sair da sessão. Não presume dois apontamentos simultâneos.
- A listagem pode ser limitada por configuração de quantidade máxima. Resultado parcial exige verificar o aviso, além dos filtros e autorizações.
- Pesquisa automática de conhecimento usa palavras-chave dos artigos; título e sumário não são critérios dessa recuperação. OS podem participar de busca manual configurada, mas não da recuperação automática descrita.
- Artigo sem papéis restritivos fica público. Aviso de mural filtrado por grupos no Workspace fica visível a todos no Portal quando publicado ali.
- Fórmula de dados adicionais de cliente deve retornar texto; conversão do valor nulo não dispensa checar objetos intermediários quando puderem faltar.

## Guia para Administradores: primeiras conferências integrais

- Ativar versão executa validação implicitamente; configuração inválida não pode ser ativada. Avisos e pendências têm efeitos diferentes.
- Configuração de autorização por tipo de subprocesso prevalece sobre a global. Público permite leitura ampla, mas não edição indiscriminada. Acesso especial de Admin também depende de opção do subprocesso.
- ANS escolhe regras pela afinidade de Serviço/Tipo de Serviço e depois pelo menor prazo. Campos não preenchidos na regra admitem qualquer conteúdo; não afirmar simplesmente que sempre vence o menor prazo global.
- ANO soma execuções repetidas da tarefa, inclusive após Voltar. ANO baseado em percentual do ANS para quando o ANS é interrompido. Não generalizar essa paralisação aos demais critérios.
- Responsável pelo ANO é, por padrão, o solucionador com maior tempo de responsabilidade; coordenador pode redefini-lo. Agrupamento compartilha prazo, unidade e ações e replica alterações nessas propriedades.
- Interrupção prevista em processo precisa existir no ANS e não pode ser cancelada manualmente como a interrupção manual. Interrupção no finalizador pode excluir tempo finalizado até reabertura.
- Datas de solicitação/entrega afetam também relatório de disponibilidade, não somente cronômetro da tela.
- Exemplo de período de exceção alterna dias 20–30 e 1–10; exemplo de fórmula de disponibilidade contém `ife`. Conferir figura e corrigir somente após confirmar intenção.
- Armazenamento especial de campos de OS pode usar tabelas `CPE_`, além do padrão `CP_`. Como podem faltar linhas para OS que não utilizaram o campo, o exemplo recomenda LEFT JOIN.
- Relatórios combinam `OCORRENCIA` e `ORDEM_SERVICO` por `ID_OCORRENCIA`; Serviço pertence à especialização OrdemServico. Respeitar herança ao consultar banco.
- Campos preenchidos na aprovação podem ficar bloqueados por aprovação válida. Alteração pode exigir cancelar versão e iniciar outra; obrigatoriedade distingue aprovação, reprovação e ambas.
- Bibliotecas devem conter definições de funções; importação é feita no editor e o cabeçalho gerado é somente leitura. Alterar biblioteca compartilhada pode afetar mais de um fluxo e versões legadas.
- Licenciamento possui texto conflitante: administração de conexões diz que nova conexão não é bloqueada; relatório de conexões descreve bloqueio ao exceder licenças. Não determinar política atual a partir de um único tópico.

## Recursos Avançados: revisão dos exemplos

A leitura integral encontrou exemplos que não devem ser copiados diretamente. São constatações da cópia textual, sem prova de execução na instalação:

- `ad_enableuser` descreve desabilitação; `ad_userclearmanager` reproduz integralmente o conteúdo de desbloqueio. Título e corpo divergem.
- `DisableUser`/`EnableUser` têm assinatura `void`, mas o texto promete retorno booleano.
- `CreateUniversalGroup` documenta parâmetro `security` ausente na assinatura; o exemplo chama `CreateGlobalGroup`.
- `CreateUser` usa `LDAP.CreateUser` no primeiro exemplo e `AD.CreateUser` no segundo. `GroupExists` aparece como `AD.DGroupExists`; `UserExists` também aparece como `UserExist`.
- `ResetUser` apresenta assinatura `ADResetUser` e chamada `AD.ResetUser`.
- Há `if` sem dois-pontos, indentação irregular, literais `Falso` e strings quebradas. Preservar a fonte, reconstruir sintaxe e revisar contexto antes de elaborar código funcional.
- `UserIsDisabled` retorna verdadeiro para usuário já desabilitado, mas o exemplo tenta desabilitá-lo nessa condição. `AuthenticateUser` descarta o retorno e depois registra criação de grupo e avanço; isso não comprova autenticação bem-sucedida.
- `UserWriteProperty` alterna entre exceção, falso e nulo para propriedade inexistente. Não escolher contrato só pelo último parágrafo.
- `EntryExists` apresenta assinatura `GetEntry`; `GetEntryByName` promete Hashtable mas descreve False na ausência e o exemplo testa None. `DeleteEntry` tem exemplo com quantidade de parâmetros diferente da assinatura.
- `DB.ExecuteDataTable` retorna tabela vazia quando não encontra linhas. Teste apenas contra None não verifica existência de resultado.
- Exemplos SQL contêm concatenação e erros de parênteses/nomes. `NewDBOutputParam` tem assinatura de um parâmetro, mas um exemplo passa dois.
- Jobs Customizados combinam alteração de pessoa com alteração no diretório; nenhuma transação ou compensação entre os sistemas está comprovada. O exemplo usa `Utils.ExecuteDataTable`/`Utils.ADDisableUser`, enquanto os capítulos específicos usam `DB`/`AD`.
- `SetAccountExpirationDate` mostra soma direta de inteiro a DateTime; conferir operação apropriada na API. Não tratar expiração da conta como expiração de senha.
- Os exemplos de Exchange são explicitamente de 2007; não são receita atual de integração.
- `SendMail` aceita associação de registro e temporalidade em dias. Não inferir entrega confirmada a partir de chamada que retorna `void`.
- Objeto Webservices aparece como `Utils.LoadWebService`, `WebService.LoadWebService` e capítulo Webservices. Confirmar nome disponível no contexto real.

Para fluxo futuro com integração: consultar assinatura confirmada, checar precondições, tratar exceção/retorno e registrar evidência apenas depois de confirmar o resultado. O simples uso de `AvancaProximaAtividade = True` no exemplo não prova que a integração ocorreu com sucesso.


## Continuação: configuração de processos, formulários e Portal

Cobertura textual acumulada: **1.718 de 3.228 tópicos**, com critérios individuais no arquivo de progresso. Leitura textual não inclui imagens ausentes nem testes no produto.

### Elementos e responsabilidades

- Desvio Paralelo cria solicitações filhas em todas as saídas, sem fórmula de seleção. A numeração relativa tem separador configurável. Fonte: `paralelo.md`.
- Desvio por Evento apresenta pergunta ao solucionador; alternativas recebem Texto, motivo pode ser obrigatório e ter rótulo próprio. Publicar resposta no Portal é configuração explícita. Fonte: `pergunta_e_resposta.md`.
- Desvio Exclusivo computa expressão IronPython e compara o retorno com Valor comparação; texto deve estar delimitado como literal. Após aprovação pode utilizar Regra de Desvio apontando para a tarefa de aprovação. Fonte: `por_formula.md`.
- Evento por regra em sequência aguarda condição; avaliação depende do job da máquina de processos. Não prometer reação instantânea.
- Evento intermediário ServiceBus exige parâmetro OrdemServico com NUMERO para direcionar uma OS. Ausência desse parâmetro pode atingir todas as OS esperando pelo evento correspondente. Configuração é aplicada antes do ScriptEvento.
- Link Final oferece criação ou associação e finaliza a ocorrência; criação automática não é conclusão geral. Cardinalidade e associação inversa precisam de configuração própria.
- Recuperação de aprovadores anteriores considera aprovação individual e pode incluir aprovador de versão cancelada. Para reutilizar aprovação válida, estabelecer critério explícito.

### Campos e aprovações

- Tipo, Nome, NomeColuna e NomeTabela de campo customizado são imutáveis após criação segundo o capítulo específico.
- Campo lógico ausente pode retornar False em GetCustom; usar valor padrão None quando a regra precisa distinguir não preenchido de resposta negativa.
- Listas podem exibir descrição e armazenar identificador. ComboBox numérico exige pelo menos duas colunas; capítulo de propriedade com exatamente duas colunas precisa ser interpretado no contexto da versão.
- Listas de registros e listas de objetos têm capacidades diferentes; não presumir listas aninhadas em colunas de registro.
- Precisão Decimal documentada é 15 dígitos e duas casas. Confirmar necessidade dos indicadores RVA antes de selecionar tipo de campo; o exemplo de coordenadas recomenda texto por perda de precisão.
- Aprovação padrão exige todos. Quórum mínimo e ReprovarImediatamente alteram a decisão; uma rejeição não implica necessariamente resultado final reprovado.
- Permitir alteração de campo depois da aprovação é exceção explícita ao bloqueio. Reutilização de pré-aprovação depende de dados inalterados e não é documentada para aprovação hierárquica incremental.
- Evento individual de aprovador e evento de aprovação da versão são distintos; cadastrar mensagens nos dois pode produzir notificações diferentes para a mesma etapa.
- Favorecidos múltiplos na abertura pelo Portal podem criar uma OS por favorecido.

### Inicialização, comunicados e integração

- Timer sem responsável é desconsiderado. Ativação não cria retroativamente OS de datas passadas; nova versão não necessariamente gera segunda OS no mesmo dia.
- Regra que retorna tabela ou coleção pode gerar uma OS por linha/item. Periodicidade da máquina de processos e agenda do timer são conceitos diferentes.
- Exemplo de leitura de arquivo cria OS antes de conferir término ou linha vazia: pode deixar OS adicional e falhar em campos[1]. OrdemServico.Nova cria OS sem associação, diferentemente de iniciador de subprocesso associado. Exemplos exigem revisão antes de uso.
- Descrição do elemento de comunicado pode ser assunto do email. ANS, resposta e incorporação de anexos dependem das opções de comunicado.
- Coletor de email apaga mensagens processadas. Remetente não reconhecido pode resultar em ClienteSistema. Não executar essas rotinas durante estudo.
- Arquivo público permite acesso sem autorização do registro; não equivaler permissões do arquivo às da OS.

### Importações e cadastros compartilhados

- Importação de fluxo requer versões compatíveis, cria versão Em Edição e exige validação/ativação. Novos cadastros são a regra, com exceções como campos customizados e atualização de biblioteca de scripts com mesmo nome a partir da versão descrita.
- Scripts importados preservam identificadores fixos e referências literais; não pressupor remapeamento automático.
- Importação .rec pode atualizar registros existentes e associados; não aplicar a ela a regra do XML de fluxo. Relatório .rel omite string de conexão.
- Importação de RH pode inativar pessoas e órgãos ausentes, conforme opções. Feriados ausentes na fonte são removidos, inclusive os cadastrados manualmente; calendários são preservados.
- No layout de RH, email duplicado é permitido mas compromete recuperação de senha; UsuarioRede é obrigatório e único. ATIVO de pessoa nulo assume S; ATIVO de órgão não admite nulo. Fonte: `layout_fontes_dados.md`.
- OCS utiliza consulta direta ao banco do inventário. O texto chama importação de reversível, mas explica que a rotina não elimina registros já importados: redação contraditória. Trechos de prazo e periodicidade estão incompletos na cópia. Fonte: `ocs_configurando_a_rotina_de_impor.md`.
- Blacklist OCS acompanha nome do software e pode classificar automaticamente outra versão do mesmo nome. Fonte: `ocs_criando_processos.md`.

### Relatórios e Portal

- Dashboard publicado externamente sem autenticação usa ID_PESSOA = -1. Não inferir identidade ou permissões de uma sessão interna.
- Drilldown admite Série ou Argumento em um painel; filtros mestres dependem de campos correspondentes entre fontes. Gráficos podem ignorar filtro configurado.
- Salvar no Editor pode gravar todos os processos modificados, não apenas a guia selecionada.
- Formulário Direto exige subprocesso com iniciador que tenha Código preenchido. Serviço pode ficar em aberto para escolha; permissão de alteração é opção própria. Fonte: `portal_abertura_configuracao_form.md`.
- Assistente tem cinco passos, com opções de omissão; filtro por macroprocessos vazio significa todas as solicitações disponíveis, não nenhuma. Fonte: `portal_abertura_configuracao_assist.md`.
- Portal documenta interfaces separadas para Clássico, Mobile e Tablet; módulos reutilizados têm parâmetros globais e configuração pela página original. Não presumir que cópia de apresentação cria configuração independente. Fonte: `portal_configurando_um.md`.
- Permissões de página e módulo são definidas separadamente. Prazo de página sem datas é indeterminado; Nome participa do endereço e não aceita espaços/caracteres especiais.
- Pesquisa de satisfação enviada ao favorecido, por padrão cliente, respeita percentual de envio. Reabertura e mudança de avaliador podem gerar nova pesquisa preservando a anterior; havendo Favorecido, mudar somente Cliente não garante reenvio. Fonte: `pesquisas_de_satisfacao.md`.

Essas são regras descritas na cópia estudada. Exemplos SQL concatenados, instruções de instalação antiga e rotinas de importação foram tratados como material de referência, sem execução ou alteração de ambiente.


## Conclusão da leitura textual do Guia para Administradores

Os 285 tópicos administrativos foram lidos integralmente na cópia local. Isso inclui todos os tutoriais ali presentes; não equivale à conferência de suas imagens.

- **Raias:** campo Papel define responsabilidade dos elementos, exceto responsabilidade Sistema ou fila; campo Texto sozinho apenas organiza visualmente. Expandir Configuração global do papel altera o papel compartilhado, não só o desenho. Fonte: `raias.md`.
- **Toolbox:** clicar na ferramenta e depois no diagrama; Aprovação deve ser inserida sobre uma tarefa. Point cancela o modo de inserção. Propriedades comuns de seleção múltipla são alteradas em bloco; incluir/remover itens de coleção exige diálogo específico.
- **Prioridade de atores:** menor número tem prioridade maior. Havendo atores na primeira prioridade, grupos posteriores servem como alternativa; mesma prioridade reúne atores. Seleção final pode usar menor quantidade de OS, fila rotativa ou todas as pessoas; Excluir aprovações muda a contagem. Fonte: `tipos_papeis.md`.
- **Papéis e usuários:** perfis de acesso acumulam; solucionador ativo pertence a apenas um Grupo de Trabalho. Redefinição por Serviço ou Item de Configuração pode mudar atores recuperados. Filtros de calendário e unidade de negócio são escolhas próprias.
- **Scripts de tarefa:** há Início, Validação, Fim e Volta, apesar do texto anunciar três eventos. Validação também pode executar na finalização do processo por padrão; pendências impedem transição. Fim executa em avanço automático e manual. Fonte: `tarefas.md`.
- **Restrição do papel:** Responsável não implica automaticamente exclusividade; Permissão restrita Papel responsável controla o bloqueio. Execução fora do papel pode registrar não conformidade quando permitida.
- **Pré-aprovação:** identidade do solicitante no Portal e reutilização de aprovação anterior são duas opções distintas. Decisão após aprovação usa código específico da tarefa em PossuiAprovacao; copiar elemento exige revisar Código e aprovadores.
- **Cancelamento sincronizado:** tutorial documenta também propagação da reabertura entre chamadora e chamada quando Sincronizar cancelamento está habilitado. Reprovação só cancela automaticamente quando o caminho e finalizador estão configurados para isso.
- **Itens de Configuração:** inclusão/remoção de usuário no item não é desfeita por Voltar ou reabrir OS. A associação de usuários no cadastro do item não prova alteração efetiva no diretório externo.
- **Formulários dinâmicos:** Formulário carregado e Script Modificado têm momentos distintos. O manual alterna entre uma execução no início e execução quando carrega/exibe; confirmar comportamento real antes de usar operação com efeitos externos nesse evento.
- **Defeitos nos exemplos dinâmicos:** checkbox lógico é comparado com texto Sim em um exemplo; outro usa string None como sentinela. Exemplo de anexo inicializa visibilidade sempre False mesmo com indicador previamente preenchido. Campos em cascata precisam conferir limpeza de filhos ao trocar o pai e se limpeza dispara outro evento.
- **Peso no grid:** o exemplo multiplica PESO já multiplicado pela quantidade anterior; repetir edição pode acumular multiplicações indevidas. Separar peso unitário e total na implementação. Há consultas em bases distintas e concatenação de texto sem tratamento.
- **Campos calculados:** tutorial explicita que valores da Fórmula de Cálculo não são gravados no banco. Para RVA, indicar quais indicadores precisam de persistência e rastreabilidade, em vez de assumir que aparecem em consulta SQL.
- **Query Builder e parâmetros:** prefixo @ no SQL Server e : no Oracle; seleção usa primeiro campo como valor e segundo como descrição. Exemplo contém Order Bi, corrigido para Order By no passo posterior.
- **Relatórios operacionais:** parâmetro pode ser alterável ou fixo; disponibilização na consulta do Portal é opção explícita. Relatórios em comunicado podem usar DestinatarioMensagem, que é email, para individualizar conteúdo.
- **Dashboard:** publicação por grupos e publicação por link são ações distintas. REFRESH no link tem frequência em minutos. Count exclui Null e DBNull; StdDev/Var e StdDevP/VarP distinguem amostra e população.
- **Portal:** modos suportam recursos diferentes; módulo de abertura documentado apenas para Clássico/Tablet, Consulta Mobile sem Apontamentos/Comunicados; mural apenas Clássico e um por página. Link de Aprovação no índice de módulos aponta incorretamente para Conhecimento.
- **Segurança visual:** ocultar aba/campo é configuração de apresentação; não presumir que bloqueia toda API ou consulta. Escopo customizado usa dados do registro, como órgão/serviço; redação sobre pessoas que podem visualizar exige confirmar semântica, não inferir autorização global.
- **Web Service customizado:** biblioteca gera .asmx quando visível em chamadas; token de usuário é primeiro parâmetro, mas o exemplo PHP não o mostra. XML montado por concatenação não escapa Assunto e mistura texto simples com XML conforme resultado. Rever contrato e serialização.
- **Iniciadores por arquivos:** AnexaArquivo com True no exemplo remove o arquivo de origem. Não executar em diretório real durante estudo. Timer sem iniciador manual não aparece na criação manual.
- **Qualidade:** exclusão de OS pelo Editor remove diretamente do banco e não recicla numeração; isso é operação real, não simulação de leitura. Não executada.

### Conferência visual oficial nesta rodada

A página `https://help.supravizio.com/Supravizio.htm?tutorial06_desenho_do_fluxo.htm` foi aberta no navegador em 07/10/2026. Foram conferidos o texto e imagens iniciais, incluindo o desenho de Calcular Hora extra → Calcular folha → Imprimir contra-cheque. A figura utiliza iniciador verde com relógio, tarefas em retângulos arredondados claros, setas pretas e finalizador rosa/vermelho com borda espessa sobre grade. Essa conferência é parcial; imagens restantes do tutorial ainda precisam de inspeção.


## Janelas: cadastros, indicadores e limites

Foram cobertos os 123 textos de Janelas. A partir do tópico 35, foram omitidos da exibição apenas blocos literalmente iguais aos já lidos; todas as diferenças, regras de campos e listas de dependências foram examinadas. Nenhuma figura ausente é considerada revisada por essa leitura.

- Autorizações de transações acumulam entre perfis; **restrições de registros acumulam por AND**, e ocultar campo prevalece sobre desabilitar. Assim, somar perfis não implica ampliar todos os registros visíveis. Fontes: `authorization_sub`, `memberof_sub`, `role_sub`.
- Nome de Associação é único, alfanumérico sem espaços e normalizado para minúsculas. Cardinalidade Fonte representa sentido alvo → fonte; Cardinalidade Alvo representa fonte → alvo. Inativa impede novas associações, não afirma apagar antigas.
- Redirecionamento de papel e pessoa são mutuamente exclusivos; um limpa o outro. Redefinição por Item de Configuração depende também do tipo do item e configuração do Serviço. Evitar definições recursivas. Fontes: `atoresservico_sub`, `classeconfiguracao_sub`, `servico_sub`.
- Diversas siglas são descritas simultaneamente como convertidas para minúsculas e restritas a maiúsculas. É contradição repetida, não requisito a resolver por adivinhação.
- Filtro de serviços vazio no Tipo de Subprocesso admite todos; restrição por Tipo de Serviço pode admitir todos os serviços daquele tipo. Não equivaler à ausência de Serviço.
- Inativar Grupo de Trabalho desativa solucionadores associados. Permissões de cancelar, encaminhar, classificar, reabrir, interromper ANS e priorizar **não se aplicam recursivamente** a grupos filhos. Hierarquia de equipes não é automaticamente a de Órgãos.
- Calendário do solucionador ausente pode usar calendário de sua unidade; sem localização a disponibilidade pode ser 24×7. A introdução de ANS que resume ausência como 24×7 precisa ser confrontada com esse fallback específico. Fonte: `tecnico_sub`.
- Interrupção de ANS sem aprovadores é automaticamente aprovada. Tempo máximo e comentário obrigatório do Motivo de Interrupção referem-se a inclusões manuais; comentário obrigatório é publicado no Portal.
- Arquivo público é acessível a qualquer usuário **autenticado**. Tipo de arquivo e tipo de artefato são cadastros diferentes. Nome/descrição usados como pasta têm caracteres proibidos.
- Domínio filtra o universo de dados após seleção na conexão e admite customizações próprias. Domínio inativo impede login.
- Eventos customizados têm argumentos somente leitura; implementação pode emitir exceção para interromper modificação. Não inferir reversão de efeitos externos de uma exceção local.
- Indicador define provedor, função de agregação, sentido de melhor desempenho, fórmula de valor e seleção. Sem fórmula de valor, a documentação assume contagem dos registros selecionados; percentual exige fórmula de seleção. Fonte: `indicador_sub`.
- Filtros de OS abertas/canceladas/finalizadas são descritos em função do período. A descrição de finalização com sucesso menciona Data/hora de Execução de Mudança: não tratar como data de encerramento universal sem conferir. Não copiar filtro RVA só pelo rótulo.
- Indicador no Plano possui meta, tolerância, desafio, responsável e períodos. Alterar meta geral atualiza períodos cujo valor era igual ao antigo; ajustes mensais diferentes são preservados. Mesmo critério descrito para meta no período. Fontes: `indicadorplano_sub`, `periodoplano_sub`.
- Plano define datas e grupos autorizados, com inclusão opcional de subníveis. Restrição ao usuário/subordinados e restrição ao responsável do indicador são parâmetros distintos. Valor apurado editável é descrito para provedor Lançamento Manual.
- Cores do painel precisam considerar o sentido de melhor desempenho; texto da meta explica principalmente cenário de maior é melhor. Limites exatos e desafio de indicador inverso precisam de teste.
- Fórmula percentual de envio de pesquisa substitui percentual fixo; 0 nunca envia e 100 sempre envia, mantidas demais condições. Não interpretar 50 como envio alternado determinístico.
- Substituição de aprovação verifica intervalo na data em que a página é exibida, não na data da criação da solicitação de aprovação. Fonte: `pessoa_sub`.
- Autenticação Pessoa/Portal e Usuário/solucionador têm campos e precedências diferentes. Descrição antiga de senha de Portal ignorando AD não deve virar proposta de configuração atual sem conferência.
- Temporalidade de mensagem: zero exclui após envio, nulo preserva, positivo em dias. Anexo precisa existir no instante do envio; registro de mensagem não é prova de recebimento pelo destinatário.
- Consulta de relatório corresponde a banda; bloqueio de edição admite desbloqueio por autor, responsável pelo bloqueio ou Admin. Disponibilidade visual do relatório e autorização de consulta precisam de configuração própria.
- Campo calculado da coluna de registro confirma **não persistência no banco**. O estado Inválido de propriedade customizada indica ausência da coluna física; cadastro de definição não prova armazenamento existente.
- Situação Desativado do item afirma incluir artigo na busca, aparentemente contradizendo descontinuação. Conferir resultado real antes de prometer exclusão de pesquisa.

As imagens do tutorial 6 foram preservadas em `imagens-oficiais/tutorial06_desenho_do_fluxo`, com manifesto da origem. Salvar a imagem não equivale a examiná-la.


## Modelo de dados: primeiros 41 tópicos

Leitura integral da sequência `dados_acao_acordo` até `dados_classe_apontamento` na ordem do catálogo, incluindo relacionamentos e SQL. Outros 198 tópicos de tabelas continuam pendentes.

- APURACAO_INDICADOR guarda valor decimal(15,2), instante de apuração, numerador/denominador para percentual e memória binária de cálculo. Ritmo é documentado somente para Count e ao fim do período equivale ao apurado. Especializações APUR_IND_OS/PESQ/ITEM compartilham chaves compostas; não fazer ligação de apurações apenas por ID_INDICADOR.
- APROVACAO liga aprovador esperado e aprovador real separadamente, além de assunto e versão. UTILIZOU_PRE_APROV e PASSO permitem distinguir reutilização e aprovação hierárquica. Estado individual não é estado da VERSAO_APROVACAO.
- ATIVIDADE.SINCRONIZA_CANCELA descreve cancelamento se **todas** invocadas canceladas, enquanto tutorial descreve propagação de uma associada. Divergência para teste com múltiplas chamadas, sem escolher regra por analogia.
- ATIVIDADE.CHAM_ASSINC repete a descrição invertida já observada. Tipos usam varchar, lógicos char(3); não atribuir ordinal de enumeração ou bool SQL sem conferir representação real.
- ACAO_ACORDO.PERCENTUAL igual a zero desabilita a ação, diferentemente de temporalidade zero que exclui mensagem após envio.
- APLIC_CONH_SERV mostra chave de Conhecimento em branco e exemplo termina em CONHECIMENTO.; o SQL está incompleto. Referência de herança não dispensa verificar a chave de ITEM.
- AFIRM_FINANC utiliza a grafia ID_AFIRM_FIANC, não a grafia intuitiva FINANC. Preservar nome real para validar no esquema.
- CLASSE_ANEXO define requerido na inicialização e produzido ao término como mutuamente exclusivos; configuração de usuários não é desfeita ao voltar/reabrir.
- CAMPO_APROV e CAMPO_PREENCH_APROV são diferentes: campo a ser aprovado versus preenchido na decisão. O segundo documenta apenas TextBox, Memo e DropDownList; validar outros controles na versão antes de sugerir.
- AUSENCIA distingue autorização do substituto para modificar OS e redirecionamento de encaminhamentos; habilitar um não prova outro.
- ASSOCIACAO guarda definição, ASSOCIACAO_OCORR guarda vínculo das ocorrências e autor/data/atividade geradora; ATOR registra pessoas recuperadas para papel naquela ocorrência. Não misturar configuração com evidência de execução.

Arquivo oficial iniciado em 07/10/2026: 3.229 URLs efetivamente extraídas do índice público, em `URLS-OFICIAIS.json`. `salvar_manual_oficial.py` baixa páginas e imagens com quatro conexões, sem executar conteúdo. Manifestos registram bytes, hash, falhas e leitura_confirmada=False. A aquisição é separada da revisão.

## Continuação em 07/10/2026 — Modelo de dados, tópicos 42 a 119

Leitura interpretativa dos campos, nulabilidade, relações e exemplos SQL até `dados_macro_processo.md`, sem executar scripts. Total acumulado: 1.796 tópicos com texto integral da cópia local lido; modelo de dados: 119/239. Conferência de imagens e comparação com HTML atual continuam separadas.

- **Figura, atividade e fluxo:** FIGURA guarda posição, dimensões, tipo gráfico, referência à atividade/gateway e diagrama; Data Object referencia OPERACAO_ATIVIDADE. FLUXO_SEQUENCIA liga atividades por origem/destino e ACOP_ORIGEM distingue evento intermediário acoplado de atraso programado. Um desenho correto precisa representar a configuração operacional, não apenas aproximar uma figura BPMN. EXECUCAO_ATIVIDADE e EXECUCAO_GATEWAY registram instâncias/histórico; CANCELADO está relacionado ao comando Voltar, não automaticamente ao cancelamento de toda a OS.
- **Tempos de execução:** descrições de TEMPO_EXEC falam em complemento de dias; TEMPO_EXEC_DIAS menciona segundos. A unidade está inconsistente. TEMPO_ANO_REAL_SEG é explicitamente complemento em segundos do valor em minutos. Exigir validação antes de construir fórmulas e relatórios; não somar valores com unidades presumidas.
- **Versão e reclassificação:** DESENHO_PROCESSO e CLASSE_SUB_PROCESSO se relacionam a campos atuais e iniciais da OCORRENCIA. Relatórios devem escolher a versão/tipo atual ou inicial de acordo com a pergunta de negócio. Não equiparar ambos em reclassificações.
- **Chaves e herança:** ENUM_VARIAVEL depende do nome e método de priorização. GAP/ACAO_GAP/RISCO_GAP usam ocorrência e sequencial; ITEM_APROVACAO depende de assunto e versão. CONHECIMENTO, HARDWARE e FORNECEDOR herdam identidades de ITEM/EMPRESA, mas certas tabelas de ligação estão incompletas na documentação.
- **Erros de referências:** CLASSE_COMPONENTE.ID_CLASSE_CONFIGURACAO tem texto de Tipo de Serviço, mas referência a CLASSE_CONFIGURACAO. CONTRATO.ID_CONTRATANTE descreve Órgão e aponta EMPRESA. CONTROLE.ID_SUB_PROCESSO aponta SUB_PROCESSO apesar de texto Tipo de Subprocesso. INTER_SLA contém exemplo inválido terminado em `ORDEM_SERVICO.` e coluna de ligação vazia; preservar fonte e verificar chave no objeto/banco antes de propor SQL. FORNECEDOR também possui ligações vazias em dependentes.
- **Indicadores:** INDICADOR separa seleção, valor, agregação, provedor e filtros de situação/período. Fórmula de valor vazia assume contagem; percentual exige seleção. OS_FILTRO_FIN_SUC repete a descrição baseada em execução de mudança, que precisa ser conferida para processos gerais. INDICADOR_PLANO tem responsável, restrição, tolerância e desafio; mudança da meta atualiza apenas períodos com meta igual ao valor antigo. Sua descrição das cores presume maior é melhor e deve ser confrontada com SENTIDO_MELHOR.
- **Papéis:** GRUPO_PAPEL confirma prioridades crescentes e parada no primeiro agrupamento que retorna pessoas, inclusão de descendentes opcional e disponibilidade 24x7 quando calendário não definido/sem períodos. SOMENTE_MESMA_UND é ignorado se cliente sem localidade. Hierarquia de grupos não concede automaticamente todas as operações dos níveis inferiores.
- **Charge-back e rastreabilidade:** HIST_ITEM/HIST_COMP/HIST_PESSOA/HIST_ORGAO/HIST_USUARIO guardam situação na competência apurada. ITEM_CHARGE_BACK identifica origem e memória do lançamento. Custo de aquisição/manutenção e preço de charge-back são campos distintos. ITEM_COMPONENTE distingue proprietário ID_ITEM de componente ID_ITEM_COMPONENTE.
- **Aprovação/anexação:** CLASSE_APROVACAO.COPIAR_ANEXADO não tem efeito se copiar todos habilitado. ITEM_OCORRENCIA registra data, configuração geradora e relatório que produziu o arquivo; ITEM_APROVACAO vincula item a versão de assunto. Não confundir anexar à OS com submeter à aprovação.
- **Interrupções e execução:** EXEC_TIMER registra execução bem-sucedida do timer; EXECUCAO_ACAO registra ação de acordo, diferente de histórico de atividade. INTER_SLA registra início/fim previsto, aviso e tempo útil calculado ao finalizar interrupção; campos de envio/registro não comprovam entrega externa.
- **Tutorial visual (parcial):** conferidas figuras do Timer diário e mensal. O exemplo mensal mostra dia 15, 08:00, todos os meses habilitados e Último dia falso. Esses valores não estavam explicitados na extração textual. As demais imagens do tutorial ainda não estão todas conferidas.

As 3.229 páginas vinculadas pelo índice oficial foram arquivadas sem erros HTTP nesta rodada. O arquivamento automático das 2.341 URLs de imagens referenciadas ainda está em andamento; baixar não equivale a ler ou conferir visualmente.

### Modelo de dados — continuação até tópico 149/239

Total acumulado atualizado: 1.826/3.228 textos integrais. Próximo tópico: dados_[149] no catálogo.

- OCORRENCIA confirma ID_CORRENCIA_PRIN (grafia da fonte) como macrofluxo e ID_OCORR_PAI como chamada imediatamente superior; podem diferir em mais de dois níveis. Não confundir criação imutável DATA_HORA_CRIACAO, solicitação editável DATA_HORA_SOL, datas previstas, planejadas, reais e previsão original. NUMERO formatado pertence à base OCORRENCIA; ORDEM_SERVICO herda ID_OCORRENCIA.
- PAPEL_COMP contém divergência interna: introdução promete soma de todos os atores dos papéis, mas PRIORIDADE define parada no primeiro agrupamento que encontra pessoas. União geral não é assegurada quando as prioridades diferem. Deve ser validado em composição recursiva com atores e prioridades distintas. PAPEL_PROCESSO referencia versão e opcionalmente papel global; PAPEL_CLASSE_NEGOCIO é reutilizável por classe de negócio.
- OPERACAO_ATIVIDADE separa ATIVO, INICIA_AUTOMATICO e BLOQUEAR_PENDENCIA; desativar operação ignora sua validação. Quantidade mínima, reprovação imediata, pré-aprovação pela identidade do solicitante, reaproveitamento de aprovação anterior e cópia dos anexos são opções independentes.
- PASSAGEM_ITEM ocorre na criação da OS invocada, diferente de OUTPUT_SUB_PROC, que seleciona propriedade nativa ou customizada para saída. Não presumir sincronização posterior de anexos a partir da passagem inicial.
- PERIODO_PLANO reúne plano, indicador, mês e ano; VALOR_APURADO é descrito para provedor Lançamento Manual. As anotações de causa, perspectiva e providência são campos específicos, úteis ao RVA, com limite documentado de 500 caracteres. PLANO_GESTAO tem restrição de dados própria; mudanças de datas atualizam a coleção de períodos.
- METODO_PRIORIZACAO repete limite estritamente maior, enquanto GRAU_PRIORIDADE diz maior ou igual. Testar valor exatamente na fronteira. MENSAGEM_EVENTO.ID_PROCESSO é descrito incorretamente como Tipo de Serviço, mas ligação aponta PROCESSO.
- PERM_CONH_PAPEL novamente contém SQL incompleto `CONHECIMENTO.`; PESQUISA liga OS a ORDEM_SERVICO com coluna da base herdada omitida. Os exemplos inválidos precisam ser corrigidos a partir do modelo verificado, sem copiar cegamente.
- PESSOA distingue pessoa/fila/cliente, usuário de rede, usuário solucionador vinculado e login do portal. Substituição para aprovação usa instante de exibição da página, não criação da solicitação. O texto sobre senha é legado e não comprova funcionamento da futura instalação. Nenhum dado de credencial foi consultado.
- OPCAO_ATIVIDADE.INDISPONIBILIDADE influencia o relatório de disponibilidade/MTBF/MTTR; não é configuração automática de interrupção de ANS. NIVEL_SLA.VISIVEL_PAINEL_WS depende adicionalmente da regra do Grupo de Trabalho.

### Continuidade final desta rodada

Leitura textual integral: 1841/3.228; modelo de dados 164/239, próximo dados_[164]. Foram lidos também PREDIO, PRIOR_ENTIDADE, PROCESSO, questões/pesquisas, RECEPTOR, RECURSO_APLICADO, relatórios de atividade/operação e seus parâmetros, restrições de horários, anexos, aprovação e serviço. REL_ATIVIDADE e REL_OPERACAO têm finalidades distintas; parâmetros se ligam por relatório + atividade/operação, e permissão de modificar consta em REL_ATIVIDADE_PARAM. RECURSO_APLICADO.VALIDA_SALDO vazio/zero restringe consumo ao próprio mês; duração suficiente forma banco de horas. PROCESSO.ATIVO contém descrição copiada de Tipo de Serviço.

Conferidas visualmente as imagens oficiais iniciadortimer23_zoom80.jpg e iniciadortimer24_zoom80.jpg: job Máquina de Processos no Gerenciamento de Ambiente; OS gerada às 08:00 de 15/11/2012, responsabilidade Simone Santos, subprocesso versão 4, serviço Rotinas de RH, assunto automático com mês/ano. Estas imagens não provam funcionamento na futura instalação.

Arquivamento concluído: 3.229 páginas e 2.335 imagens. Seis imagens referenciadas retornaram HTTP 404, documentadas em LEIA-ME-ARQUIVO-OFICIAL.md. Validação local de existência e SHA-256 concluída; não confundir isso com comparação semântica integral.
