# Idade da conta no GitHub e especificações em Spec-Driven Development

Pacote de replicação do artigo sobre a relação entre a idade da conta no GitHub
e características das especificações escritas com Spec-Driven Development (SDD),
usando o dataset SpecMine v1.0 (snapshot de julho de 2026), desafio de mineração
do MSR 2027.

## Conteúdo

| Pasta | Arquivo | O que é |
|---|---|---|
| `notebooks/` | `01_idade_contas.ipynb` | Coleta a data de criação das contas pela API do GitHub e calcula a idade da conta no primeiro uso de SDD |
| `notebooks/` | `04_dimensoes_x_idade.ipynb` | Calcula as medidas por especificação, agrega por autor e roda as correlações de Spearman (IC por bootstrap, correção de Holm, correlação parcial) |
| `data/` | `account_created.csv` | Data de criação da conta por identificador numérico do autor (`author_id`) |
| `data/` | `autores_idade_v2.csv` | Primeiro uso de SDD, data de criação e idade da conta (anos) por autor |
| `data/` | `resultados_dimensoes.csv` | Resultados estatísticos por ferramenta e medida |
| `figures/` | `fig_resultados.pdf/.png` | Figura dos resultados do artigo |
| `figures/` | `dist_idade_contas.png` | Distribuição da idade das contas |

Os dados derivados identificam os autores apenas pelo identificador numérico
usado no SpecMine; não há logins, nomes ou e-mails. O SpecMine não é
redistribuído aqui: os notebooks leem as tabelas diretamente do Hugging Face
(`ShyAgarwal/specmine`).

## Como reproduzir

1. Abra os notebooks no Google Colab (Arquivo → Fazer upload de notebook).
2. Coloque as pastas `data/` e `notebooks/` em uma pasta do seu Google Drive e
   ajuste a variável `BASE` na primeira célula de código para esse caminho.
3. Notebook 01: crie o segredo `GITHUB_TOKEN` no Colab (ícone de chave na barra
   lateral) com um token pessoal do GitHub sem permissões extras. Rode as
   células em ordem. Para pular a coleta, use o `account_created.csv` já incluído.
4. Notebook 04: rode as células em ordem; não precisa de token. Os resultados
   são salvos em `data/resultados_dimensoes.csv` e a figura em `data/`.

Ambiente: Colab com CPU padrão (sem GPU nem RAM alta), Python 3, pandas, numpy,
scipy e matplotlib. Semente do bootstrap: 42 (1.000 reamostras).

## Fonte dos dados

SpecMine v1.0 (julho de 2026), distribuído sob licença CC BY 4.0.
Datas de criação das contas obtidas pela API pública do GitHub.
