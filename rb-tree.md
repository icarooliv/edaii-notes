# Árvore vermelha e preta

## Regras

### 1 Todo nó é preto ou vermelho

### 2 Raiz é sempre preta

### 3 Toda folha Null é preto

### 4 Todo caminho de raiz-folha tem o mesmo número de nós PRETOS

### 5 Nenhum caminho pode ter dois nós VERMELHOS consecutivos (se um nó é vermelho, os filhos são pretos)

## Inserção

### - Novas inserções são sempre vermelhas

## Rebalanceamento

### 1 Tio Preto -> rotaciona

### 2 Tio Vermelho -> troca de cor

## Exemplos

### Exemplo 1

Dada a situação:

```
       3(b)
1(r)           5(r)
                        7(r)
```

- Ocorre uma violação da regra 5

Logo, segundo a orientação 2 do Balanceamento, deve-se fazer uma troca de cor.

```
        3(r)
1(b)            5(b)
                        7(r)
```

- Violação da regra 2

Em seguida, deve-se voltar a raiz para a cor preta.

```
        3(b)
1(b)            5(b)
                        7(r)
```

- Árvore RB corretamente montada

### Exemplo 2 - Adicionando número 6

Este exemplo trata de uma inserção na árvore do Exemplo 1. Inserindo o **valor 6**, tem-se:

```
              3(b)
   1(b)                5(b)
nil    nil          nil      7(r)
                          6(r)  nil
```

- Existem dois nós vermelhos consecutivos (7) e (6): infração da regra 5.

Verificando que o tio de (6), o nó (nil), filho de (5), é preto, pois respeita a regra 3, deve-se fazer uma rotação à esquerda.

```
              3(b)
   1(b)                  6(r)
nil    nil          5(b)      7(r)
```

- Existem dois nós vermelhos consecutivos (6) e (7): infração da regra 5.

Após, para corrigir esta infração, deve-se corrigir a cor dos nós (6), (5) e (7). O nó pai é da cor preta e os filhos, vermelha.

```
              3(b)
   1(b)                  6(b)
nil    nil          5(r)      7(r)
```

- Inserção e balanceamento finalizados. A árvore RB respeita todas as regras.

### Exemplo 3 - Adicionando número 8

Este exemplo trata de uma inserção na árvore do Exemplo 2. Inserindo o **valor 8**, tem-se:

```
              3(b)
   1(b)                  6(b)
nil    nil          5(r)      7(r)
                                    8(r)
```

- Infração da regra 5: os nós vermelhos (7) e (8) são consecutivos.

Para corrigir esta infração, leva-se em conta que (1), o tio de (8), é vermelho. Portanto, deve-se fazer uma troca de cores nos nós problemáticos: (6), (5) e (7). O pai é vermelho e os filhos, pretos.

```
              3(b)
   1(b)                  6(r)
nil    nil          5(b)      7(b)
                                    8(r)
```

- Árvore não infringe nenhuma regra e o processo de inserção termina.

### Exemplo 4 - Inserção de 9

Este exemplo trata de uma inserção na árvore do Exemplo 3. Inserindo o **valor 9**, tem-se:

```
              3(b)
   1(b)                  6(r)
nil    nil          5(b)          7(b)
                            (nil)       8(r)
                                             9(r)
```

- Infração da regra 5: dois nós vermelhos consecutivos, (8) e (9).

Para corrigir essa violação, leva-se em conta que (nil), filho de (7) e o tio de (9), é preto. Deve-se, portanto, fazer uma rotação à esquerda.

```
              3(b)
   1(b)                   6(r)
nil    nil          5(b)          8(r)
               (nil)    (nil)  7(b)    9(r)
```

- Infração da regra 5. Os nós (6), (8) e (9) são vermelhos e consecutivos.

Deve-se reordenar a cor dos nós, segundo a regra 5. O pai é preto e os filhos são vermelhos.

```
              3(b)
   1(b)                  6(r)
nil    nil          5(b)        8(b)
                            7(r)    9(r)
```

- A árvore obedece todas as regras e o processo de inserção é finalizado.

###
