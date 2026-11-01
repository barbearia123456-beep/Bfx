# Forex Robô (PWA)
App web instalável pelo Chrome: gráfico limpo (M1 M3 M5 M15 M30 H1 H4 D1), 29 pares (28 de Forex + XAUUSD), 20 estratégias (tendência, martingale, scalping, grade, reversão, rompimento, candles), operação manual ou automática, backtest de 2025, simulador, conta demo e conta real. Funciona offline (visual e backtests já baixados).

## Publicar no GitHub e instalar no Chrome
1. Crie um repositório no GitHub e envie **todos os arquivos desta pasta** (incluindo `.nojekyll` e `.github/`).
2. Em *Settings → Pages → Build and deployment*, escolha **GitHub Actions**. Após o push, o endereço será `https://SEU_USUARIO.github.io/NOME_DO_REPO/`.
3. Abra o endereço no Chrome do Android → menu ⋮ → **Instalar app** (ou botão "Instalar app" em *Contas*).

## Conectar a corretora (Exness, XM, IC Markets, etc.)
Um navegador não consegue falar o protocolo do MT5. O app usa o serviço **MetaApi** (nuvem de terceiros; tem plano gratuito limitado).
1. Crie conta em app.metaapi.cloud e gere um **token**.
2. Em *Contas*: escolha corretora, informe **servidor** (nome exato do seu MT5), **login** e **senha de trading**, cole o token → *Conectar conta*. A senha vai ao MetaApi para criar o terminal e **não é salva** no app.
3. *Modo*: Simulador (virtual) → Demo → Real (exige digitar REAL). O app recusa operar se o modo não bater com o tipo da conta.
O token fica salvo só no aparelho. Nunca use senha de investidor para operar nem compartilhe o token.

## Limitações — leia
- **Não há dados de 2025 dentro do app** (não é possível inventá-los). O backtest baixa os candles reais de 2025 da *sua* conta MetaApi e guarda no aparelho. Use H1 ou M15; M1/M5 exigem centenas de requisições por par.
- **Nunca testado contra MetaApi/MT5 reais nem em aparelho.** Testes feitos: motor (52 verificações com dados sintéticos), contabilidade, SL/TP, spread, martingale, ausência de lookahead.
- **Background:** um app web **não roda com o app fechado**. A automação funciona com o app aberto e tela ligada (Wake Lock). Os SL/TP de cada ordem ficam na corretora. Rodar fechado exige um APK Android com serviço em primeiro plano (não incluído nesta pasta).
- O backtest usa um posição por vez, entrada na abertura da vela seguinte, spread fixo, sem swap/comissão. Em cruzamentos o valor em US$ é aproximado.
- Estratégias não garantem lucro; martingale pode zerar a conta. Teste em demo.
