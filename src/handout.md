Problema da Mochila
===================

[comment]: <> (Imagem da mochila)


A ideia
--------

O problema da mochila é um dos algoritmos mais importantes da história, sendo estudado a mais de um século! Esse algoritmo tem diversas aplicações, desde o mercado financeiro até a computação, inclusive em algumas situações não muito convencionais como veremos a seguir. 

Para entendermos melhor o problema da mochila, vamos considerar uma situação do nosso dia-a-dia. 

<div style="height:200px;display:flex;justify-content:space-evenly;align-items:flex-start;">
    <img src="fernando.jpg" alt="fernando" width="140"/>
    <img src="mochila.jpg" alt="mochila" width="140"/>
</div>

Esse é o Fernando, um estudante do 4° semestre de engenharia do Insper. Fernando deixou para última hora estudar para sua prova final de eletromagnetismo, mas como sabemos essa é uma matéria muito vasta e com diversos conteúdos, sendo impossível estudar tudo nas 6 horas que ele tinha disponível.

Tendo isso em vista, Fernando pensou em uma ideia para tentar se salvar, que consistia em separar toda a máteria em áreas de estudo. Para cada área, Fernando analisou quanto tempo ele demoraria para aprender e a média de quantos pontos cada conteúdo correspondeu nas últimas cinco provas dos semestres passados. Com esses dados em mãos, Fernando agora só precisa encontrar a melhor combinação de áreas para estudar. 

<div style="height:200px;display:flex;align-items:center;justify-content:space-evenly">
    <img src="eletrodinamica.jpg" alt="áreas de estudo" height="120" />
    <img src="laboratorios.jpg" alt="áreas de estudo" height="120" />
    <img src="maxwell.jpg" alt="áreas de estudo" height="120" />
    <img src="ondulatoria.jpg" alt="áreas de estudo" height="120" />
</div>


O primeiro pensamento do estudante foi de estudar as duas maiores áreas em relação a pontuação. Assim, ele estudaria Ondulatória e Leis de Maxwell que consumiriam 5 horas de estudo e lhe garantiriam 6 pontos na prova. 

<div style="height:200px;display:flex;align-items:center;justify-content:space-evenly">
    <img src="maxwell.jpg" alt="áreas de estudo" height="120" />
    <img src="ondulatoria.jpg" alt="áreas de estudo" height="120" />
</div>


??? Checkpoint 
Você deve ter percebido que o Fernando subestimou o problema de planejar os seus estudos. Qual é a melhor maneira que ele pode combinar as matérias para que possa estudar a maior combinação de pontos possíveis nas 6 horas que ele tem disponível?

::: Gabarito
Para maximizar os seus estudos, Fernando deveria levar em conta opções fora as de maior valor! Assim chegaria que a melhor opção é estudar Eletrodinâmica, Laboratórios e Leis de Maxwell. 

<div style="height:200px;display:flex;align-items:center;justify-content:space-evenly">
    <img src="eletrodinamica.jpg" alt="áreas de estudo" height="120"/>
    <img src="laboratorios.jpg" alt="áreas de estudo" height="120"/>
    <img src="maxwell.jpg" alt="áreas de estudo" height="120" />
</div>
:::

???

Para a sorte do Fernando, o seu amigo Pedro que está no quinto semestre percebeu que seu dilema era muito relacionado a um problema que ele estava estudando na matéria de Desafios da Programação, **o problema da mochila**! 

Curioso, Fernando pediu para que seu amigo explicasse como resolveu o problema.

??? Checkpoint
Primeiro Pedro pediu para que Fernando considerasse o caso mais simples de todos, uma mochila vazia e apenas um item. Qual deverá ser o processo de escolha para preencher a mochila nesse caso?

::: Gabarito
Primeiro devemos verificar se o item cabe ou não na mochila. Se esse item couber, vamos coloca-lo na mochila e considerar que o valor da mochila agora é o valor anterior da mochila, somado com o valor do item. Para esse caso de mochila vazia, o valor será somente o próprio valor do item!

:mochila_vazia
:::
???

Claro que a primeira vista, o caso mais simples de todos não parece ser muito útil para resolver um problema complexo como esse.

??? Checkpoint
Será que não existe uma maneira de transformar um problema da mochila que analisa vários itens em problemas menores, ou até mesmo, em vários subproblemas que analisam o caso trivial visto acima? Que método de resolução de problemas de programação seria útil para nos auxiliar nisso?

::: Gabarito
Quando consideramos três itens por exemplo, é possível dividir esse problema em subproblemas de dois itens. Com a resposta dos subproblemas analisaremos se vale a pena ou não colocar o terceiro item na mochila! 

