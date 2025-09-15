# Previsão do IBOVESPA (D+1) com Machine Learning

Este projeto foi desenvolvido como parte do challenge técnico para a FASE 2 da FIAP, curso de Data Analytics.  
O objetivo foi construir um pipeline completo para prever se o IBOVESPA vai fechar em alta ou baixa no **próximo pregão (D+1)**.

---

## Contexto

Prever movimentos de curtíssimo prazo na bolsa é uma tarefa altamente desafiadora. O mercado é volátil, sujeito a notícias e eventos inesperados, e os modelos acabam tendo que extrair padrões de muito ruído.  

O foco aqui não foi “acertar sempre”, mas sim **testar diferentes estratégias de modelagem** e entender quais sinais realmente trazem valor preditivo.

---

## Estrutura do Projeto

postech-challenge2/
├── notebooks/
│ ├── 00_get_data.ipynb # Aquisição dos dados (Yahoo Finance)
│ ├── 01_eda_ibov.ipynb # Limpeza, consistência e exploração inicial
│ ├── 02_target_features.ipynb # Criação do target e engenharia de atributos
│ ├── 03_modelagem_baseline.ipynb # Baselines: Regressão Logística e Árvore
│ ├── 04_modelagem_avancada.ipynb # Avançados: Random Forest e Gradient Boosting
│ └── 05_experimento_extra.ipynb # Testes com XGBoost + indicadores técnicos (RSI, Bollinger, EMAs)
├── reports/ # Gráficos de matrizes de confusão e importâncias
├── requirements.txt
├── .gitignore
└── README.md

Os diretórios `data/` e `models/` não aparecem aqui porque estão ignorados no versionamento (veja `.gitignore`).

---

## Como rodar

1. Clone este repositório:
   ```bash
   git clone https://github.com/MarianaRuther/postech-challenge2-ibov.git
   cd postech-challenge2-ibov

2. Instale as dependências:

pip install -r requirements.txt

3. Execute os notebooks na ordem:

00_get_data.ipynb → baixa dados históricos do IBOVESPA.
01_eda_ibov.ipynb → faz limpeza, consistência e EDA.
02_target_features.ipynb → cria o target e as features.
03_modelagem_baseline.ipynb → roda os modelos simples (logística e árvore).
04_modelagem_avancada.ipynb → testa ensembles (Random Forest, Gradient Boosting).
05_experimento_extra.ipynb → adiciona indicadores técnicos e roda XGBoost.

---

## Conclusões

* Previsão de curtíssimo prazo é altamente ruídosa, mas conseguimos extrair sinais consistentes.
* O modelo mais confiável foi o Random Forest (63%).
* Momentum e lags curtos são os fatores que mais pesam no resultado.
* Estratégias futuras podem usar horizontes maiores (D+3, D+5) e variáveis externas (dólar, juros, commodities).