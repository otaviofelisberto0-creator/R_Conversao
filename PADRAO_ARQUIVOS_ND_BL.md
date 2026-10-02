# Padrão dos arquivos mensais ND e BL

## 1. Nomes reconhecidos

O tipo e a competência podem ser separados por hífen, espaço ou sublinhado.

Exemplos válidos:

```text
ND-26-01.json
ND 26 01.csv
ND_26_01.json.gz
Conversao-ND-2026-01.csv.gz
BL-26-01.json
BL 26 01.csv
BL_26_01.json.gz
Conversao_BL_2026_01.csv.gz
```

A competência deve aparecer como:

```text
AA-MM
AAAA-MM
```

Os mesmos separadores podem ser usados entre o ano e o mês.

## 2. Nomes rejeitados ou ignorados

```text
ND.json                    # sem competência
BL-final.csv               # sem competência
ND-BL-26-01.json           # tipo ambíguo
ND-26-13.json              # mês inválido
arquivo-26-01.pdf          # formato não suportado
```

Arquivos de outros processos não são incorporados às bases ND ou BL.

## 3. Formatos aceitos

```text
.csv
.txt
.json
.gz
.csv.gz
.txt.gz
.json.gz
```

No `.gz` sem extensão interna, o painel detecta JSON ou CSV depois da descompactação.

### CSV/TXT

Delimitadores reconhecidos:

- ponto e vírgula;
- vírgula;
- tabulação.

Codificações tratadas:

- UTF-8;
- Windows-1252 como contingência.

### JSON

Formato 1 — lista direta:

```json
[
  {
    "NR_ANO_MES": "202601",
    "DT": "2026-01-02",
    "DT_VENDA": "2026-01-01",
    "COD_MUNICIPIO": "4205407",
    "NM_INDICADOR_NEGOCIO": "Venda Bruta",
    "NM_MARCA": "NET",
    "NM_LINHA_NEGOCIO": "Residencial",
    "NM_PERFIL_CLIENTE": "Prospect",
    "QT": 10
  }
]
```

Formato 2 — objeto com `rows`:

```json
{
  "schema": 3,
  "type": "ND",
  "rows": [
    {
      "NR_ANO_MES": "202601",
      "DT": "2026-01-02",
      "DT_VENDA": "2026-01-01",
      "COD_MUNICIPIO": "4205407",
      "NM_INDICADOR_NEGOCIO": "Venda Bruta",
      "NM_MARCA": "NET",
      "NM_LINHA_NEGOCIO": "Residencial",
      "NM_PERFIL_CLIENTE": "Prospect",
      "QT": 10
    }
  ]
}
```

## 4. Colunas exigidas

### ND

```text
COD_MUNICIPIO
NM_INDICADOR_NEGOCIO
NM_MARCA
DT
DT_VENDA
QT
NM_PERFIL_CLIENTE
```

### BL

```text
COD_MUNICIPIO
NM_INDICADOR_NEGOCIO
NM_MARCA
DT
DT_VENDA
QT
```

### Recomendadas para ambos

```text
NR_ANO_MES
NM_LINHA_NEGOCIO
```

A competência é obtida primeiro de `NR_ANO_MES`; quando ela não estiver disponível, o painel tenta `DT` e depois `DT_VENDA`.

## 5. Valores esperados

Marca:

```text
NET
```

Indicadores usados nas conversões:

```text
Venda Bruta
Instalacao
```

Para ND, o painel utiliza os perfis previstos nas análises existentes, incluindo:

```text
Migracao - NET
Prospect
```

## 6. Arquivos brutos e compactos

Quando a coluna `NM_TIPO_ASS_DOMICILIO` existe, o painel mantém apenas:

```text
COM QUEBRA
SEM QUEBRA
```

No processo de redução para JSON, são preservadas as dimensões usadas pelas análises e a quantidade `QT` é agregada por combinação de dimensões.

## 7. Competência e Mês x Mês

Exemplos equivalentes de competência:

```text
NR_ANO_MES = 202601
NR_ANO_MES = 2601
nome = ND-26-01.json
nome = ND_2026_01.csv.gz
```

A apresentação do acompanhamento mensal usa `MM/AA`, mas a ordenação interna usa `AAAA-MM`, evitando ordem alfabética incorreta entre anos.

## 8. Recomendação operacional

Para reduzir ambiguidades, publique exatamente um arquivo ND e um arquivo BL por competência:

```text
ND-AA-MM.json
BL-AA-MM.json
```

JSON reduzido ou JSON GZIP tende a oferecer menor volume de transferência e leitura mais rápida que CSV bruto.
