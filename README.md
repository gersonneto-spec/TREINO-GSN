# TREINO-GSN: Foco

Aplicativo web (PWA) para registrar o treino da academia por grupo muscular, em 3 toques por exercício. Substitui o Registro de Carga neste endereço. A versão anterior continua no histórico do repositório.

## O que faz

- **Hoje**: capa, 9 grupos musculares, treino do dia, semana contra a meta e missão da semana. Botão de repetir o último treino do grupo e alvo de carga e repetições por exercício.
- **Evolução**: treinos por semana, séries por grupo, curva por exercício (carga ou 1RM estimado) e recordes recentes.
- **Desafios**: metas da semana e do mês, sequência de semanas na meta e conquistas.
- **Corpo**: mapa de frente e de costas. Tocar no músculo mostra os melhores movimentos, e a cor acompanha as séries dos últimos 7 dias.
- **Técnicas**: 11 técnicas avançadas com passo a passo e exemplo, mais o treino rápido de 15, 25 ou 35 minutos.

## Onde os dados ficam

Nesta versão (GitHub Pages) tudo é gravado no localStorage do navegador, ou seja, **no aparelho em que você registrou**. Não há sincronização entre aparelhos. Em Ajustes existe o botão para copiar o histórico em CSV.

A versão principal é a publicada como Artifact no Claude, com banco sincronizado entre aparelhos. É ela que alimenta o resumo semanal de domingo.

## Instalar no celular

1. Abrir a página no Safari (iPhone) ou Chrome (Android).
2. Menu do navegador > **Adicionar à tela de início**.
3. O app abre em tela cheia e funciona sem internet, via service worker.

## Estrutura

    index.html              app inteiro em um único arquivo
    foco.jpg                imagem de capa
    manifest.webmanifest    metadados do PWA
    sw.js                   service worker (cache para uso sem rede)
    icon-180.png            ícone para iPhone
    icon-512.png            ícone do PWA

Sem dependências, sem build, sem framework. Os gráficos são SVG gerados no próprio arquivo.

## Cálculos

- **Marca de um registro**: fórmula de Epley, carga x (1 + reps / 30). Sem carga, vale o número de repetições.
- **Recorde**: registro que supera a melhor marca anterior do mesmo exercício.
- **Semana**: de segunda a domingo.