Isso seria uma abordagem **recursiva** para resolver o problema da mochila! Para resolver o problema para três itens, preciso primeiro saber a resposta desse problema para dois itens, e assim em diante. 

:recursao
::: 
???

Porém, determinar quais são os subproblemas não é tão simples, envolve determinar qual mochila tem o maior valor: caso colocassemos o item atual na mochila e caso não colocassemos! Isso garante que vamos levar em conta todas as combinações possiveis de itens dentro da mochila e assim vamos conseguir determinar qual o maior valor possivel para essas combinações. 

??? Checkpoint
Vamos considerar uma mochila com capacidade 6 e os dois itens abaixo.

![](cp_n2.png)

Quais são os subproblemas necessários para determinar a melhor mochila possível considerando dois itens a serem analisados (**n = 2**)? 
Como as duas variáveis da mochila, capacidade e valor, são diferentes nesses subproblemas?


*Dica: Pense em chamadas recursivas de funções.*

::: Gabarito
Os dois subproblemas são: a melhor mochila caso não colocassemos o 2º item na mochila e a melhor mochila caso colocassemo o 2º item na mochila! 

O primeiro subproblema equivale ao mesmo problema que o original, porém analisando **n - 1** itens, o que para o caso equivale a 1 item. O segundo também equivale ao mesmo problema que o original, analisando **n - 1** itens, porém com uma nova capacidade para a mochila, **W - peso do item colocado**.

:passo_da_recursao
:::
???

Mas peraí, o que faremos se o item analisado não cabe na mochila? Para esse caso não podemos realizar o segundo subproblema, então vamos levar em conta apenas o resultado do primeiro subproblema!

Vamos ver se você está entendendo qual é o **passo da recursao** para o problema da mochila!

??? Checkpoint
Considerando os valores e pesos dos itens abaixo e n = 3, desenhe as chamadas recursivas de n = 2 e n = 1, e quais os de W e V. 

![](cp.png)

Faça o desenho no mesmo formato de árvore do checkpoint anterior. Para dar uma facilitada, deixei o começo da árvore pronto para vocês :)

<div style="height:300px;display:flex;align-items:center;justify-content:space-evenly">
    <img src="cp_arv.png" alt="áreas de estudo" height="300"/>
</div>

::: Gabarito
![](cp_gabarito.png)
:::
???

Agora que já dominamos o passo da recursão vamos considerar a **base da recursão**.

??? Checkpoint
Pense em qual deve ser a base do problema.

*Dica: Quais serão as situações em que não conseguiremos mais colocar itens na mochila?*
::: Gabarito
A base da recursão será quando **n = 0**, ou seja, consideramos todos os itens ou **W = 0**, o caso em que não é possível mais preencher a mochila! 
:::

???

Podemos resumir o algoritmo da seguinte maneira:

:busca

[comment]: <> (animação do slide)

A ideia que Pedro ensinou para o seu amigo é a **solução recursiva** do problema da mochila. 

Solução Recursiva 
---------------

Vamos começar a pensar em como traduzir essa resolução para código. Precisamos escrever uma função que recebe como entrada os itens e a capacidade da mochila e nos devolve o maior valor possível que cabe na mochila para aqueles itens. Lembrando que cada item possui um valor e um peso. 

A maneira mais simples de representar os itens seria através de dois arrays, um para os valores, outro para os pesos.

``` c
int valores[] = {2, 2, 3, 3};
int pesos[] = {2, 2, 2, 3};
```
Para o item **n**, o seu valor estaria em ```c valores[n - 1]``` e seu peso em ```c pesos[n - 1]```.
O conteudo de ```c knapsack()``` seria semelhante ao pseudocódigo a seguir:

```txt
se n == 0 ou W == 0
    valor da mochila é 0
senão
    se peso do item <= W
        subproblema1 = maior valor da mochila sem o item
        subproblema2 = maior valor da mochila com o item

        valor da mochila é o maior valor dentre subproblema1 e subproblema2
    senão
        valor da mochila é o maior valor da mochila sem o item
```
O pseudocódigo pode ser traduzido para **C** da seguinte forma:

```c
int max(int a, int b) {
    return a > b ? a : b;
}

int knapsack(int valores[], int pesos[], int n, int W) {
    if (n == 0 || W == 0) {
        return 0;
    }

    if (W >= pesos[n - 1]) {
        return max(knapsack(valores, pesos, n - 1, W), 
        valores[n - 1] + knapsack(valores, pesos, n - 1, W - pesos[n - 1]));
    }

    return knapsack(valores, pesos, n - 1, W);
}
```

