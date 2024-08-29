# Principais elementos de um criptossistema de chave pública

- **Chave Pública**: Usada para encriptação e é conhecida por todos.
- **Chave Privada**: Mantida em segredo e usada para decriptação.
- **Algoritmo de Encriptação**: Um procedimento que usa a chave pública para transformar uma mensagem em texto cifrado.
- **Algoritmo de Decriptação**: Um procedimento que usa a chave privada para reverter o texto cifrado de volta à mensagem original.
- **Algoritmo de Geração de Chaves**: Produz o par de chaves pública e privada.

## Papéis da chave pública e privada

- **Chave Pública**: Usada para encriptar mensagens. Por exemplo, se Alice deseja enviar uma mensagem segura para Bob, ela usaria a chave pública de Bob para encriptar a mensagem. Somente a chave privada correspondente, que Bob possui, pode decriptar a mensagem.
- **Chave Privada**: Usada para decriptar mensagens encriptadas com a chave pública correspondente. Bob usaria sua chave privada para decriptar a mensagem enviada por Alice. 

### Exemplo:

- Alice encripta "HELLO" usando a chave pública de Bob. O texto cifrado só pode ser decriptado pela chave privada de Bob.

## Requisitos para criptossistemas de chave pública serem seguros

- **Inviabilidade Computacional**: Não deve ser viável calcular a chave privada a partir da chave pública em tempo razoável.
- **Segurança Baseada em Problemas Matemáticos**: A segurança deve ser fundamentada em problemas matemáticos difíceis de resolver, como a fatoração de números grandes (exemplo do RSA).
- **Confidencialidade**: Deve garantir que, sem a chave privada, o texto cifrado não pode ser revertido ao texto original.
- **Integridade e Autenticidade**: Deve permitir a verificação de que a mensagem não foi alterada e que o remetente é autêntico.

## Procedimento eficiente para escolher um número primo

- **Teste de Primalidade**: Um procedimento comum é usar um algoritmo probabilístico como o Teste de Miller-Rabin, que verifica se um número é primo com alta probabilidade. Outro método é o Crivo de Eratóstenes, usado para encontrar todos os números primos até um determinado limite.
- **Escolha Aleatória**: Começa-se com um número aleatório grande, verificando se é ímpar e aplicando um teste de primalidade. Se o número não for primo, incrementa-se e testa-se o próximo número.

## Esquema de encriptação/decriptação com as tabelas M1, M2 e M3

### Encriptação:

1. Encontra-se o valor correspondente a `k` em M1, resultando em `x`.
2. Usando `x` e a mensagem `p`, localiza-se `z` em M2.
3. Usando `z` e `k`, encontra-se o valor final `p'` em M3, que é a mensagem encriptada.

### Decriptação:

1. Usando o valor cifrado `p'`, encontra-se `z` em M3.
2. Usando `z`, encontra-se `x` em M2.
3. Finalmente, usando `x`, encontra-se `k` em M1.

### Preenchimento da matriz M3:

Para satisfazer a condição \( f_3(f_2(f_1(k), p), k) = p \), podemos construir M3 de forma a que, para qualquer par `(z, k)`, o valor de `p` seja obtido corretamente. Um exemplo para M3 seria:


| 4 | 5 | 3 | 2 | 1 |

| 2 | 4 | 1 | 5 | 3 |

| 1 | 2 | 5 | 4 | 3 |

| 3 | 1 | 4 | 5 | 2 |

| 5 | 3 | 2 | 1 | 4 |


## Exemplo (a):

- \( p = 3 \), \( q = 11 \), \( e = 7 \), \( M = 5 \).
- Calcule \( n = pq = 33 \) e \( \phi(n) = (p - 1)(q - 1) = 20 \).
- Calcule \( d \) tal que \( ed \equiv 1 \mod \phi(n) \).
- \( C = M^e \mod n = 5^7 \mod 33 = 14 \).

### Decriptação:

- \( M = C^d \mod n \) (usando \( d \) calculado).

## Intercepção de texto cifrado em RSA:

Para interceptar, seria necessário tentar fatorar \( n \) para descobrir \( p \) e \( q \), e então calcular \( \phi(n) \) e \( d \). Sem essa informação, decriptar a mensagem diretamente a partir do texto cifrado é considerado inviável com os métodos criptográficos atuais.
