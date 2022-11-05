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


[comment]: <> (Imagem das áreas)

O primeiro pensamento do estudante foi de estudar as duas maiores áreas em relação a pontução. Assim, ele estudaria X e Y que consumiriam 5 horas de estudo e lhe garantiriam 6 pontos na prova. 

[comment]: <> (Imagem da seleção dessa opção)

??? Checkpoint 
Você deve ter percebido que o Fernando subestimou o problema de planejar o seus estudos. Qual é a melhor maneira que ele pode combinar as matérias para que possa estudar a maior combinação de pontos possíveis nas 6 horas que ele tem disponível?

::: Gabarito
Para maximizar os seus estudos Fernando deveria levar em conta opções fora as de maior valor! Assim chegaria que a melhor opção é estudar X, Y, e Z. 

[comment]: <> (Imagem da seleção da opção correta)
:::

???

Para a sorte do Fernando, o seu amigo Pedro que está no quinto semestre percebeu que seu dilema era muito relacionado a um problema que ele estava estudando na matéria de Desafios da Programação, **o problema da mochila**! 

Fernando, um novo estudante!
---------------

Com a ajuda de Pedro, Fernando conseguiu passar na prova que mal havia estudado. Percebendo o quanto seu tempo de estudo foi otimizado ao utilizar do algorítimo, ele decidiu por usa-lo novamente para organizar seus estudos semanais. 

De segunda a sexta Fernando tem disponíveis 3 horas por dia para estudar os conteúdos das suas 5 matérias da faculdade. No final de todo seu planejamento, ele teria 35 conteudos para serem estudados em 45 horas, visando as provas finais que estão a três semanas de distância. 

Sendo assim, pediu que seu amigo o explica-se como ele resolveu o problema da mochila para a situação anterior:

[comment]: <> (animação do slide)

A resolução de Pedro para o problema é conhecida como **busca exaustiva!**

Busca exaustiva
---------------

Vamos começar a pensar em como traduzir essa resolução para código. Precisamos escrever uma função que recebe como entrada os itens e a capacidade da mochila e nos devolve o maior valor possível que cabe na mochila para aqueles itens. Lembrando que cada item possui um valor e um peso. 

??? Checkpoint 
Você deve ter percebido que o Fernando subestimou o problema de planejar o seus estudos. Qual é a melhor maneira que ele pode combinar as matérias para que possa estudar a maior combinação de pontos possíveis nas 6 horas que ele tem disponível?

::: Gabarito
Para maximizar os seus estudos Fernando deveria levar em conta opções fora as de maior valor! Assim chegaria que a melhor opção é estudar X, Y, e Z. 

[comment]: <> (Imagem da seleção da opção correta)
:::

???













