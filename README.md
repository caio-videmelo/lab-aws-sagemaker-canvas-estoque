🚀 Passo a Passo
1. Selecionar Dataset
O Dataset selecionado foi o 'dataset-1000-com-preco-promocional-e-renovacao-estoque'

2. Construir/Treinar
Com o dataset selecionado, cliquei em 'create a model' e coloquei o nome do modelo (Nesse caso, EstoqueInteligente1)

Configurei a variavel Quantidade_Estoque como 'target' e em seguida cliquei em 'configure model'

A coluna que identifica o produto é a ID_produto e a coluna que refere-se ao tempo é Data_Evento.

Configurei para prever um dia.

Selecionei 'Quick build'

![EstoqueInteligente1Model](https://github.com/caio-videmelo/lab-aws-sagemaker-canvas-estoque/assets/174061850/36c78624-2026-4bd7-9a79-50d2a413e14b)

3. Analisar

Avaliando as Métricas de Performance do Modelo.
AVG.wQL (Average Weighted Quantile Loss): 0.393

A métrica AVG.wQL de 0,393 representa a perda média ponderada por quantil. Quanto menor esse valor, melhor o desempenho do modelo em prever os diferentes percentis (P10, P50, P90). Um valor de 0,393 sugere que o modelo ainda pode ser aprimorado para melhorar a precisão das previsões por quantil.

MAPE (Mean Absolute Percentage Error): 0.464

O MAPE expressa o erro médio como uma porcentagem dos valores reais. Um valor de 0.464 indica que, em média, as previsões do modelo têm um erro percentual absoluto de 46,4% em relação aos valores reais. Isso sugere que o modelo não está prevendo com alta precisão e pode precisar de ajustes ou melhorias.

WAPE (Weighted Absolute Percentage Error): 0.584

O WAPE de 0,584 significa que o erro absoluto ponderado pelas magnitudes dos valores reais é de 58,4%. Essa métrica também aponta para um desempenho insatisfatório do modelo, com erros significativos.

RMSE (Root Mean Squared Error): 26.501

As previsões do modelo têm um erro quadrático médio de 26,501 unidades. Esse valor é relativamente alto, sugerindo que o modelo tem dificuldade em fazer previsões precisas.

MASE (Mean Absolute Scaled Error): 0.576

O MASE de 0,576 é menor que 1, o que significa que o modelo tem um desempenho melhor que uma previsão ingênua. Isso é um ponto positivo, mas ainda assim indica que o modelo pode ser aprimorado.

Em resumo, as métricas apresentadas indicam que o modelo de séries temporais treinado no SageMaker Canvas não está apresentando um desempenho satisfatório.

O MAPE, WAPE e RMSE apontam para erros significativos nas previsões, enquanto o MASE e a AVG.wQL sugerem que o modelo pode ser aprimorado.

Portanto, serão necessários ajustes e refinamentos adicionais no modelo para melhorar sua precisão e confiabilidade.

4. Prever
Selecionei 'single prediction' e fiz as previsões individuais para cada produto. Fiz previsões para o produto 23 para o proximo dia com três cenarios distintos (P10 , P50 e P90):

![single_prediction_results](https://github.com/caio-videmelo/lab-aws-sagemaker-canvas-estoque/assets/174061850/fa81f5b0-6fa0-48b4-bcdb-36aa0fbd980b)

Explicando a Relação entre Preço e Percentis de Previsão de Estoque
Os percentis P10, P50 e P90 são medidas estatísticas importantes para entender a distribuição das previsões de estoque geradas pelo seu modelo de séries temporais.

Relação com o Preço

O preço do produto é um fator-chave que influencia fortemente as previsões de estoque representadas pelos diferentes percentis:

P10: Este percentil indica o valor abaixo do qual estão 10% das previsões de estoque. Ou seja, é o cenário mais pessimista, com baixos níveis de estoque. Geralmente, P10 está associado a períodos de preços mais baixos, quando a demanda tende a ser menor.

P50: Este é o valor mediano das previsões, representando o cenário mais provável. Quando o preço está em níveis típicos ou "normais", a previsão de estoque tende a se concentrar em torno de P50.

P90: Este percentil indica o valor abaixo do qual estão 90% das previsões de estoque.

Representa o cenário mais otimista, com altos níveis de estoque. Normalmente, P90 está relacionado a períodos de preços mais elevados, quando a demanda tende a ser maior.

Portanto, a variação do preço do produto é um fator determinante para a distribuição das previsões de estoque representada pelos diferentes percentis.

Períodos de preços mais baixos tendem a resultar em previsões com valores mais próximos de P10, enquanto preços mais altos estão associados a previsões próximas de P90.

Compreender essa relação entre preço e os percentis de previsão de estoque é essencial para tomar decisões de gestão de estoque e planejamento da produção de forma mais assertiva.
