# Monitor externo do NewsBase

Este repositório só vigia o site https://newsbase.site **de fora**: se ele sair do ar, ou se a coleta de notícias ou o vigia interno pararem,
a execução fica vermelha e o GitHub avisa o dono por e-mail (e pelo app do GitHub no celular).

- A cada 10 minutos o GitHub roda `.github/workflows/monitor.yml`.
- Confere as páginas `/boas-vindas`, `/entrar` e `/premium` (têm de responder 200) e `/api/saude` (`ok` e `vigiaEmDia` verdadeiros).
- Uma vez por semana grava um carimbo de data no arquivo `ultima-verificacao.txt`: o GitHub desliga agendamentos de repositórios sem atividade
  por 60 dias, e esse carimbo evita isso.
- Não guarda segredo nenhum: só consulta endereços públicos.
