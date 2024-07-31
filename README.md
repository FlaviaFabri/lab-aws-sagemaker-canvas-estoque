Meu nome é Flavia e este Laboratório foi feito com o objetivo de realizar a atividade de Lab do curso da DIO "Machine Learning para Iniciantes".


# 📊 LAB Previsão de Estoque Inteligente na AWS 

Neste Lab foi criado um modelo de previsão de estoque inteligente, usando a ferramenta SageMaker Canvas da AWS que gera modelos em  Machine Learning (ML). 

O modelo criado foi feito a partir de uma base de dados de estoque de produtos que possue os campos: ID_PRODUTO, PRECO, FLAG_PROMOCAO, DATA_EVENTO (data da atualização do registro),QUANTIDADE_ESTOQUE, sendo o campo QUANTIDADE_ESTOQUE renovável e o campo FLAG_PROMOCAO, preenchido com 1 (promoção) ou 0 (sem promoção). 

Com o treinamento, foi criado um modelo de previsão de estoque e alguns insights foram gerados a partir da análise das previsões.


## 🚀 Passo a Passo

### 1. Selecionação do Dataset

-   O dataset escolhido foi o dataset-1000-com-preco-variavel-e-renovacao-estoque.csv disponibilizado pela DIO .
-   Foi feito upload do arquivo no sagemaker canvas  e salvo com o nome de estoque-lab-dio.csv.
-   Este dataset foi usado para construir o modelo de estoque inteligente.
  
   
### 2. Construção/Treinamento:

-   As variáveis de entrada foram: quantidade de estoque (campo target/campo que será feita a previsão).
-   A quantidade de estoque que é prevista pelo modelo foi definida prever essa quantidade para um dia após a última atualização de estoque de cada item no dataset.
-   O treinamento do modelo foi feito pelos métodos QUICK BUILD e STANDAR BUILD.
-   O modelo gerado pelo método QUICK BUILD foi escolhido para fazer a previsão de estoque.

### 3. Análise

-  Após o treinamento pelo método QUICK BUILD , foram verificadas as seguintes métricas, que serão rapidamente analisadas:

    - Avg.wQL(Média da Perda Quantil Ponderada)=  0,06   (mede a quantidade de erro nas previsões, ponderado pela importância de cada item);
    - MAPE  (Erro Percentual Médio Absoluto) =    0,148  (média da porcentagem de erro das previsões em relação aos valores reais);
    - WAPE (Erro Percentual Absoluto Ponderado) = 0,100  (média da porcentagem de erro das previsões em relação à importância de cada item no estoque);
    - RMSE (Raiz do Erro Quadrático Médio) =      5,765  (diferença média entre os valores previstos e os valores reais, dando mais peso aos grandes erros);
    - MASE(Erro Escalado Médio Absoluto): =       0,301  (Compara o erro da previsão com um modelo simples. Um valor de MASE menor que 1 indica que o modelo está fazendo                                                                 previsões mais precisas do que simplesmente usar a média histórica).   
       
-  OBS.: é importante verificar que todos modelos gerados possuem sempre alguma porcentagem de erros, ou seja não fazerm previsões 100% corretas.

-  As Colunas do dataset que tiveram impacto para a geração do modelo foram:
    - PRECO = 9,61% e FLAG_PROMOCAO = 0% .

-  Após o treinamento pelo método STANDARD BUILD , foram verificadas as seguintes métricas, que serão rapidamente analisadas:
  
    -  Avg.wQL(Média da Perda Quantil Ponderada)=  0,150 ;
    -  MAPE  (Erro Percentual Médio Absoluto)=     0,258 ;
    -  WAPE (Erro Percentual Absoluto Ponderado)=  0,204 ;
    -  RMSE(Raiz do Erro Quadrático Médio) =      20,435 ;
    -  MASE(Erro Escalado Médio Absoluto): =       0,000 .   
  
-  As Colunas do dataset que tiveram impacto para a geração do modelo foram:
     -  PRECO = -12,48% e FLAG_PROMOCAO = 87,52%

-  Analisando os resultados das estáticas acima, é possível verificar que o campo FLAG_PROMOCAO teve impacto 0 ou positivo durante o treinamento dos modelos.
-  Apesar do modelo gerado pelo método STANDARD apresentar o valor da  métrica MASE igual a zero, os outros valores das métricas gerados pelo método QUICK BUILD são menores do   que os valores apresentados anteriormente no modelo STANDARD.
-  Além disso, o valor da métrica RMSE foi o que mais impactou na escolha do modelo. Ele foi bem menor no modelo gerado pelo método QUICK BUILD, sendo menor, ele ajuda a         diminuir as discrepâncias que podem levar a um super ou subestimativas das críticas.
-  Dessa forma, o modelo gerado pelo método QUICK BUILD foi o escolhido por apresentar um desempenho mais satisfatório.
  

### 4. Previsão

-  Nesta etapa, foram geradas previsões com todos os itens do dataset utilizando o modelo escolhido. O arquivo gerado com as previsões de todos os itens é o
    previsoes-de-todos-produtos.csv.
-  Também foram geradas SINGLE PREDICTIONS (previsões individual) de alguns itens para poder ser possível verificar uma visualização individual de cada produto e, assim,           ajudar a fazer uma análise crítica das previsões de forma geral.
-  Com a observação dos gráricos gerados pelas previsiões individuais e dos dados do arquivo de previsões de todos os itens, foi possíel verificar que a maioria dos itens         apresentam um queda na quantidade de estoque indicada na previsão dos percentis 50 e 90, como é apresentado na figura abaixo, que mostra o item 1008.   

![single_prediction_results(1008)](https://github.com/user-attachments/assets/f5ce66c1-7f26-41b6-bb85-cededbcd511f)

 O controle de estoque inteligente gerado pelo modelo no AWS SAGEMAKKE CANVAS apresenta as métricas (percentis) abaixo para cada item:
 P10 (quantidade de estoque necessária em um cenário de baixa demanda do produto);
 P50 (quantidade de estoque necessária em um cenário mais comum da demanda do produto);
 P90 (quantidade de estoque necessária em um cenário de demanda máxima do produto).

 Para o caso do item 1008, mostrado na ilustração acima, é possível verificar que a quantidade de estoque para todas métricas estão diminuindo, o que torna possível inferir que o produto está sendo menos demandado em relação a sua demanda histórica (a demanda histórica é uma infomação também fornecida pelo AWS SAGEMAKER CANVAS). No caso, a demadanda histórica do produto é 33 e os percentis P10,P50 e P90 apresentam os seguintes valores: 14,653- 21,5867 - 31,682.

 No entanto, existem alguns casos de alguns produtos (que ocorrem menos frequetemente), cujas métricas, citadas anteriormente, apresentam-se de forma diferente em relação ao produto 1008. Esse é o caso do produto 1022, mostrado no gráfico abaixo, gerado na previsão individual do produto no SAGEMAKE CANVAS:
 
 ![single_prediction_results(1022)](https://github.com/user-attachments/assets/e2d024a0-f730-4188-bc6c-9aaebc9106db)

 Para o caso item 1022, mostrado na ilustração acima, é possível verificar que a quantidade de estoque para todas métricas estão aumentando, o que torna possível inferir que o produto está sendo mais demandado em relação à média histórica. A demanda histórica dele é 9 e os percentis P10,P50 e P90 apresentam os seguintes valores: 1,672- 14,725 - 99,999).

 OBS.: Os gráficos gerados pela opçao previsão individual do produto apresentam os mesmos percentis que estão no arquivo previsão-estoque-de-todos-produtos.csv.


