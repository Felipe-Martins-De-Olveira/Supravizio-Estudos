# Toolbox, aprovação e scripts — 08/10/2026

Estudo baseado no CHM fornecido pelo usuário e na documentação local. Foram extraídas 3.295 páginas HTML do CHM; onze tópicos foram lidos integralmente, com conferência parcial de quatro imagens. Uma leitura adicional integral do Tutorial 8 sobre alteração de subprocesso foi realizada para conferir a fórmula de aprovação. A seção PossuiAprovacao do modelo de objetos Ocorrencia foi consultada pontualmente. Isso não é leitura integral do CHM.

## Elementos e desenho

- Iniciador manual: abertura pelo Portal ou Workspace, conforme configuração.
- Entrada de Dados: Data Object laranja ligado ao iniciador, tarefa ou finalizador; Campos para Preenchimento define os dados e sua obrigatoriedade.
- Aprovação: Data Object verde associado a uma tarefa. O papel responsável pela tarefa e os papéis de aprovadores são configurações distintas.
- Tarefa: atividade manual ou automática, com responsável configurado.
- Desvio exclusivo por dados: usa fórmula ou regra ligada à aprovação para escolher um caminho.
- Evento intermediário de mensagem: configura destinatário, modelo de comunicado e assunto.
- Finalizador normal e cancelamento têm efeitos diferentes. Reprovação não implica necessariamente cancelar toda a OS; depende da regra de negócio.

Os desenhos devem mostrar esses objetos associados, os responsáveis, os campos e as alternativas. Uma imagem de BPMN sem essas configurações não representa toda a implementação no Supravizio. Os campos propostos precisam ser validados pela área antes do cadastro.

## Configuração da aprovação

No Toolbox, clicar em Aprovação e depois na tarefa. Configurar:

1. Aprovadores: papéis que recuperam as pessoas da aprovação.
2. Campos para Aprovação: conteúdo da solicitação que será analisado.
3. Campos para Preenchimento: informações do parecer; a obrigatoriedade pode valer ao aprovar, reprovar, nas duas ações ou em nenhuma.
4. Iniciar automaticamente: inicia a solicitação de aprovação ao entrar na tarefa quando habilitado.
5. Mínimo aprovadores e Reprovar imediatamente: definir de acordo com a regra da área.

No comportamento padrão documentado, todas as pessoas indicadas precisam aprovar; uma reprovação encerra como reprovada. Não assumir que selecionar uma fila implica aprovação por um único integrante.

Campos aprovados ficam bloqueados, salvo configurações específicas ou cancelamento e nova versão da aprovação.

## Gateway após aprovação

Exemplo genérico de código da tarefa: APROVA_EXEMPLO.

Em Fórmula critério do desvio exclusivo:

```python
OrdemServico.PossuiAprovacao("APROVA_EXEMPLO")
```

Valores de comparação das alternativas:

| Caminho | Valor |
|---|---|
| Aprovada | True |
| Reprovada | False |

O argumento identifica o Código da tarefa que contém a aprovação, não a descrição do papel, da fila ou do gateway. O manual também permite selecionar a tarefa em Regra de Desvio.

PossuiAprovacao verifica se a aprovação vinculada à atividade foi finalizada como Aprovada. False isoladamente não prova reprovação: a aprovação pode estar pendente ou a atividade informada pode não corresponder à desejada. O fluxo deve aguardar a conclusão da aprovação antes de avaliar os dois caminhos.

## Avanço de tarefa automática

No Script Início de uma tarefa automática, o padrão documentado é:

```python
AvancaProximaAtividade = True
```

Esse comando solicita avanço da tarefa. Ele não substitui a fórmula do gateway e não deve ser aplicado indiscriminadamente na entrada de uma tarefa que precisa aguardar aprovação. A presença de pendências, regras da operação e contexto do script precisam ser conferidos.

## Scripts de formulário

Exemplo genérico em uma única linha, conforme o padrão de edição solicitado pelo usuário:

```python
Formulario["LABEL10"].Valor = '<div style="text-align:center;padding:24px 16px;font-family:Arial,sans-serif;"><div style="font-size:20px;line-height:1.6;">Mensagem informativa do formulário.</div><div style="margin-top:14px;font-size:18px;">Consulte as orientações disponíveis.</div></div>'
```

A renderização HTML/CSS deve ser conferida no controle e na interface usados. O exemplo não garante que todas as versões de Label aceitem qualquer estilo. A orientação de manter a atribuição em uma linha é um requisito observado nesta conversa, não uma afirmação universal sobre o interpretador IronPython.

## Teste do cliente no Linux

Wine 10.0, Winetricks e .NET Framework 4.0 foram instalados em um prefixo separado. O executável do cliente foi iniciado; o usuário mostrou uma mensagem “Object reference not set to an instance of an object”. A causa não foi determinada. Isso não comprova falha de rede nem compatibilidade funcional do cliente.

Nenhum login, importação de fluxos ou teste de execução dos scripts da empresa foi realizado. O teste de inicialização é separado da validação funcional no produto.

## Fontes e limites

Tópicos consultados no CHM: Toolbox; Data Objects; Aprovação; Genérico; Tarefas; Eventos Intermediários; Eventos Finalizadores; Desvios; Desvio Exclusivo; Entrada de Dados; Tutorial 6/Desenho do fluxo; Tutorial 8/Modificar o Subprocesso. Consulta pontual: modelo de objetos Ocorrencia/PossuiAprovacao.

[Manual oficial](https://help.supravizio.com/Supravizio.htm). O CHM não comprova correspondência com a versão instalada na empresa. Arquivo completo, código interno, configurações de conexão e imagens empresariais permanecem locais.
