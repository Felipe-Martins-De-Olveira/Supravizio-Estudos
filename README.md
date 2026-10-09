# Estudos de Supravizio

Atualização em 09/10/2026. Este repositório reúne relatórios de aprendizado e progresso. Os relatórios não incluem XMLs, scripts internos ou credenciais; as transcrições agora têm cópias com omissões sinalizadas. Os materiais completos permanecem no computador.

## Manual

- [Estudo do manual](estudo-manual/ESTUDO-MANUAL-SUPRAVIZIO.md).
- [Revisão detalhada](estudo-manual/REVISAO-DETALHADA.md): 1.841 de 3.228 textos com leitura integral registrada; revisão dos demais textos e imagens ainda parcial.
- [Pontos de conferência](estudo-manual/PONTOS-DE-CONFERENCIA.md).

## XMLs e scripts

Estudo estrutural de 104 XMLs: 98 exportações distintas e 113 subprocessos. Foram encontrados 1.447 scripts e expressões distintos, todos submetidos à checagem estática automatizada. A leitura direta registrada abrange 983 corpos executáveis; 464 ainda não têm leitura literal integral registrada, embora tenham perfis estruturados revisados. A rodada aprofundada examinou perfis de 319 unidades distintas de função/classe e identificou 69 nomes de bibliotecas em 109 variantes. Foram registradas 32 observações conferidas nesta rodada; não representam falhas comprovadas em produção e podem se sobrepor aos achados históricos.

- [Conhecimento aprofundado de scripts](estudo-xml/scripts/CONHECIMENTO-SCRIPTS.md).
- [Imports, DGCO, Excel e CSV](estudo-xml/scripts/EXEMPLOS-DGCO-EXCEL-IMPORTS.md).
- [Cobertura da revisão aprofundada](estudo-xml/scripts/COBERTURA.json).
- [Revisão interpretativa histórica e cenários de teste](estudo-xml/REVISAO-INTERPRETATIVA-SCRIPTS.md).
- [Progresso agregado](estudo-xml/PROGRESSO-REVISAO-INTERPRETATIVA.json).

Nenhum script da empresa foi executado no Supravizio. Houve teste de inicialização do cliente pelo Wine, com erro de referência nula; acesso funcional ao ambiente não foi confirmado. O áudio de seis aulas foi transcrito localmente (aproximadamente 23h31min); imagens foram revistas por amostragem.

[Manual oficial](https://help.supravizio.com/Supravizio.htm).

## Toolbox, CHM e exemplos de scripts

- [Estudo do Toolbox, aprovação e scripts](estudo-chm/TOOLBOX-APROVACAO-SCRIPTS.md).
- [Progresso do CHM](estudo-chm/PROGRESSO.json): 12 tópicos lidos integralmente e uma consulta pontual em 3.295 páginas extraídas.

Inclui a fórmula de aprovação para o gateway, o comando de avanço automático da tarefa e a distinção entre aprovação pendente e reprovação.

## Transcrições das seis aulas

[Consultar as aulas em TXT e SRT](estudo-materiais/transcricoes/README.md). As cópias publicadas mantêm os tempos, substituem nomes de participantes e sinalizam trechos omitidos sobre autenticação, identificadores e referências de acesso. Transcrições automáticas podem conter erros; os originais completos permanecem locais.

## Revisões detalhadas e orientação para outra IA

- [Revisões das seis aulas](estudo-aulas/revisao-2026-10-08/README.md): conteúdo transcrito revisado até encerramento, com 138 quadros conferidos por amostragem.
- [Prompt completo para ensinar outra IA a auxiliar no aplicativo](PROMPT-PARA-IA-SUPRAVIZIO.md): ordem de estudo, desenho nativo, formulários, scripts, validação e operação autorizada.

Os exemplos de código acrescentados são didáticos. As notas publicadas generalizam nomes e referências específicas; nenhuma execução no software empresarial foi validada nesta rodada.
