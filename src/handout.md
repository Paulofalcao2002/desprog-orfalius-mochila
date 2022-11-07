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

Esse é o Fernando, um estudante do 4o semestre de engenharia do Insper. Fernando deixou para ultima hora estudar para sua prova final de eletromagnetismo, mas como sabemos essa é uma matéria muito vasta e com diversos conteúdos, sendo impossivel estudar tudo nas 6 horas que ele tinha disponível.

Tendo isso em vista, Fernando pensou em uma ideia para tentar se salvar, que consistia em separar toda a máteria em áreas de estudo. Para cada área, Fernando analisou quanto tempo ele demoraria para aprender e a média de quantos pontos cada conteudo correspondeu nas últimas cinco provas dos semestres passados. Com esses dados em mãos, Fernando agora só precisa encontrar a melhor combinação de áreas para estudar. 


<div style="height:300px;display:flex;justify-content:space-evenly;align-items:flex-start;">
    <img src="areas.png" alt="áreas de estudo" height="280" width="80%" />
</div>


O primeiro pensamento do estudante foi de estudar as duas maiores áreas em relação a pontução. Assim, ele estudaria Ondulatória e Leis de Maxwell que consumiriam 5,5 horas de estudo e lhe garantiriam 6 pontos na prova. 

<div style="height:300px;display:flex;justify-content:space-evenly;align-items:flex-start;">
    <img src="1escolha.png" alt="primeira escolha" height="280" width="80%" />
</div>


??? Checkpoint 
Você deve ter percebido que o Fernando subestimou o problema de planejar o seus estudos. Qual é a melhor maneira que ele pode combinar as matérias para que possa estudar a maior combinação de pontos possíveis nas 6 horas que ele tem disponível?

::: Gabarito
Para maximizar os seus estudos Fernando deveria levar em conta opções fora as de maior valor! Assim chegaria que a melhor opção é estudar Eletrodinâmica, Laboratórios e Leis de Maxwell. 

<div style="height:300px;display:flex;justify-content:space-evenly;align-items:flex-start;">
    <img src="solucao.png" alt="solucao" height="280" width="80%" />
</div>
:::

???

Para a sorte do Fernando, o seu amigo Pedro que está no quinto semestre percebeu que seu dilema era muito relacionado a um problema que ele estava estudando na matéria de Desafios da Programação, **o problema da mochila**! 

Curioso, Fernando pediu para que seu amigo explicasse como resolveu o problema:

<!-- Fernando, um novo estudante!
---------------

Com a ajuda de Pedro, Fernando conseguiu passar na prova que mal havia estudado. Percebendo o quanto seu tempo de estudo foi otimizado ao utilizar do algorítimo, ele decidiu por usa-lo novamente para organizar seus estudos semanais. 

De segunda a sexta Fernando tem disponíveis 3 horas por dia para estudar os conteúdos das suas 5 matérias da faculdade. No final de todo seu planejamento, ele teria 35 conteudos para serem estudados em 45 horas, visando as provas finais que estão a três semanas de distância. 

Sendo assim, pediu que seu amigo o explica-se como ele resolveu o problema da mochila para a situação anterior: -->

[comment]: <> (animação do slide)

A resolução de Pedro para o problema é conhecida como **busca exaustiva!**

Busca exaustiva
---------------

Vamos começar a pensar em como traduzir essa resolução para código. Precisamos escrever uma função que recebe como entrada os itens e a capacidade da mochila e nos devolve o maior valor possível que cabe na mochila para aqueles itens. Lembrando que cada item possui um valor e um peso. 

??? Checkpoint 
Considerando que estamos escrevendo uma função em C, como podemos representar os itens, dado que cada item possui um par valor e peso?

::: Gabarito
A maneira mais simples seria dois arrays, um para os valores, outro para os pesos.
``` c
int valores[] = {1, 2, 3, 4};
int pesos[] = {1, 2, 3, 4};
```
Para o item **n**, o seu valor estaria em ```c valores[n - 1]``` e seu peso em ```c pesos[n - 1]```.
:::

