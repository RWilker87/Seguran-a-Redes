# Respostas

## 1. Por que \( \text{mdc}(n, n + 1) = 1 \) para dois inteiros consecutivos \( n \) e \( n + 1 \)?

Dois números consecutivos \( n \) e \( n + 1 \) não têm divisores comuns além de 1. Qualquer divisor comum a ambos deve dividir a diferença \( (n + 1) - n = 1 \). Portanto, o máximo divisor comum (mdc) entre \( n \) e \( n + 1 \) é 1.

## 2. Usando o Teorema de Fermat, encontre \( 3^{201} \mod 11 \):

Pelo Teorema de Fermat, se \( p \) é primo e \( a \) não é divisível por \( p \), então \( a^{p-1} \equiv 1 \mod p \). Aqui, \( p = 11 \), então:

\[ 
3^{10} \equiv 1 \mod 11 
\]

Como \( 201 \mod 10 = 1 \), temos:

\[
3^{201} = 3^{200+1} = (3^{200}) \times 3 \equiv 1 \times 3 \equiv 3 \mod 11
\]

Portanto, \( 3^{201} \equiv 3 \mod 11 \).

## 3. Usando o Teorema de Fermat, encontre um número \( a \) entre 0 e 72, tal que \( a \) seja congruente a 9794 módulo 73:

Pelo Teorema de Fermat, para \( p = 73 \) e \( a \):

\[
a^{72} \equiv 1 \mod 73
\]

Como \( 9794 \mod 73 = 10 \), precisamos encontrar:

\[
a \equiv 10 \mod 73
\]

Portanto, \( a = 10 \).

## 4. Use o Teorema de Euler para encontrar um número \( a \) entre 0 e 9, tal que \( a \) seja congruente a \( 7^{1000} \mod 10 \):

Primeiro, calcule \( \phi(10) = 4 \). Pelo Teorema de Euler:

\[
7^4 \equiv 1 \mod 10
\]

Então:

\[
7^{1000} = 7^{4 \times 250} \equiv 1^{250} \equiv 1 \mod 10
\]

Portanto, \( 7^{1000} \equiv 1 \mod 10 \), ou seja, o último dígito de \( 7^{1000} \) é 1.

## 5. Use o Teorema de Euler para encontrar um número \( x \) entre 0 e 28, com \( x^{85} \) congruente a 6 módulo 35:

Temos \( \phi(35) = \phi(5) \times \phi(7) = 4 \times 6 = 24 \).

Assim, \( x^{24} \equiv 1 \mod 35 \), e \( 85 \mod 24 = 13 \), então:

\[
x^{85} \equiv x^{13} \equiv 6 \mod 35
\]

Testando \( x = 6 \):

\[
6^{13} \equiv 6 \mod 35
\]

Portanto, \( x = 6 \).

## 6. Por que \( \phi(n) \) é par para \( n > 2 \)?

Se \( n \) é maior que 2, ele deve ter ao menos um fator primo \( p \geq 2 \). Como \( \phi(n) \) é calculado considerando todos os números menores que \( n \) que são coprimos com \( n \), esses números sempre aparecerão em pares \( (x, n-x) \), exceto quando \( n \) é ímpar e \( x = \frac{n}{2} \). Como \( \phi(n) \) conta os elementos em pares, \( \phi(n) \) deve ser par.

## 7. Mostrar que 2047 é um pseudoprimo forte à base 2:

2047 pode ser fatorado como \( 2047 = 23 \times 89 \). O Teste de Miller-Rabin para base 2:

\[
2046 = 2 \times 1023
\]

\( 2^{1023} \equiv 1 \mod 2047 \), o que indica que 2047 passa no teste para a base 2, mesmo sendo composto. Assim, 2047 é um pseudoprimo forte à base 2.

## 8. Solucione para \( x \) no sistema de congruências:

- \( x \equiv 2 \mod 3 \)
- \( x \equiv 3 \mod 5 \)
- \( x \equiv 2 \mod 7 \)

Usando o Teorema Chinês do Resto:

Para \( x \equiv 2 \mod 21 \) (com \( 3 \times 7 = 21 \)):

\[
x = 21k + 2
\]

Substituindo na segunda congruência \( x \equiv 3 \mod 5 \):

\[
21k + 2 \equiv 3 \mod 5 \quad \text{ou} \quad k \equiv 1 \mod 5
\]

\( k = 5m + 1 \), então:

\[
x = 21(5m + 1) + 2 = 105m + 23
\]

Portanto:

\[
x \equiv 23 \mod 105
\]

**Solução final:** \( x = 23 \).