Finalmente temos um algoritmo que pode solucionar o problema da mochila! Mas será que essa é a melhor solução possível? 

??? Checkpoint
Usando as estratégias vistas em aula, calcule a complexidade do algoritmo da **solução recursiva**, utilizando a notação **O**!


:::Gabarito
Passo A: Escrever a recorrência
```c
            /
           | 1             se n ou W == 0;
k(n, W) = <
           | k(n - 1, W) + k(n - 1, W - a)    se n ou W > 0;
            \
```
OBS: Como a notação O leva sempre em consideração o pior caso possível, para obtermos o maior número de chamadas recursivas para a função ```c knapsack()```, "a" teria que ser igual a **zero**! Por isso, no pior caso a função sempre faz duas chamadas recursivas, já que sempre entra no ```c if(W >= pesos[n - 1])```.

Assim o parâmetro W pode ser desconsiderado para esse cálculo: 
```c
         /
        | 1           se n == 0;
k(n) = <
        | 2k(n - 1)   se n > 0;
         \
```

Passo B: Desenhe a árvore de recursão:

<div style="height:500px;display:flex;justify-content:space-evenly;align-items:flex-start;">
    <img src="arvore.drawio.svg" alt="arvore" width="700"/>
</div>

Passo C: Estimar a altura *h* da arvore
```txt
Tamanho n diminui em 1 a cada andar enquanto for maior que 0.
No antepenúltimo andar (h-2), ainda não chegamos na base.

n - 1(h - 2) > 0
n - h + 2 > 0
h < n + 2

h = O(n), ou seja, h <= c n
```

Passo D: Calcular a soma da complexidade de cada andar

```txt
Ao longo dos andares, temos
  (1 + 2 + 4 + ... + 2^(h-2)) + 2^(h-1)
= (1 + 2 + 4 + ... + 2^(h-2) + 2^(h-1))

Soma de PG
- primeiro elemento 1
- razão 2
- número de elementos h

= 1 (2^h - 1) / (2 - 1)
= 2^h - 1.

Como h <= n, a complexidade é O(2^n)
```
:::
???

O problema da solução recursiva
-----------------------------

Como vocês devem imaginar após calcular a complexidade da **solução recursiva**, esse não deve ser o melhor algoritmo para resolver o problema da mochila. O principal motivo para essa complexidade alta é a quantidade enorme de **chamadas repetidas** que são feitas ao longo de uma rotina:

:memo

<!-- Animação mostrando as chamadas repetitivas -->

??? Checkpoint
Existe algum jeito que podemos usar resultados de chamadas já feitas durante a rotina de uma função recursiva?

*Dica: Relembre o que foi feito na APS 3.*

:::Gabarito
Podemos utilizar uma matriz n x W para armezanar o resultado das chamadas de ```c knapsack()```! Essa estratégia é conhecida como **memoização**.   
:::
???

??? Checkpoint
Qual é a maneira mais adequada de inicializar uma matriz para esse problema? 

*Dica: Pense em como saber se a célula da matriz já foi preenchida.*

:::Gabarito
Precisamos iniciar a matriz com valores inválidos para a mochila, para que a função ao ver que a matriz n x W possui um valor inválido saiba que aquela combinação de n e W é inédita. Para o caso do problema da mochila, a mochila não pode ter valores negativos, então -1 pode ser utilizado como valor inicial para a matriz. 
:::
???



Programação Dinâmica
--------------------

Ufa! Conseguimos resolver o problema das várias chamadas repetidas utilizando uma matriz *cache*. Mas pera aí, se a função ```c knapsack()``` existe apenas para preencher uma matriz n x W, podemos utilizar uma estratégia velha conhecida para preencher essa matriz. Um loop iterativo!

Esse método de transformar problemas recursivos em iterativos é conhecido como **programação dinâmica**. Ao invés de resolver o problema de maneira recursiva, vamos resolvê-los de maneira sequencial, utilizando o que já foi calculado para obter o resultado atual. A estratégia continua basicamente a mesma: analisar se o maior valor é atingido colocando ou não o item atual na mochila.  

Para uma matriz **n x W**, cada linha **n** representa uma quantidade de itens analisados, e cada coluna de **zero até W**, uma capacidade para a mochila, e cada célula o **melhor valor** que cabe na mochila para aquela combinação n e W! Vamos considerar como podemos preencher essa matriz considerando que ao contrário da abordagem recursiva, estamos resolvendo o problema de baixo para cima.

??? Checkpoint
Nos casos em que a capacidade da mochila (**W**) é zero e nos casos em que não temos itens a serem analisados (**n = 0**) qual deverá ser o valor da mochila? O que esses casos representavam na solução recursiva do problema?
::: Gabarito
São situações em que a mochila não comporta nenhum item, por não termos nenhum item para ser analisado ou pela capacidade da mochila ser zero, sendo assim o valor da mochila para esses casos é **zero**. 

