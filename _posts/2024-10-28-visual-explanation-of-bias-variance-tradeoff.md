
# Viés e variância


Aprenda sobre a importância de se entender o famoso trade-off Bias x Variance (viés e variância).


## Introdução:

Este artigo explicai sobre a importância de se entender o famoso trade-off Bias x Variance (viés e variância) e de como obter melhores resultados em seus modelos de machine learning ao ajustar corretamente esta compensação.

Antes de se aprofundar nas definições e termos técnicos, devemos entender o conceito em que estas expressões estão inseridas.

Caso você esteja iniciando nos estudos/carreira em Ciência de Dados, siga aqui comigo nesta pequena introdução para se contextualizar sobre este tema super importante para a área. Se já domina o conceito, sugiro que pule para o próximo tópico.

Em modelos de machine learning preditivos, o grande objetivo é prever uma resposta futura com base nos preditores passados (campos da sua base de dados que se relacionem com seu alvo resposta). Por exemplo, utilizar valores de oferta e demanda do último mês (preditores) para prever o preço de um produto no próximo mês (alvo).

Quando falamos em prever uma resposta, o primeiro passo é entender bem o passado dos seus dados. A ideia aqui é que, para saber se algo acontecerá, podemos simplesmente jogar uma moeda para o alto e “chutar” uma possibilidade ou podemos intuitivamente pensar que os acontecimentos futuros podem seguir determinados padrões que já ocorreram.

Por você estar lendo este artigo, a probabilidade é grande de você achar mais sensato utilizar a segunda opção: de aprender com os dados do passado, para prever o futuro. Então, caso eu fizesse uma pesquisa neste site perguntando qual das duas opções você, leitor, acha mais sensata, eu teria respostas com alto viés a segunda opção. Esse viés ocorre pelo fato de eu utilizar “baixa variância” na coleta de meus dados. Caso eu fizesse a mesma pergunta em sites não relacionados à ciência de dados, minhas respostas poderiam ser diferentes, então se eu quiser respostas com menor viés eu devo aumentar minha variância, pronto, esse é o ponto que queremos chegar!

Viés e variância aplicadas a machine learning:

Em uma linguagem simples, podemos dizer que um modelo de machine learning com alto viés “aprendeu pouco” e um modelo com muita variância “aprendeu demais”. Estas clássicas imagens demonstram com clareza este trade-off.


Fig 1: Ilustração gráfica de Viés e Variância; Fonte: https://www.3dimensoes.com.br/post/overfitting-e-underfitting
Através da figura 1, ficou claro que o objetivo aqui é obtermos um resultado com baixo viés e baixa variância. Com isso, dedicaremos nossos esforços para chegar a um resultado mais próximo possível desta realidade para garantirmos boa acurácia e precisão nas nossas previsões.

O segundo alvo na parte superior (baixo viés e alta variância) exemplifica bem os casos de overfitting ou “os modelos que aprenderam demais.” Perceba que o excesso de ajuste com os dados de treino neste caso não permitiu uma boa generalização com os dados novos calhando em uma baixa precisão.

O primeiro alvo da parte inferior (alto viés e baixa variância) demonstra os casos de underfitting ou “os modelos que aprenderam pouco.” Neste caso, houve um sub treinamento ao ponto do modelo não ser capaz de capturar a real relação entre os dados calhando também em uma previsão falha.

O segundo alvo da parte inferior da figura 1 (alto viés e alta variância) demonstra os casos de total inconsistência preditora de nosso modelo.

Dependendo do modelo de machine learning que escolhemos utilizar ou do ajuste de seus parâmetros, conseguimos ajustar essa curva de aprendizado para a nossa base de dados, buscando construir um modelo que seja flexível o suficiente para se adaptar a variações dos dados de entrada e que represente bem sua tendência ou respeite sua distribuição.


Fig 2: Ilustração gráfica de overfitting, underfitting e good balance; Fonte: https://www.dadosaleatorios.com.br/post/overfitting/
Overfitting ou excesso de treinamento = modelo muito complexo que não é capaz de generalizar resultados. O problema aqui é que este tipo de modelo é “viciado” nos dados em que ele foi treinado para aprender e qualquer variação de entrada de dados que fuja esse padrão será um problema.

Underfitting ou pouco treinamento = um modelo simples demais e que não se ajusta aos dados nem a sua distribuição. Assim como o exemplo anterior, esse tipo de ocorrência resulta em uma previsão falha e pouco assertiva.