???

Com isso, já temos todas as informações necessárias sobre quais são os argumentos dessa função e o que ela retorna.

??? Checkpoint
Escreva o cabeçalho da função ```c knapsack()```
::: Gabarito
```c 
int knapsack(int valores[], int pesos[], int n, int W);
```
:::
???

Vamos começar a pensar no conteudo da função ```c knapsack()```. Para a solução que queremos implementar vamos utilizar de **chamadas recursivas**!

[comment]: <> (imagem da animação)

??? Checkpoint 
Como seria a chamada recursiva de ```c knapsack()``` caso **não** adicionássemos o item **n** na nossa mochila? E casos adicionássemos?

::: Gabarito
```c 
// Caso não adicionássemos
knapsack(valores, pesos, n - 1, W);

// Caso adicionássemos
knapsack(valores, pesos, n - 1, W - pesos[n - 1]);
```

Quando adicionamos o item atual na mochila a capacidade atual da mochila é subtraida do peso do item atual. 
:::
???

??? Checkpoint 
Escreva o passo de ```c knapsack()```.

Dica: Pense sobre o retorno das chamadas de ```c knapsack()``` e o que precisa ser feito com esse valores.

::: Gabarito
```c 
int knapsack(int valores[], int pesos[], int n, int W) {
    // ??? Base da recursão

    // Passo da recursão
    int sem_adicionar = knapsack(valores, pesos, n - 1, W);

    int adicionando = valores[n - 1] + knapsack(valores, pesos, n - 1, W - pesos[n - 1]);

    if (sem_adicionar > adicionando) {
        return sem_adicionar;
    }
    return adicionando;
}
```

Para uma solução com melhor legibilidade poderiamos definir uma função ```c max()``` que devolve o maior valor entre dois inteiros. Além disso, para evitar chamadas recursivas desnecessárias podemos verificar se o item **n** cabe ou não na mochila.

```c 
int max(int a, int b) {
    return a > b ? a : b;
}

int knapsack(int valores[], int pesos[], int n, int W) {
    // ??? Base da recursão

    // Passo da recursão
    // Testa as duas possibilidades somente se o item cabe na mochila
    if (W >= pesos[n - 1]) {
        return max(knapsack(valores, pesos, n - 1, W), 
        valores[n - 1] + knapsack(valores, pesos, n - 1, W - pesos[n - 1]));
    }

    // Se não verifica o próximo item
    return knapsack(valores, pesos, n - 1, W);

}
```
:::

???

Ainda temos um problema, a função que escrevemos não tem nenhuma base, o que levaria a uma recursão infinita! 

??? Checkpoint
Escreva a base da função ```c knpasack() ```

Dica: Analise as chamadas recursivas dos checkpoints anteriores para saber o que está sendo mudado a cada chamada 

:::Gabarito 
```c
int knapsack(int valores[], int pesos[], int n, int W) {
    // Caso não tenha itens a serem colocados na mochila retornamos
    // zero!
    if (n == 0) {
        return 0;
    }
    // Caso não tenha capacidade na mochila não conseguimos adicionar
    // item nenhum! 
    if (W == 0) {
        return 0;
    }

    // Passo da recursão
    
}
```

Assim a versão final de ```c knapsack()``` é:


```c
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
:::
???

Finalmente temos um algoritmo que pode solucionar o problema da mochila! Mas será que essa é a melhor solução possível? 

??? Checkpoint
Usando as estratégias vistas em aula, calcule a complexidade do algoritmo da **busca exaustiva** utilizando a notação **O**!


:::Gabarito
Passo A: Escrever a recorrência
```c
            /
           | 1             se n ou W == 0;
k(n, W) = <
           | k(n - 1, W) + k(n - 1, W - a)    se n ou W > 0;
            \
```
OBS: Como a notação O leva sempre em consideração o pior caso possível, para obtermos o maior número de chamadas recursivas para a função ```c knapsack()``` "a" teria que ser igual a **zero**! Por isso, no pior caso a função sempre faz duas chamadas recursivas já que sempre entra no ```c if(W >= pesos[n - 1])```.

Assim o parâmetro W pode ser desconsiderado para esse calculo: 
```c
         /
        | 1           se n == 0;