São os mesmos casos considerados na **base da recursão!**

:base_matriz
:::
???

??? Checkpoint
Ainda pensando sobre como preencher a matriz, vamos considerar o caso em que o item não cabe na mochila. Qual o valor da mochila para esse caso? 

Como podemos usar a matriz para descobrir esse valor?

*Dica: Assim como o caso anterior, a ideia por trás é muito semelhante ao o que é feito no algoritmo recursivo.*
::: Gabarito
O valor da mochila para esse caso é o melhor valor possível para a mochila desconsiderando o item atual.

E como estamos preenchendo a matriz de **baixo para cima** já sabemos que valor é esse, é justamente o melhor valor possível determinado até então para esse valores de n e W, que está na célula n - 1 e W.

:nao_cabe
:::
???

??? Checkpoint
E como você já deve ter adivinhado: Qual o valor da mochila para o caso em que o item cabe na mochila?

Como podemos usar a matriz para descobrir esse valor?

*Dica: pense em como acessar o valores de diferentes capacidades da mochila.*

::: Gabarito
O valor da mochila é o maior valor dentre as duas opções a seguir: a melhor combinação vista até então sem o item, a melhor combinação dos itens vistos até então com o item atual.

E assim como na abordagem recursiva para descobrir a resposta nós vamos considerar duas opções: colocar ou não o item na mochila. 

Caso não colocássemos, vamos considerar o maior valor possível para aquela capacidade. Esse valor está na célula com n - 1 e W. 

Caso colocássemos, vamos considerar a soma do maior valor possível para a mochila que cabe o item com o próprio valor do item. O maior valor possível para uma mochila que cabe o item está na célula n - 1 e W - peso do item. Ai está o pulo do gato da nossa matriz!

O novo valor da célula será o maior valor dentre essas duas opções. 

:item_cabe
:::
???

Agora vamos conferir se estamos entendendo como preencher essa matriz!

??? Checkpoint
Preencha as duas últimas linhas da matriz a seguir:

![](cp_matriz.png)
::: Gabarito

![](cp_matriz_gabarito.png)
:::
???

Podemos resumir o processo de preenchimento da matriz da seguinte forma:

:dinamico

<!-- Animação de preencher a matriz -->

Agora já podemos escrever uma versão de ```c knapsack()``` utilizando programação dinâmica!

```c
int knapsack(int valores[], int pesos[], int n, int W) {
    int M[n + 1][W + 1];
    for (int i = 0; i <= n; i++) {
        for (int w = 0; w <= W; w++) {
            if (i == 0 || w == 0) {
                M[i][w] = 0;
            } else if (w >= pesos[i - 1]) {
                M[i][w] = max(M[i - 1][w], valores[i - 1] + M[i - 1][w - pesos[i - 1]]);
            } else {
                M[i][w] = M[i - 1][w];
            }
        }
    }
    return M[n][W];
}
```
Além de trocar a abordagem recursiva pela abordagem iterativa, não precisamos inicializar a matriz M com valores negativos!

Legal, conseguimos escrever um algoritmo de programação dinâmica para o problema da mochila! Mas será que depois de todo esse trabalho a complexidade temporal do nosso algoritmo realmente ficou melhor?

??? Checkpoint
Calcule a complexidade ***O*** da solução de programação dinâmica usando as técnicas vistas em aula.
::: Gabarito
Estimar as quantidades de iterações do loop externo em função de n:
```txt
Quantidade de iterações do loop externo (x):
-------------------------------------------
Contador começa de 0 e aumenta em 1 enquanto for menor ou igual a n.

Depois de x-1 iterações, a condição ainda vale.
0 + (x - 1) <= n
x - 1 <= n
x <= n + 1

x = O(n), ou seja, x <= c_x n
``` 

Estimar a quantidade de iterações do loop interno em função de W

```txt
Quantidade de iterações do loop interno (y):
-------------------------------------------
Contador começa de 0 e aumenta em 1 enquanto for menor ou igual a W.

Depois de y-1 iterações, a condição ainda vale.
0 + (y - 1) <= W
y - 1 <= W
y <= W + 1

y = O(W), ou seja, y <= c_y W
``` 

O loop interno é repetido x vezes. Como a quantidade de iterações do loop interno não varia, a complexidade é dada pela multiplicação entre a complexidade do loop interno com a complexidade do loop externo. Assim, a complexidade do algoritmo é **$O(n \cdot W)$**! 

:::
???