Claro! Vou converter o seu arquivo LaTeX para Markdown. Aqui está o conteúdo convertido:

---

# 1. Técnica de troca de chaves Diffie-Hellman

Dado que \(q = 71\) e \(\alpha = 7\):

## (a) Se o usuário A tem chave privada \(X_A = 5\), qual é a chave pública de A, \(Y_A\)?

A chave pública \(Y_A\) é calculada como:

\[ Y_A = \alpha^{X_A} \mod q \]

Substituindo os valores:

\[ Y_A = 7^5 \mod 71 = 16807 \mod 71 = 56 \]

Portanto, \(Y_A = 56\).

## (b) Se o usuário B tem chave privada \(X_B = 12\), qual é a chave pública de B, \(Y_B\)?

A chave pública \(Y_B\) é calculada como:

\[ Y_B = \alpha^{X_B} \mod q \]

Substituindo os valores:

\[ Y_B = 7^{12} \mod 71 = 13,841,287,201 \mod 71 = 64 \]

Portanto, \(Y_B = 64\).

## (c) Qual é a chave secreta compartilhada?

A chave secreta compartilhada \(K\) é calculada como:

\[ K = Y_B^{X_A} \mod q \quad \text{ou} \quad K = Y_A^{X_B} \mod q \]

Usando \(Y_B^{X_A} \mod q\):

\[ K = 64^5 \mod 71 = 1073741824 \mod 71 = 18 \]

Portanto, a chave secreta compartilhada é \(K = 18\).

---

# 2. Esquema ElGamal com \(q = 71\) e \(\alpha = 7\)

## (a) Se B tem chave pública \(Y_B = 3\) e A escolheu um inteiro aleatório \(k = 2\), qual é o texto cifrado de \(M = 30\)?

Cálculo do texto cifrado:

\[ C_1 = \alpha^k \mod q = 7^2 \mod 71 = 49 \]

\[ C_2 = M \times Y_B^k \mod q = 30 \times 3^2 \mod 71 = 30 \times 9 \mod 71 = 270 \mod 71 = 57 \]

Portanto, o texto cifrado é \((C_1, C_2) = (49, 57)\).

## (b) Se A, então, selecionar um valor diferente de \(k\), de modo que a codificação de \(M = 30\) seja \(C = (59, C_2)\), qual é o inteiro \(C_2\)?

Para \(C_1 = 59\), precisamos encontrar \(k\) tal que:

\[ C_1 = 7^k \mod 71 = 59 \]

Neste caso, \(k = 11\) satisfaz \(7^{11} \mod 71 = 59\).

Agora, calcule \(C_2 = M \times Y_B^k \mod q\):

\[ C_2 = 30 \times 3^{11} \mod 71 = 30 \times 20 \mod 71 = 600 \mod 71 = 31 \]

Portanto, \(C_2 = 31\).

---

# 3. Curvas elípticas

Demonstre que as duas curvas elípticas na Figura 10.4 satisfazem, cada uma, as condições para um grupo sobre os números reais.

*(Para uma demonstração completa, você precisaria da descrição ou imagem específica das curvas mencionadas.)*

---

# 4. Verificação de ponto em curva elíptica

Verifique se o ponto \((4, 7)\) pertence à curva elíptica \(y^2 = x^3 - 5x + 5\) sobre os números reais.

Substituindo \(x = 4\) e \(y = 7\) na equação da curva:

\[ y^2 = 7^2 = 49 \]

\[ x^3 - 5x + 5 = 4^3 - 5 \times 4 + 5 = 64 - 20 + 5 = 49 \]

Como \(49 = 49\), o ponto \((4, 7)\) está na curva.

---

Se precisar de mais alguma ajuda ou