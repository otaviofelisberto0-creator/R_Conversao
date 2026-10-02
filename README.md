# Dashboard Conversão ND e BL

Pacote pronto para publicação no GitHub Pages.

## Início rápido

1. Mantenha `index.html` e `.nojekyll` na raiz do repositório.
2. Publique a branch `main` pelo GitHub Pages.
3. Crie Releases e anexe os arquivos mensais ND e BL.
4. Use nomes com tipo e competência, por exemplo `ND-26-01.json` e `BL-26-01.json`.
5. Abra o site publicado e confira a auditoria dos arquivos encontrados.

Leia antes da publicação:

- `GUIA_CONFIGURACAO_GITHUB.md`: configuração completa do repositório, Pages e Releases.
- `PADRAO_ARQUIVOS_ND_BL.md`: nomes, formatos e estrutura esperada dos dados.
- `CHECKLIST_PUBLICACAO.md`: verificação operacional antes e depois da entrada em produção.
- `SHA256SUMS.txt`: integridade dos arquivos do pacote.

## Estrutura do pacote

```text
conversao-nd-bl-github/
├── index.html
├── .nojekyll
├── README.md
├── GUIA_CONFIGURACAO_GITHUB.md
├── PADRAO_ARQUIVOS_ND_BL.md
├── CHECKLIST_PUBLICACAO.md
└── SHA256SUMS.txt
```

O `index.html` contém HTML, CSS, JavaScript e tabela de critérios no próprio arquivo. Não há bibliotecas externas, etapa de build ou arquivos de execução adicionais.

## Fonte de dados

A fonte automática oficial é a API de GitHub Releases configurada no `index.html`:

```text
https://api.github.com/repos/otaviofelisberto0-creator/R_Conversao/releases
```

A carga manual de ND e BL permanece disponível separadamente, apenas para contingência.
