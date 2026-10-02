# Checklist de publicação

## Antes de enviar ao GitHub

- [ ] O arquivo principal se chama `index.html`.
- [ ] `.nojekyll` está na raiz.
- [ ] O proprietário configurado é `otaviofelisberto0-creator`.
- [ ] O repositório configurado é `R_Conversao`.
- [ ] O repositório será público, permitindo consulta sem token no navegador.
- [ ] Não foram incluídos dados mensais diretamente na pasta do site.

## Para cada competência

- [ ] Existe um arquivo ND.
- [ ] Existe um arquivo BL.
- [ ] Os nomes contêm `ND` ou `BL` como token independente.
- [ ] A competência está em `AA-MM` ou `AAAA-MM`.
- [ ] A extensão é CSV, TXT, JSON ou GZIP compatível.
- [ ] O arquivo ND contém as colunas obrigatórias de ND.
- [ ] O arquivo BL contém as colunas obrigatórias de BL.
- [ ] Há registros da marca NET.
- [ ] Há indicadores Venda Bruta e Instalacao.
- [ ] O Release foi publicado e não ficou como rascunho.

## Depois de ativar o GitHub Pages

- [ ] O site abre sem tela em branco.
- [ ] A carga automática inicia.
- [ ] A mensagem final informa sucesso.
- [ ] A auditoria lista ND e BL em ordem de competência.
- [ ] Todas as competências esperadas aparecem.
- [ ] Duplicidades estão identificadas.
- [ ] O Mês x Mês apresenta as colunas em ordem cronológica.
- [ ] A análise ND funciona.
- [ ] A análise BL funciona.
- [ ] A Análise Diária funciona.
- [ ] Os rankings funcionam.
- [ ] A tabela de Dados da Conversão funciona.
- [ ] As exportações existentes funcionam.

## Teste da contingência manual

- [ ] Um CSV ND carrega somente no seletor ND.
- [ ] Um JSON BL carrega somente no seletor BL.
- [ ] Um GZIP válido é descompactado.
- [ ] Vários meses podem ser selecionados juntos.
- [ ] Limpar ND não remove BL.
- [ ] Limpar BL não remove ND.
- [ ] Um arquivo BL colocado no seletor ND gera orientação clara.
- [ ] Um arquivo de outro processo é rejeitado.

## Critério de liberação

A publicação está apta quando:

1. a auditoria automática encontra as competências esperadas de ND e BL;
2. as telas principais abrem sem erro;
3. o Mês x Mês está cronológico;
4. os dois testes de limpeza independente passam;
5. a contingência manual carrega pelo menos um arquivo válido de cada tipo.