k(n) = <
        | 2k(n - 1)   se n > 0;
         \
```

Passo B: Desenhe a árvore de recursão:

<!-- imagem da árvore -->

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

O problema da busca exaustiva
-----------------------------

Como vocês devem imaginar após calcular a complexidade da **busca exaustiva** esse não deve ser o melhor algoritmo para resolver o problema da mochila. O principal motivo para essa complexidade alta é a quantidade enorme de **chamadas repetidas** que são feitas ao longo de uma rotina:

<!-- Animação mostrando as chamadas repetitivas -->

??? Checkpoint
Existe algum jeito que podemos usar resultados de chamadas já feitas durante a rotina de uma função recursiva?

Dica: Relembre o que foi feito na APS 3

:::Gabarito
Podemos utilizar uma matriz n x W para armezanar o resultado das chamadas de ```c knapsack()```! Essa estratégia é conhecida como **memoização**. 
:::
???

??? Checkpoint
Qual é a maneira mais adequada de inicializar uma matriz para esse problema? 

:::Gabarito
Precisamos iniciar a matriz com valores inválidos para a mochila, para que a função ao ver que a matriz n x W possui um valor invalido saiba que aquela combinação de n e W é inédita. Para o caso do problema da mochila, a mochila não pode ter valores negativos então -1 pode ser utilizado como valor inicial para a matriz. 
:::
???

??? Checkpoint
Modifique a função da busca exaustiva para que ela passe a utilizar a estratégia discutida nos checkpoint anteriores.

:::Gabarito
```c
int knapsack(int valores[], int pesos[], int n, int W, int memo[][]) {
    if (memo[n][W] != -1) {
        return memo[n][W];
    }
    if (n == 0 || W == 0) {
        return 0;
    }

    if (W >= pesos[n - 1]) {
        memo[n][W] = max(knapsack(valores, pesos, n - 1, W), 
        valores[n - 1] + knapsack(valores, pesos, n - 1, W - pesos[n - 1]));
        return memo[n][W];
    }

    memo[n][W] = knapsack(valores, pesos, n - 1, W)
    return memo[n][W];
}
```
:::
???

Programação Dinâmica
--------------------

Ufa! Conseguimos resolver o problema das várias chamadas repetidas utilizando uma matriz cache. Mas pera ai, se a função ```c knapsack()``` existe apenas para preencher uma matriz n x W, podemos utilizar uma estratégia velha conhecida para preencher essa matriz. Um loop iterativo!

Esse método de transformar problemas recursivos em iterativos é conhecido como **programação dinâmica**. Ao invés de resolver o problema de maneira recursiva vamos resolve-los de maneira sequencial, utilizando o que já foi calculado para calcular o resultado atual. A estratégia continua basicamente a mesma: analisar se o maior valor é atingido colocando ou não o item atual na mochila. 

Cada linha da matriz representa uma quantidade **n** de itens analisados, cada coluna uma capacidade que vai de **zero até W** e nas células serão guardados os maiores valores possiveis para aquela combinação n e W. A tabela vai sendo preenchida conforme a animação a seguir:

<!-- Animação de preencher a matriz -->

??? Checkpoint
Agora que você já sabe como é feito preenchimento da matriz, escreva uma versão de ```c knapsack()``` utilizando programação dinâmica!
::: Gabarito
Além de trocar a abordagem recursiva pela abordagem iterativa, não precisamos inicializar a matriz memo com valores negativos!
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
:::
???

Legal, conseguimos escrever um algoritmo de programação dinâmica para o problema da mochila! Mas será que depois de todo esse trabalho a complexidade temporal do nosso algoritmo realmente ficou melhor?

??? Checkpoint
Calcule a complexidade ***O*** da solução de programação dinâmica usando as técnicas vistas em aula.
:::
Estimar as quantidade de iterações do loop externo em função de n:
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