Então, este é o famoso “cobertor curto”, no qual não podemos ter o melhor dos dois mundos e o papel do cientista de dados é justamente encontrar o melhor balanceamento que se adeque ao seu modelo de dados e a realidade do seu problema.

Os erros de previsão em um modelo de machine learning podem ser divididos em:

Erro irredutível
Erro de variância
Erro de viés
erro = erro irredutível + viés + variância

O erro irredutível ou “ruído”, o próprio nome já nos diz: Não pode ser reduzido. Ele independe do algoritmo utilizado e pode ser causado, por exemplo, por preditores mal enquadrados ou incompletos.

Erro de alto viés geralmente é mais cometido por algoritmos lineares, que apresentam facilidade no aprendizado mas são pouco flexíveis. Com isso, estes modelos apresentam um desempenho inferior quando aplicados em problemas mais complexos, por exemplo: Regressão linear, regressão logística…


Fig 3: Ilustração gráfica de regressão linear; Fonte: https://www.datageeks.com.br/regressao-linear/
Alguns exemplos de algoritmos de baixo viés:

KNN, SVM, árvores de decisão…

Erro de alta variância normalmente é encontrado em algoritmos não lineares, que apresentam grande flexibilidade mas pouca generalização. Exemplo de algoritmos de alta variação são árvores de decisão, KNN, SVM … e de baixa variação podem ser regressão linear e logística.


Fig 4: Ilustração gráfica de algoritimo KNN; Fonte: https://cambridgecoding.wordpress.com/2016/03/24/misleading-modelling-overfitting-cross-validation-and-the-bias-variance-trade-off/
O exemplo acima mostra claramente um exemplo de baixo viés à esquerda e alto viés a direita. No algoritmo KNN o ajuste é facilmente manipulado através da variável “K”, que serve justamente para fazer este balanço aumentando ou reduzindo a tendência do modelo.

Agora, se você está trabalhando com um modelo de regressão, é possível usar o que é chamado de regularização. De forma simples, a regularização pode ser entendida como a inserção ou redução de viés em um algoritmo, podendo reduzir ou aumentar sua variância. Modelos como Lasso Regression, Ridge regression e Elastic net regression são amplamente utilizados para acrescentar esse viés, de forma a torná-la mais generalista.


Fig 5: Ilustração gráfica de ridge regression com diversos alfas; Fonte: https://www.analyticsvidhya.com/blog/2016/01/ridge-lasso-regression-python-complete-tutorial/
No exemplo de modelo de Ridge acima, é possível perceber visualmente o resultado do ajuste do parâmetro alpha na adequação do modelo (linha azul) a realidade dos dados ( pontos verdes). A ideia aqui é ter a percepção visual desta mudança, mas na prática, o ideal é utilizar um parâmetro de comparação, como: (r², mae, mse) entre os diferentes alfas e identificar qual deles reduz mais o erro.

Outra técnica bastante interessante é a de cross validation ou validação cruzada, que pode ser usada para testar a capacidade de generalização de um modelo. A técnica faz divisões na base de dados de treino e teste e permite treinar e validar seus dados em diversos grupos distintos. Dessa forma, conseguimos mensurar a flexibilidade ou capacidade de generalização de um modelo antes mesmo da chegada de novos dados.


Fig 6: Ilustração gráfica de cross validation; Fonte: https://es.mathworks.com/discovery/cross-validation.html
Conclusão:

Agora que já entendemos um pouco sobre o trade-off viés e variância, seguem aqui algumas recomendações quando se for trabalhar com modelos de machine learning preditivos.

Fazer uma boa análise exploratória de dados antes de escolher o modelo a ser utilizado. Esta etapa te ajudará a entender melhor sua base de dados além de direcionar qual tipo de modelo você poderá utilizar.
Fazer a divisão da base de dados para treinar seus modelos (cross validation), dessa forma conseguimos saber se nosso modelo é capaz de generalizar o suficiente mantendo uma performance satisfatória.
Fazer ajustes inerentes no modelo, se possível, para balancear o viés e variância reduzindo assim o erro total.
Por fim, mas não menos importante, avaliar se a quantidade de dados utilizada para a construção do modelo é suficiente. Uma pequena quantidade de dados de treino pode trazer problemas de generalização causando overfitting muito facilmente. Se este for o caso, tente conseguir mais dados para sua base.


https://medium.com/bix-tecnologia/ci%C3%AAncia-de-dados-vi%C3%A9s-e-vari%C3%A2ncia-em-modelos-preditivos-f37b1b96a935