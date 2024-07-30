Meu nome é Flavia e este projeto é baseado no Lab do curso da DIO Machine Learning para Iniciantes.


# 📊 LAB Previsão de Estoque Inteligente na AWS 

Neste Lab foi criado um modelo de previsão de estoque inteligente usando o SageMaker Canvas para criar previsões de estoque baseadas em Machine Learning (ML). 

O modelo criado foi feito a partir de uma base de dados de estoque de produtos que possue os campos: ID_PRODUTO, PRECO, FLAG_PROMOCAO, DATA_EVENTO (data da atualização do registro),QUANTIDADE_ESTOQUE, sendo o campo qtd-estoque renovável e o campo FLAG_PROMOCAO preenchido com 1 (promoção) ou 0 (sem promoção). 

Com o treinamento, foi criado um modelo de previsão de estoque e alguns insights foram gerados a partir  da análise do modelo de previsão.


## 🚀 Passo a Passo

### 1. Selecionação do Dataset

-   O dataset escolhido foi o dataset-1000-com-preco-variavel-e-renovacao-estoque disponibilizado pela DIO .
-   Foi feito upload do arquivo no sagemaker canvas  e salvo com o nome estoque-lab-dio.
-   Este dataset foi usado para construir o modelo de estoque inteligente.
  
   
### 2. Construção/Treinamento

-   As variáveis de entrada foram: quantidade de estoque (campo target/campo que será feita a previsão).
-   O treinamento do modelo foi feito da forma "Quick Build".

### 3. Analise

-   Após o treinamento, foram verificadas as seguintes métricas, que serão rapidamente analisadas:
-   AWG.WQL(Média da Perda Quantil Ponderada) = 0.06  =  6% - mede o erro nas previsões, ponderado pela importância de cada item.
-   MAPE  (Erro Percentual Médio Absoluto): = 0.148 =  14,8%:   porcentagem de erro das previsões em relação aos valores reais
-   WAPE (Erro Percentual Absoluto Ponderado) = 0.100 -  10%  porcentagem de erro das previsões em relação aos valores/itens mais criticos.
                                                              Quanto mais proximo de zero melhor ou seja o modelo está prevendo com uma boa precisão.
-   RMSE(Raiz do Erro Quadrático Médio) = 5.765
-   MASE(Erro Escalado Médio Absoluto): =  0.301
-     
  Obs.: é importante verificar que todos modelos de treinamento possuem sempre alguma porcentagem de erros, ou seja não fazerm previsões 100% corretas.

-  AS Colunas do dataset que tiveram impacto para a geração do modelo foram:
-  PRECO = 9,61%
-  FLAG-PROMOCAO = 0%
-  
  

-   
-   Verifique as principais características que influenciam as previsões.
-   Faça ajustes no modelo se necessário e re-treine até obter um desempenho satisfatório.

### 4. Previsão

-   Use o modelo treinado para fazer previsões de estoque.
-   Exporte os resultados e analise as previsões geradas.
-   Documente suas conclusões e qualquer insight obtido a partir das previsões.

## 🤔 Dúvidas?

