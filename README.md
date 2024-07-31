Meu nome é Flavia e este projeto/lab foi feito para a atividade de Lab do curso da DIO "Machine Learning para Iniciantes".


# 📊 LAB Previsão de Estoque Inteligente na AWS 

Neste Lab foi criado um modelo de previsão de estoque inteligente usando o SageMaker Canvas para criar previsões de estoque baseadas em Machine Learning (ML). 

O modelo criado foi feito a partir de uma base de dados de estoque de produtos que possue os campos: ID_PRODUTO, PRECO, FLAG_PROMOCAO, DATA_EVENTO (data da atualização do registro),QUANTIDADE_ESTOQUE, sendo o campo qtd-estoque renovável e o campo FLAG_PROMOCAO preenchido com 1 (promoção) ou 0 (sem promoção). 

Com o treinamento, foi criado um modelo de previsão de estoque e alguns insights foram gerados a partir  da análise do modelo de previsão.


## 🚀 Passo a Passo

### 1. Selecionação do Dataset

-   O dataset escolhido foi o dataset-1000-com-preco-variavel-e-renovacao-estoque disponibilizado pela DIO .
-   Foi feito upload do arquivo no sagemaker canvas  e salvo com o nome estoque-lab-dio.
-   Este dataset foi usado para construir o modelo de estoque inteligente.
  
   
### 2. Construção/Treinamento:

-   As variáveis de entrada foram: quantidade de estoque (campo target/campo que será feita a previsão).
-   O treinamento do modelo foi feito pelos métodos "Quick Build" e "Standard Build".
-   O modelo gerado pelo método "Quick Build" foi escolhido para fazer a previsão de estoque.

### 3. Analise

-  Após o treinamento pelo método QUICK BUILD , foram verificadas as seguintes métricas, que serão rapidamente analisadas:
   
  -> Avg.wQL(Média da Perda Quantil Ponderada):  0,06   (mede a quantidade de erro nas previsões, ponderado pela importância de cada item);
  -> MAPE  (Erro Percentual Médio Absoluto):     0,148  (média da porcentagem de erro das previsões em relação aos valores reais);
  -> WAPE (Erro Percentual Absoluto Ponderado)   0,100  (média da porcentagem de erro das previsões em relação à importância de cada item no estoque);
                                                         Um WAPE menor é desejável, pois indica que o modelo está prevendo com mais precisão para os itens mais críticos,                                                                o que é essencial para uma gestão eficiente do estoque);
  -> RMSE(Raiz do Erro Quadrático Médio) =       5,765  (diferença média entre os valores previstos e os valores reais, dando mais peso a grandes erros);
  -> MASE(Erro Escalado Médio Absoluto): =       0,301  (Compara o erro da previsão com um modelo simples. Um valor de MASE menor que 1 indica que o modelo está fazendo                                                                 previsões mais precisas do que simplesmente usar a média histórica).   
  
      
  Obs.: é importante verificar que todos modelos de treinamento possuem sempre alguma porcentagem de erros, ou seja não fazerm previsões 100% corretas.

-  As Colunas do dataset que tiveram impacto para a geração do modelo foram:
    -> PRECO = 9,61%
    -> FLAG_PROMOCAO = 0%

-   Após o treinamento pelo método STANDARD BUILD , foram verificadas as seguintes métricas, que serão rapidamente analisadas:
  -> Avg.wQL(Média da Perda Quantil Ponderada):  0,150 ;
  -> MAPE  (Erro Percentual Médio Absoluto):     0,258 ;
  -> WAPE (Erro Percentual Absoluto Ponderado)   0,204 ;
  -> RMSE(Raiz do Erro Quadrático Médio) =      20,435 ;
  -> MASE(Erro Escalado Médio Absoluto): =       0,000 .   
  
-  AS Colunas do dataset que tiveram impacto para a geração do modelo foram:
    -> PRECO = -12,48%
    -> FLAG_PROMOCAO = 87,52%

 -  Analisando os resultados das estáticas acima, é possível verificar que o campo FLAG_PROMOCAO teve impacto 0 ou positivo durante o treinamento dos modelos.
 -  Apesar do modelo gerado pelo método STANDARD apresentar o valor da  métrica MASE igual a zero, os outros valores das métricas gerados pelo método QUICK BUILD são menores       do que os valores  apresentados anteriormente no modelo STANDARD.
 -  O valor da métrica RMSE foi o que mais impactou na escolha do modelo. Ele foi bem menor no modelo gerado pelo método QUICK BUILD, sendo menor, ele ajuda a diminuir as         discrepâncias que podem levar a um super ou subestimativas das críticas.
-  Dessa forma, o modelo gerado pelo método QUICK BUILD foi o escolhido por apresentar um desempenho mais satisfatório.
  

### 4. Previsão

-   Nesta etapa, foram geradas previsões com o modelo escolhido. O arquivo.
-   Exporte os resultados e analise as previsões geradas.
-   Documente suas conclusões e qualquer insight obtido a partir das previsões.



