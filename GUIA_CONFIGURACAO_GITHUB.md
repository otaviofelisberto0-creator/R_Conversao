# Guia de configuração do GitHub

## 1. Configuração prevista no painel

O arquivo entregue está configurado para:

```text
Proprietário: otaviofelisberto0-creator
Repositório: R_Conversao
Branch de publicação recomendada: main
Pasta de publicação: raiz do repositório
```

Endpoint usado pelo painel:

```text
https://api.github.com/repos/otaviofelisberto0-creator/R_Conversao/releases
```

Se esses nomes forem mantidos, não é necessário alterar o código.

## 2. Criar ou preparar o repositório

1. Entre na conta `otaviofelisberto0-creator` no GitHub.
2. Crie o repositório público `R_Conversao`, caso ele ainda não exista.
3. Use a branch `main`.
4. Extraia o pacote ZIP.
5. Envie para a raiz do repositório:
   - `index.html`;
   - `.nojekyll`;
   - os arquivos Markdown do pacote, se desejar mantê-los junto do projeto.
6. Confirme que o arquivo principal se chama exatamente `index.html`.

Não coloque os arquivos mensais na pasta do site. Eles devem ser anexados aos GitHub Releases.

## 3. Ativar o GitHub Pages

1. Abra o repositório.
2. Acesse **Settings > Pages**.
3. Em **Build and deployment**, escolha **Deploy from a branch**.
4. Selecione a branch `main`.
5. Selecione a pasta `/(root)`.
6. Salve.
7. Aguarde o GitHub informar que o site foi publicado.

Endereço esperado:

```text
https://otaviofelisberto0-creator.github.io/R_Conversao/
```

## 4. Criar o primeiro Release de dados

1. Abra **Releases** no repositório.
2. Clique em **Draft a new release**.
3. Crie uma tag, por exemplo `dados-26-01`.
4. Use um título descritivo, como `Conversão ND e BL — 26-01`.
5. Anexe os arquivos mensais, preferencialmente:

```text
ND-26-01.json
BL-26-01.json
```

6. Publique o Release. Releases deixados como rascunho não são usados pelo painel.

ND e BL podem estar no mesmo Release ou em Releases diferentes. O painel percorre todas as páginas da API, reúne todos os Releases publicados e seleciona os assets mensais válidos.

## 5. Publicar novas competências

Para cada mês:

1. gere o arquivo ND;
2. gere o arquivo BL;
3. confira o padrão de nomes e colunas;
4. crie um novo Release ou atualize um Release ainda não publicado;
5. anexe os dois arquivos;
6. publique;
7. abra o painel e confira a seção **Auditoria dos arquivos localizados**.

Padrão recomendado:

```text
ND-AA-MM.json
BL-AA-MM.json
```

Exemplo para setembro de 2026:

```text
ND-26-09.json
BL-26-09.json
```

## 6. Substituição de um mês

Quando for necessário corrigir uma competência já publicada:

1. prefira publicar o arquivo corrigido em um Release mais recente;
2. mantenha o mesmo tipo e a mesma competência no nome;
3. abra o painel;
4. confira na auditoria qual arquivo foi selecionado;
5. remova a versão antiga quando o processo interno permitir.

Para a mesma competência, o painel prefere o asset do Release mais recente. Persistindo empate, usa a preferência de formato definida no código.

## 7. Alterar proprietário ou repositório

Se o projeto mudar de endereço, procure no `index.html` por:

```javascript
const githubReleaseConfig = {
  owner: "otaviofelisberto0-creator",
  repo: "R_Conversao",
  api: "https://api.github.com/repos/otaviofelisberto0-creator/R_Conversao/releases"
};
```

Atualize os três valores de forma consistente. Também atualize o link **Ver releases**, procurando por:

```text
https://github.com/otaviofelisberto0-creator/R_Conversao/releases
```

## 8. Validação após a publicação

1. Abra o endereço do GitHub Pages.
2. Confirme que a carga automática começa.
3. Aguarde a mensagem **Carga concluída**.
4. Abra **Auditoria dos arquivos localizados**.
5. Verifique:
   - páginas da API consultadas;
   - quantidade de Releases considerados;
   - competências encontradas para ND;
   - competências encontradas para BL;
   - duplicidades descartadas;
   - eventual mês sem contraparte ND ou BL.
6. Abra **Acompanhamento Mês x Mês**.
7. Alterne entre ND e BL.
8. Confira Conversão, Análise Diária, rankings e Dados da Conversão.

## 9. Contingência manual

Se a consulta automática estiver indisponível:

- use **Arquivos ND** somente para ND;
- use **Arquivos BL** somente para BL;
- selecione um ou vários meses de cada tipo;
- use CSV, JSON ou GZIP;
- limpe cada base pelo seu próprio botão.

A carga manual não substitui a organização dos Releases; ela serve apenas para continuidade temporária da análise.

## 10. Diagnóstico de erros

### HTTP 403

Possíveis causas:

- limite temporário da API pública;
- política de rede do ambiente;
- repositório sem acesso público.

Aguarde o horário indicado na mensagem ou use a contingência manual.

### Nenhum Release publicado

Confirme que existe pelo menos um Release publicado e que ele não está como rascunho.

### Nenhum arquivo ND ou BL encontrado

Confirme que cada nome contém:

- `ND` ou `BL` como token independente;
- competência `AA-MM` ou `AAAA-MM`;
- extensão CSV, TXT, JSON ou GZIP compatível.

### Arquivo inválido

Consulte `PADRAO_ARQUIVOS_ND_BL.md` e verifique colunas, datas, indicadores, marca e conteúdo compactado.
