# TREINO-GSN — Registro de Carga

Aplicativo web (PWA) para registrar séries e acompanhar a evolução de treino exercício por exercício, montado sobre o plano de 8 sessões: mobilidade diária e Treinos 1 a 7.

## O que faz

- **Treino** — abre no treino do dia da semana. Cada exercício traz a prescrição original (FD, TS, BO, WS, cluster, drop, cadência 1:3, reps na reserva), campos de carga, repetições, RIR e técnica, 1RM estimado calculado em tempo real, marcação de recorde, comparação com a última sessão, botão de repetir a última sessão e cronômetro de descanso que dispara sozinho com o intervalo previsto para aquele exercício.
- **Evolução** — por exercício: curva de 1RM estimado (fórmula de Epley), tonelagem por sessão e o registro sessão a sessão em tabela.
- **Volume** — séries válidas por grupo muscular na semana contra a meta (editável) e tonelagem semana a semana. Aquecimento, preparo, alongamento e cardio ficam fora da contagem.
- **Histórico** — sessões finalizadas, com exportação e importação de backup em JSON.
- **Plano** — o plano completo com a legenda do protocolo.

## Onde os dados ficam

Nesta versão (GitHub Pages) tudo é gravado no localStorage do navegador, ou seja **no aparelho em que você registrou**. Não há sincronização entre celular e computador.

Para levar o histórico de um aparelho para outro: aba **Histórico > Exportar backup (.json)** no aparelho de origem, **Importar backup** no de destino. A importação não duplica sessões já existentes.

Existe também uma versão publicada como Artifact no Claude, essa sim com banco sincronizado entre aparelhos.

## Instalar no celular

1. Abrir a página no Chrome (Android) ou Safari (iPhone).
2. Menu do navegador > **Adicionar à tela de início**.
3. O app abre em tela cheia e funciona sem internet, via service worker.

## Estrutura

    index.html              app inteiro: plano, cálculo, gráficos e interface, em um único arquivo
    manifest.webmanifest    metadados do PWA
    sw.js                   service worker (cache para uso sem rede)
    icon.svg                ícone (os PNG do PWA vão embutidos no manifest)

Sem dependências, sem build, sem framework. Os gráficos são SVG gerados no próprio arquivo.

## Cálculos

- **1RM estimado**: fórmula de Epley, carga x (1 + reps / 30), aplicada à melhor série de cada sessão.
- **Série válida**: exercício de carga, com repetições registradas e técnica diferente de aquecimento (WU).
- **Tonelagem**: soma de carga x repetições das séries válidas.
- **Semana**: de segunda a domingo.
