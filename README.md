Meu nome é Flavia e este projeto é baseado no Lab do curso da DIO Machine Learning para Iniciantes.


# 📊 LAB Previsão de Estoque Inteligente na AWS 

Neste Lab foi feito um modelo de previsão de estoque inteligente usando o SageMaker Canvas para criar previsões de estoque baseadas em Machine Learning (ML). 

O modelo criado foi feito com uma base de dados de estoque de produtos que possue os campos: preço, promoção, estoque, sendo o campo estoque renovável e campo promoção preenchido com 1 ou 0. 

A partir do treinamento dele foi criado um modelo de previsão de estoque e alguns insights serão gerados a partir  deste modelo de previsão.


## 🚀 Passo a Passo

### 1. Selecionar Dataset

-   O dataset escolhido foi o dataset-1000-com-preco-variavel-e-renovacao-estoque disponibilizado pela DIO .
-   Foi feito upload do arquivo no sagemaker canvas  e salvo com o nome estoque-lab-dio.
-   Este dataset será usado para construir o modelo de estoque inteligente.
  
   
### 2. Construir/Treinar

-   As variáveis de entrada foram: quantidade de estoque (campo target/campo que será feita a previsão), flag-promocao (foi usada na configuração do modelo como agrupador do campo de identificação do produto).
-   O treinamento do modelo foi feito da forma "Quick Build".

### 3. Analisar

-   Após o treinamento, foram verificadas as seguintes métricas:
-   
-   Verifique as principais características que influenciam as previsões.
-   Faça ajustes no modelo se necessário e re-treine até obter um desempenho satisfatório.

### 4. Prever

-   Use o modelo treinado para fazer previsões de estoque.
-   Exporte os resultados e analise as previsões geradas.
-   Documente suas conclusões e qualquer insight obtido a partir das previsões.

## 🤔 Dúvidas?

