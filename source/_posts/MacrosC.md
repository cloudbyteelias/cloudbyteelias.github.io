---
layout: welcome
title: 0x1-Trabalhando com macros parte 1 [Linguagem C]
date: 2021-02-17 13:07:23
tags: Linguagem C
---





## Sobre macros
<article>
Macros são muito úteis, mas como qualquer coisa deve ser usada corretamente, alguns padrões são utilizados na hora da sua declaração como sempre usar letras maiúsculas, uma ideia não muito legal é usar macros para declaração de tipos.
</article>

Exemplo a não ser seguido:

```c
#define version "1.1.0"
#define UINT unsigned int*
UINT t;
```
Alternativa:

```c
#define VERSION "1.1.0"
typedef unsigned int UINT;
UINT t;
```
<article>
Como podemos ver macros são definidos por #define,na fase de pré-processamento o valor descrito em #define
é trocado pela sua nomenclatura ou seja em #define VERSION "1.10" representando,"1.10" como VERSION isso
efetuado por uma etapa denominada expansão de macro.
</article>

## Praticando um pouco:
Exemplo simples executando operações básicas:

```C
#include <stdlib.h>
#include <stdio.h>

#define ADD(x,y) x + y
#define SUB(x,y) x - y
#define MUL(x,y) x * y
#define DIV(x,y) x / y


int main(int argc, char const *argv[]){
    
    printf ("[%d] [%d] [%d] [%d]\n",ADD(5,5),SUB(10,5),MUL(5,5),DIV(10,2));
     
    return EXIT_SUCCESS;
}

```
Sua saida será:

```sh
[10] [5] [25] [5]

```
<article>
Exemplo mostra a execução de uma macro variada ou variadic macro, o mesmo pode ter N, argumentos, este recurso é extremamente útil.
Observe o próximo exemplo:
</article>

```c++
#include <stdlib.h>
#include <stdio.h>
#include <string.h>

#define VERSION     "0.1"
#define NET_ERROR   "Sem internet"
#define AUTH_ERROR  "Erro de autenticação"


#define LOG_ERROR(log, ...) \
 fprintf(stderr, log, __VA_ARGS__)


int main(int argc, char const *argv[]){

    int x = 5;

    if(x <= 5){
        LOG_ERROR("NÂO SUPORTADO [%s]\n", NET_ERROR);
    }



    return EXIT_SUCCESS;
}

```
<article>
Bacana não é? Estamos passando uma macro variada buscando outra macro com erros pré definidos, ou seja, se a condição
não satisfazer o macro LOG_ERROR apresentara a mensagem de escolha identificada pelo macro NET_ERROR, imagine
que ocorreu um erro de conexão e essa mensagem é responsável por apresentar para o usuário a situação atual, graças a nossa
__VA_ARGS__ que é a responsável por adquirir nossa segunda macro como parâmetro.
</article>


## Considerações finais:

<article>
Obrigado por chegar até aqui,
faça bom proveito do conteúdo. Agora fique com a foto de um gato fofo.
</article>


## Código Fonte:

https://github.com/cloudbyteelias/Kernel-Panic-Sources/tree/main/C/Macros



![alt text](https://i.pinimg.com/originals/84/48/c8/8448c8666642b94395a81945bf2af015.jpg "Title")






