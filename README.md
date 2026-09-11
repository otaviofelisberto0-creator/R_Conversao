# Dashboard Conversao

Pacote pronto para publicacao no GitHub Pages.

## Estrutura

- `index.html`: dashboard completo
- `.nojekyll`: compatibilidade com GitHub Pages
- `dados/manifest.json`: lista dos JSONs publicados
- `dados/ND-AA-MM.json`: base mensal gerada na pagina Upload

## Publicacao

Envie o conteudo deste pacote para a raiz do repositorio e habilite o GitHub Pages para a branch publicada.

## Atualizacao da base

Na pagina Upload, carregue o CSV, converta para JSON e substitua na pasta `dados` o JSON mensal e o `manifest.json` gerados.
