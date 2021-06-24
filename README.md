# Análise do Consumo de Energia da Indústria na Região Sudeste do Brasil

[<img src="https://img.shields.io/badge/author-Carolina%20Dias-FB3799?style=flat-square"/>](https://github.com/diascarolina) [<img src="https://img.shields.io/badge/carodias-0A66C2?style=flat-square&logo=linkedin&logoColor=white" />](https://www.linkedin.com/in/carodias/) [![Made withJupyter](https://img.shields.io/badge/Made%20with-Jupyter-orange?style=flat-square&logo=Jupyter)](https://jupyter.org/try) [![GitHub license](https://img.shields.io/github/license/Naereen/StrapDown.js.svg?style=flat-square)](https://github.com/diascarolina/healthcare-analysis/blob/main/LICENSE)

![](https://github.com/diascarolina/project-energy-consumption-in-brazil/blob/main/docs/banner.png?raw=true)

# Sumário

# Introdução do Problema

Reduzir custos e aumentar os lucros é um dos pilares da maioria das empresas existentes. No setor de energia elétrica, isso não seria diferente. Grandes indústrias do ramo de eletricidade buscam otimizar seus processos para a diminuição de desperdícios na produção.

É nesse contexto que se mostra relevante termos métodos e técnicas capazes de modelar com cada vez mais precisão o consumo de energia elétrica de diversos setores, como indústria, comércio e residencial, para que os processos de produção de energia se adequem às previsões e evitem gastos além do necessário e também o desperdício. [[1]](https://blog.bcntreinamentos.com.br/gestao-de-energia/amp/)

Estima-se que _"entre 2014 e 2016, o Brasil desperdiçou o equivalente a 1,4 vez a produção anual da usina hidrelétrica de Itaipu. É como se o país tivesse desprezado R$ 61,7 bilhões, já que essa energia não foi utilizada de forma produtiva."_ [Fonte: Indústria 4.0 pode mudar o cenário do consumo de energia no Brasil](https://valor.globo.com/google/amp/patrocinado/weg/weg/noticia/2019/08/05/industria-4-0-pode-mudar-o-cenario-do-consumo-de-energia-no-brasil.ghtml)

Com isso em mente, fica evidente que é necessário cada vez mais desenvolvermos novas técnicas para cessar esse desperdício não só monetário, mas até mesmo do próprio meio ambiente.

Com essa problematização, temos a tarefa de realizar exatamente isso: construir um modelo de aprendizagem de máquina para prever o futuro consumo de energia elétrica para que a oferta seja ajustada de acordo com a demanda. No caso do atual projeto, queremos **prever o consumo de energia elétrica da indústria na região sudeste do Brasil**.

### 🟢 O notebook com o projeto pode ser encontrado [aqui](https://github.com/diascarolina/project-energy-consumption-in-brazil/blob/main/notebooks/projeto_consumo_de_energia.ipynb).

### 🟢 Um relatório em PDF com as principais conclusões e resolução das questões encontra-se [aqui]().

# Dados

Os dados fornecidos contém informações sobre o consumo de energia nas 5 regiões do Brasil, além de diversas outras informações relevantes, como informações socioeconômicas e de produção comercial/industrial.

Os dados originais podem ser encontrados [aqui](https://github.com/diascarolina/project-energy-consumption-in-brazil/blob/main/data/Bases_Final_ADS_Jun2021.xlsx).

Como a região que estávamos analisando é a sudeste, durante o projeto separei as variáveis relevantes à tal região, para termos um menor número de features.

Os dados também passaram pela seguinte divisão:

- **Dados de treino:** vão desde o início do dataset, em janeiro de 2004 até Dezembro de 2017;
- **Dados de teste:** Janeiro de 2018 a Fevereiro de 2021;
- **Dados para a previsão:** Março de 2021 a dezembro de 2022.

# Metodologia

O projeto se inicia com uma análise das variáveis que tem relação direta com a região sudeste. Foi analisada a série temporal de cada uma e a correlação entre variáveis relevantes entre si.

Após essa parte de análise, me foquei em realizar teste com alguns modelos de Machine Learning. A maioria dos modelos utilizados foram escolhidos por terem um foco em séries temporais, que é o que estamos analisando e que queremos prever. Além disso, foram buscados também modelos que pudessem realizar previsões em séries temporais multivariadas, que contém mais de uma variável temporal.

### Modelo 00: Dummy Model

Modelo de previsão ingênua, utilizado como base para a avaliação das métricas dos modelos mais robustos.

### Modelo 01: SARIMA

O modelo SARIMA (Seasonal Autoregressive Integrated Moving Avarage) foi aqui aplicado por ser amplamente utilizado para a previsão de séries temporais. Como ele é um modelo para séries univariadas, não foi possível utilizar informações extras na sua modelagem, apenas a do consumo de energia elétrica da indústria do sudeste.

### Modelo 02: FB Prophet

Prophet é uma poderosa biblioteca de previsão de séries temporais criada pelo time de ciência de dados do Facebook. Presente em Python e em R, essa biblioteca trabalha muito bem (e rapidamente) com séries temporais com muita sazonalidade (como é o nosso caso). Além disso, existe a possibilidade de utilizá-lo para séries temporais multivariadas.

### Modelo 03: VAR

O modelo VAR (Vector Autoregression) é um modelo estatístico de previsão de séries temporais multivariadas, como é o caso da nossa série temporal. Ele necessita que as séries estejam estacionárias, ou seja, que tenham média constante ao longo do tempo.

### Modelo 04: LSTM

LSTM (Long Short Term Memory) é um poderoso modelo de rede neural recorrente (RNN). Seu uso não é exclusivo para séries temporais, mas suas características como uma "memória" persistente o tornam relevantes para esse problema.

### Modelo 05: XGBoost

O modelo XGBoost (Extreme Gradient Boosting) é uma implementação poderosa (ou "extrema") do algoritmo de gradient boosting. Não é um modelo específico para séries temporais, mas sua versatilidade e bons resultados o tornam um bom candidato para resolver a versão supervisionada de séries temporais.

### Modelo 06: SVR

O modelo de SVR (Support Vector Regression) é a versão "de regressão" do Support Vector Machine. Novamente, não é um modelo específico de séries temporais, mas que pode ser aplicado com algumas adaptações nos dados.

### Modelo Extra: Lazy Predict

Aqui não temos um modelo em si, mas sim uma biblioteca que testa os modelos do Scikit-Learn de uma vez, com o objetivo de comparação entre eles. Ao transformarmos o problema da série temporal em um problema de aprendizagem supervisionada, os modelos de regressão podem ser aplicados para a previsão.

# Conclusão

Após a aplicação dos modelos obtemos os seguintes resultados para as métricas **Mean Absolute Value (MAE)**, **Mean Squared Error (MSE)** e Root **Mean Squared Error (RMSE)** calculadas nos dados de teste, e obtemos os seguintes dados:

<p align = 'center'>
 <img src = 'https://github.com/diascarolina/project-energy-consumption-in-brazil/blob/main/docs/metricas.png?raw=true'
</p>
 
Abaixo vemos um gráfico com as previsões do modelo XGBoost e do modelo SVR, os dois com melhor performance.
 
<p align = 'center'>
 <img src = 'https://github.com/diascarolina/project-energy-consumption-in-brazil/blob/main/docs/grafico_2modelos.png?raw=true'
</p>

Isso nos levou a escolher o modelo **SVR** para a previsão do consumo de energia da indústria no sudeste nos próximos 2 anos, considerando a métrica escolhida **RMSE**.

O gráfico a seguir mostra o resultado dessa previsão.

<p align = 'center'>
 <img src = 'https://github.com/diascarolina/project-energy-consumption-in-brazil/blob/main/docs/previsao.png?raw=true'
</p>


# Solução das Questões

### Questão 01. Análise de Dados

>A análise de dados foi feita na primeira parte do [notebook principal]. Considero relevante...

# Propostas de melhoria

A maior limitação que tive nesse projeto foi o tempo disponível para realizá-lo. Como melhoria, proponho um melhor ajuste dos hiperparâmetros utilizados nos modelos, para a obtenção de valores mais bem acurados para a série temporal do consumo de energia da indústria no sudeste. Criação de funções. Escalabilidade. Analisar os dados das outras regiões.

# Tecnologias Utilizadas

O notebook .ipynb principal foi produzido no Google Colab devido sua praticidade para esse tipo de solução.

As principais bibliotecas utilizadas foram:

-

-

# Referências

# Observações

Esse projeto é parte de um case técnico para a empresa 4intelligence (link), especializada em . Agradeço pela oportunidade.

# Contatos


