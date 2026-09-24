# Salvando a Eleição Norte-Americana de 1936 com Data Science

## Contextualização

Em 1936, a revista *Literary Digest* conduziu uma das maiores pesquisas eleitorais já realizadas até então, prevendo a vitória do candidato Alf Landon sobre Franklin D. Roosevelt. O resultado real das eleições, no entanto, foi amplamente favorável a Roosevelt, expondo um dos casos mais estudados de viés de amostragem na história da estatística. A falha da *Literary Digest* é atribuída principalmente à forma como a amostra foi coletada — a partir de listas telefônicas, registros de automóveis e assinantes da revista — o que excluiu parte relevante do eleitorado da época e gerou distorções na representatividade da pesquisa.

Projeto acadêmico desenvolvido para o **Summit UMC**.

## Objetivo

Investigar as diferenças entre a pesquisa e o resultado real de 1936, testar uma correção com dados de 1932 e apresentar os resultados em um notebook, um resumo acadêmico e um pôster científico.

## Equipe e responsabilidades

| Integrante | Membro | Responsabilidade |
|---|---|---|
| Nelson Braga | A | Fase 1 — limpeza, preparação dos dados e análise exploratória |
| Maria Fernanda | B | Fase 2 — regressão linear, avaliação dos erros, tabelas, gráficos e conclusão da modelagem |
| Mário Marcos | C | Fase 3 — resumo acadêmico |
| Gabriel Figueiredo | D | Fase 4 — pôster científico |

## Organização do repositório

| Pasta | Conteúdo |
|---|---|
| [Fase 1 - Limpeza/](Fase%201%20-%20Limpeza/) | Notebook da Fase 1, planilha original e bases tratadas |
| [Fase 2 - Modelagem/](Fase%202%20-%20Modelagem/) | Notebook da Fase 2, tabelas de resultados e gráficos |
| [specs/](specs/) | Material de apoio da atividade |

Nas Fases 1 e 2, os dados ficam em `data/`, os notebooks em `notebooks/` e os gráficos exportados em `figures/`. 

## Notebooks e dados

1. [Fase 1 — Preparação e EDA](Fase%201%20-%20Limpeza/notebooks/01_fase1_preparacao_eda.ipynb): organiza a planilha original, calcula proporções e analisa a composição dos respondentes.
2. [Fase 2 — Modelagem e avaliação](Fase%202%20-%20Modelagem/notebooks/02_fase2_modelagem.ipynb): utiliza a base preparada na Fase 1 e os dados de 1932 para testar a regressão linear.

Os notebooks devem ser executados no **Google Colab**, na ordem das fases e das células. A Fase 1 usa caminhos relativos à pasta `notebooks/`: a planilha deve estar em `../data/raw/LitDigestFull.xlsx`, e a pasta `../data/processed/` deve existir no ambiente. Na Fase 2, envie `analysis_1936.csv` e `LitDigestFull.xlsx` quando o notebook solicitar.

A planilha original está em [Fase 1 - Limpeza/data/raw/](Fase%201%20-%20Limpeza/data/raw/). As bases preparadas estão em [Fase 1 - Limpeza/data/processed/](Fase%201%20-%20Limpeza/data/processed/).

## Resultados da Fase 2

Treinamos uma regressão linear com a pesquisa e o resultado real de 1932. Depois, aplicamos a relação aprendida à pesquisa de 1936. A avaliação considera os mesmos 48 estados, com peso igual para cada estado e proporções entre os dois principais candidatos.

| Previsão | MAE (p.p.) | RMSE (p.p.) |
|---|---:|---:|
| Pesquisa original | 18,62 | 20,06 |
| Regressão com 1932 | 16,62 | 18,04 |

A correção reduziu o MAE em 10,76% e o RMSE em 10,03%. Mesmo assim, continuou prevendo a vitória de Landon, com 362 votos eleitorais, contra 169 de Roosevelt. No resultado real, Roosevelt recebeu 523 votos eleitorais e Landon recebeu 8.

O treinamento com uma única eleição e a transferência dessa relação para 1936 são limitações do método. Os resultados reais de 1936 foram usados na avaliação, depois do treinamento.

As [tabelas completas](Fase%202%20-%20Modelagem/data/processed/) e os [gráficos](Fase%202%20-%20Modelagem/figures/) estão na pasta da Fase 2.

## Tecnologias

Python, Pandas, NumPy, Matplotlib, Scikit-Learn, Google Colab e GitHub.

## Entregáveis

- Fase 1: notebook e bases preparadas disponíveis no repositório.
- Fase 2: notebook, quatro tabelas CSV e dois gráficos PNG disponíveis no repositório.
- Fase 3: resumo acadêmico, com versão final a ser adicionada ao repositório.
- Fase 4: pôster científico, com versão final a ser adicionada ao repositório.

## Material de apoio

- [Guia técnico da Fase 2](specs/Fase2_Guia_Tecnico.pdf).
- ALENCAR, Airlane P. **Não resposta**. São Paulo: IME-USP, 2023. [Material de aula](https://www.ime.usp.br/~lane/home/MAE0315/Nonresponse.pdf). Acesso em: 17 set. 2026.
