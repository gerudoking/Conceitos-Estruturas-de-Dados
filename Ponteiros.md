## O que é um ponteiro?
Um ponteiro é uma variável que armazena um endereço de memória. Na linguagem C, uma variável ponteiro é
declarada(por exemplo) da maneira `int* A`, onde A é um ponteiro para uma área de memória que pode conter um inteiro.
O que torna a variável um ponteiro é o caractere `*` seguido ao tipo da variável durante sua declaração. É importante
notar que esse tipo de lógica pode ser aplicada a qualquer tipo de variável (ponteiro para float, ponteiro para caractere, etc.).
Um exemplo de código funcional em C que faz uso de ponteiros pode ser visto abaixo:

```
#include <stdio.h>
void main(){
  int x = 4;
  int* ponteiro;
  ponteiro = &x;
  printf("O endereço de X é: %d\n", *ponteiro);
}
```

O código acima vai imprimir a seguinte linha:

```
O endereço de X é: 4
```

Uma coisa importante para entender o código é o conceito de referência. O operador `&` em C é o operador de referência,
e com ele você pode obter o endereço de uma variável. No caso do código acima, atribuimos ao ponteiro de inteiro `ponteiro`
o endereço de `x`. Portanto, ao utilizarmos o operador de desreferência `*` em `ponteiro` como argumento da função `printf`,
obtemos o conteúdo de `ponteiro` e, por consequência, o conteúdo de `x`. Um fato que pode ser atestado através dessa afirmação
é: o caractere `*` possui mais de uma função. Além da função já citada no início do texto, se utilizado fora da declaração de uma
variável e de forma unária (operando apenas sobre uma variável) e a esquerda desta, temos o operador de desreferência ou de "conteúdo".
Basicamente, é dessa maneira que se recupera os valores que estão armazenados nas áreas de memória apontadas pelos ponteiros.


## Mais sobre ponteiros

Como exercício, veja o código de exemplo e diga se está correto:

```
float x = 3.14;
float* p = &x;
short d = 44;
short* q = &d;

p = q;
```

O código está errado. O porquê do código estar errado é que short e float são tipos diferentes de variável. Não somente isso, uma variável de cada um dos tipos ocupa um espaço diferente na memória. Em casos em que se quer atribuir a um ponteiro o valor apontado por outro ponteiro de tipos diferentes, a melhor solução seria fazer um **cast** do valor do segundo ponteiro, e atribuir esse valor como conteúdo do primeiro ponteiro.

## Vetores

Um vetor é, basicamente, uma variável que pode guardar múltiplos valores. Pode ser declarada(por exemplo) da maneira `int v[10]`. No caso, seria um vetor de inteiros com dez posições, que pode ter seus valores acessados via índice(o operador `[x]`, onde x é a posição que se deseja acessar no vetor). Vetores referenciam áreas de memória, portanto podem ser tratados como ponteiros.

Um segundo exercício para que você julgue se está certo ou errado:

```
short a[32];

for(int i = 0; i < 32; i++){
  *a++ = i*i;
}
```

O código parece confuso, mas está correto. Devido a precedência dos operadores de incremento e de desreferência, o incremento acontece antes de se obter o conteúdo de `a`. Isso significa que, basicamente, estamos iterando pelo vetor `a`, pois a cada iteração do loop, incrementa-se o endereço do ponteiro(o operador de incremento, ao ser aplicado sobre um ponteiro, o incrementa em uma quantidade igual ao tamanho de seu conteúdo). Como `a` é um vetor, o endereço passa a ser do segundo elemento de `a`(`a[1]`), e não mais do primeiro(`a[0]`). Logo em seguida, pegamos o conteúdo desse novo endereço e atribuimos a ele o valor de `i*i`.

## Referências
1. [Typecasting int pointer to float pointer](https://stackoverflow.com/questions/30276645/typecasting-int-pointer-to-float-pointer)
2. [C++ operator precedence](https://en.cppreference.com/w/cpp/language/operator_precedence)
