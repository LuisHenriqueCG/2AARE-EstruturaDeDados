# 2°Atividade Avaliativa Remota Extraordinária 24/05/2021
## Universidade Paranaense - UNIPAR
## Estrutura de Dados
### Nome: Luis Henrique de Camargo Gonçalves
### RA: 00210470    

## 1) A respeito dos principais métodos de ordenação existentes, descreva o funcionamento de cada um deles e faça comparativos de performance e execução. Também deve ser anexado um exemplo de implementação do mesmo, Ao final descreva qual o método de ordenação mais rápido, justificando a sua resposta.
## R: 


## Bubble Sort -
##### Bubble sort é o algoritmo mais simples, mas o menos eficientes. Neste algoritmo cada elemento da posição i será comparado com o elemento da posição i + 1, ou seja, um elemento da posição 2 será comparado com o elemento da posição 3. Caso o elemento da posição 2 for maior que o da posição 3, eles trocam de lugar e assim sucessivamente. Por causa dessa forma de execução, o vetor terá que ser percorrido quantas vezes que for necessária, tornando o algoritmo ineficiente para listas muito grandes.

-É verificado se o 3 é maior que 5, por essa condição ser falsa, não há troca.
-É verificado se o 5 é maior que 1, por essa condição ser verdadeira, há uma troca.
-É verificado se o 5 é maior que 2, por essa condição ser verdadeira, há uma troca.
-É verificado se o 5 é maior que 4, por essa condição ser verdadeira, há uma troca.
-O método retorna ao início do vetor realizando os mesmos processos de comparações, isso é feito até que o vetor esteja ordenado.

![](https://arquivo.devmedia.com.br/artigos/Bruno_Almeida_Honorato/Algoritmos-Resolucao-Problemas/2.jpg)

## Selection Sort -

#### Este algoritmo é baseado em se passar sempre o menor valor do vetor para a primeira posição (ou o maior dependendo da ordem requerida), depois o segundo menor valor para a segunda posição e assim sucessivamente, até os últimos dois elementos. Neste algoritmo de ordenação é escolhido um número a partir do primeiro, este número escolhido é comparado com os números a partir da sua direita, quando encontrado um número menor, o número escolhido ocupa a posição do menor número encontrado. Este número encontrado será o próximo número escolhido, caso não for encontrado nenhum número menor que este escolhido, ele é colocado na posição do primeiro número escolhido, e o próximo número à sua direita vai ser o escolhido para fazer as comparações. É repetido esse processo até que a lista esteja ordenada.

-Neste passo o primeiro número escolhido foi o 3, ele foi comparado com todos os números à sua direita e o menor número encontrado foi o 1, então os dois trocam de lugar.
-O mesmo processo do passo 1 acontece, o número escolhido foi o 5 e o menor número encontrado foi o 2.
-Não foi encontrado nenhum número menor que 3, então ele fica na mesma posição.
-O número 5 foi escolhido novamente e o único número menor que ele à sua direita é o 4, então eles trocam.
Vetor já ordenado.

![](https://arquivo.devmedia.com.br/artigos/Bruno_Almeida_Honorato/Algoritmos-Resolucao-Problemas/3.jpg)

## Insertion sort - 

#### O Insertion sort é um algoritmo simples e eficiente quando aplicado em pequenas listas. Neste algoritmo a lista é percorrida da esquerda para a direita, à medida que avança vai deixando os elementos mais à esquerda ordenados. O algoritmo funciona da mesma forma que as pessoas usam para ordenar cartas em um jogo de baralho como o pôquer.

-Neste passo é verificado se o 5 é menor que o 3, como essa condição é falsa, então não há troca.
-É verificado se o quatro é menor que o 5 e o 3, ele só é menor que o 5, então os dois trocam de posição.
-É verificado se o 2 é menor que o 5, 4 e o 3, como ele é menor que 3, então o 5 passa a ocupar a posição do 2, o 4 ocupa a posição do 5 e o 3 ocupa a posição do 4, assim a posição do 3 fica vazia e o 2 passa para essa posição.
--O mesmo processo de comparação acontece com o número 1, após esse processo o vetor fica ordenado.
![](https://arquivo.devmedia.com.br/artigos/Bruno_Almeida_Honorato/Algoritmos-Resolucao-Problemas/4.jpg)

## Quick sort - 
#### O Quicksort é o algoritmo mais eficiente na ordenação por comparação. Nele se escolhe um elemento chamado de pivô, a partir disto é organizada a lista para que todos os números anteriores a ele sejam menores que ele, e todos os números posteriores a ele sejam maiores que ele. Ao final desse processo o número pivô já está em sua posição final. Os dois grupos desordenados recursivamente sofreram o mesmo processo até que a lista esteja ordenada.

-O número 3 foi escolhido como pivô, nesse passo é procurado à sua direita um número menor que ele para ser passado para a sua esquerda. O primeiro número menor encontrado foi o 1, então eles trocam de lugar.
-Agora é procurado um número à sua esquerda que seja maior que ele, o primeiro número maior encontrado foi o 5, portanto eles trocam de lugar.
-O mesmo processo do passo 1 acontece, o número 2 foi o menor número encontrado, eles trocam de lugar.
-O mesmo processo do passo 2 acontece, o número 4 é o maior número encontrado, eles trocam de lugar.
-O vetor desse exemplo é um vetor pequeno, portanto ele já foi ordenado, mas se fosse um vetor grande, ele seria dividido e recursivamente aconteceria o mesmo processo de escolha de um pivô e comparações.
![](https://arquivo.devmedia.com.br/artigos/Bruno_Almeida_Honorato/Algoritmos-Resolucao-Problemas/5.jpg)
   