# Perguntas: Questões retiradas do livro-texto da disciplina.

## 1. Responda (de forma objetiva) as questões a seguir:
(a) **Quais são os elementos essenciais de uma cifra simétrica?**
- Texto claro
- Algoritmo de criptografia
- Chave secreta
- Texto cifrado

(b) **Quais são as duas funções básicas usadas nos algoritmos de encriptação?**
- Cifrar
- Decifrar

(c) **Qual é a diferença entre uma cifra de bloco e uma cifra de fluxo?**
- **Cifra de bloco**: Cifra dados em blocos de tamanho fixo.
- **Cifra de fluxo**: Cifra dados byte a byte.

(d) **Quais são as duas técnicas gerais para atacar uma cifra?**
- Criptoanálise
- Força bruta

(e) **Quais são os dois problemas com o one-time pad?**
- Necessidade de uma chave tão longa quanto a mensagem.
- Dificuldade de distribuir e manter a chave em segredo.

(f) **O que é uma cifra de transposição?**
- Uma cifra que reorganiza as posições dos caracteres na mensagem original de acordo com uma regra específica, sem alterar os caracteres em si.

(g) **O que é esteganografia?**
- Técnica de esconder informações dentro de outros arquivos ou mensagens, de modo que a presença da informação oculta não seja detectada.

## 2. Cifra de César Afim:
Uma generalização da cifra de César, conhecida como cifra de César afim, tem a seguinte forma: a cada letra de texto claro `p`, substitua-a pela letra de texto cifrado `C`:
\[ C = E([a, b], p) = (ap + b) \mod 26 \]
Um requisito básico de qualquer algoritmo de encriptação é que ele seja um-para-um. Ou seja, se \( p \neq q \), então \( E(k, p) \neq E(k, q) \). Caso contrário, a decriptação é impossível, pois mais de um caractere de texto claro é mapeado no mesmo caractere de texto cifrado. A cifra de César afim não é um-para-um para todos os valores de `a`. Por exemplo, para `a = 2` e `b = 3`, então \( E([a, b], 0) = E([a, b], 13) = 3 \).

(a) **Existem limitações sobre o valor de `b`? Explique por que sim ou por que não.**
- Não, não existem limitações sobre o valor de `b` na cifra de César afim. O valor de `b` pode ser qualquer inteiro, pois ele apenas desloca os caracteres de texto claro de forma linear. A limitação principal está no valor de `a`, que deve ser coprimo com 26 (o número de letras no alfabeto inglês) para garantir que a cifra seja um-para-um.

(b) **Determine quais valores de `a` não são permitidos.**
- Os divisores de 26 são 1, 2, 13 e 26. Portanto, não pode ter nenhum desses divisores, exceto 1, em comum com 26. Assim, os valores de `a` que não são permitidos são aqueles que têm divisores comuns com 26 além de 1.

(c) **Ofereça uma afirmação geral sobre quais valores de `a` são e não são permitidos. Justifique-a.**
- Os valores de `a` que são coprimos com 26 (ou seja, não têm 2 ou 13 como fator) são:
  - Permitidos: 1, 3, 5, 7, 9, 11, 15, 17, 19, 21, 23, 25
  - Não permitidos: 2, 4, 6, 8, 10, 12, 14, 16, 18, 20, 22, 24, 26

## 3. Cifra de Hill:
(a) **Encripte a mensagem "meet me at the usual place at ten rather than eight oclock" usando a cifra de Hill com a chave**
\[ \begin{bmatrix} 9 & 4 \\ 5 & 7 \end{bmatrix} \]
Mostre seus cálculos e o resultado.

(b) **Mostre os cálculos para a decriptação correspondente do texto cifrado a fim de recuperar o texto claro original.**

## 4. Programa para cifra de César
```python
def caesar_cipher(text, shift, alphabet="abcdefghijklmnopqrstuvwxyz", decrypt=False):
    text = text.lower()  # Converte o texto para minúsculas
    result_text = ""
    shift = -shift if decrypt else shift  # Inverte o deslocamento se for para desencriptar

    for char in text:
        if char in alphabet:
            # Calcula a nova posição da letra no alfabeto
            new_position = (alphabet.index(char) + shift) % len(alphabet)
            result_text += alphabet[new_position]
        else:
            # Preserva os caracteres que não estão no alfabeto (como espaços)
            result_text += char

    return result_text

def caesar_encrypt(plain_text, shift, alphabet="abcdefghijklmnopqrstuvwxyz"):
    return caesar_cipher(plain_text, shift, alphabet, decrypt=False)

def caesar_decrypt(cipher_text, shift, alphabet="abcdefghijklmnopqrstuvwxyz"):
    return caesar_cipher(cipher_text, shift, alphabet, decrypt=True)

plain_text = "meet me at the usual place at ten rather than eight o clock"
shift = 6  
encrypted = caesar_encrypt(plain_text, shift)
print("Encrypted:", encrypted)  # Exibe o texto encriptado
decrypted = caesar_decrypt(encrypted, shift)
print("Decrypted:", decrypted)  # Exibe o texto desencriptado
 


```

## 5. Ataque de Frequência de Letra

```python
import string
from collections import Counter

# Frequência de letras em português (em porcentagem)
frequencias_pt = {
    'a': 14.63, 'b': 1.04, 'c': 3.88, 'd': 4.99, 'e': 12.57, 'f': 1.02, 'g': 1.30,
    'h': 1.28, 'i': 6.18, 'j': 0.40, 'k': 0.02, 'l': 2.78, 'm': 4.74, 'n': 5.05,
    'o': 10.73, 'p': 2.52, 'q': 1.20, 'r': 6.53, 's': 7.81, 't': 4.34, 'u': 4.63,
    'v': 1.67, 'w': 0.01, 'x': 0.21, 'y': 0.01, 'z': 0.47
}

def decrypt_caesar(text, shift, alphabet="abcdefghijklmnopqrstuvwxyz"):
    decrypted = ""
    for char in text.lower():
        if char in alphabet:
            decrypted += alphabet[(alphabet.index(char) - shift) % len(alphabet)]
        else:
            decrypted += char
    return decrypted

def calculate_frequencies(text, alphabet="abcdefghijklmnopqrstuvwxyz"):
    count = Counter(char for char in text.lower() if char in alphabet)
    total = sum(count.values())
    return {char: (freq / total) * 100 for char, freq in count.items()}

def evaluate_text(text, alphabet="abcdefghijklmnopqrstuvwxyz"):
    letter_freqs = calculate_frequencies(text, alphabet)
    return sum(abs(letter_freqs.get(char, 0) - frequencias_pt.get(char, 0)) for char in alphabet)

def caesar_brute_force(cipher_text, top_n=10, alphabet="abcdefghijklmnopqrstuvwxyz"):
    results = []
    for shift in range(len(alphabet)):
        decrypted = decrypt_caesar(cipher_text, shift, alphabet)
        score = evaluate_text(decrypted, alphabet)
        results.append((score, decrypted, shift))
    return sorted(results)[:top_n]

cipher_text = "phhw ph dw wkh xvxdo sodfh dw whq udwkhu wkdq hljkw r forfn"  # Texto cifrado
top_n = 10  # Número de textos claros mais prováveis para mostrar
results = caesar_brute_force(cipher_text, top_n)

print(f"Os {top_n} textos claros mais prováveis são:")
for score, text, shift in results:
    print(f"Deslocamento: {shift}, Score: {score:.2f}, Texto: {text}")

 


```

## 6. Programa para cifra de Hill 2 × 2

```python
import numpy as np

def mod_inverse(a, m):
    m0, x0, x1 = m, 0, 1
    if m == 1:
        return 0
    while a > 1:
        q = a // m
        m, a = a % m, m
        x0, x1 = x1 - q * x0, x0
    if x1 < 0:
        x1 += m0
    return x1

def matrix_mod_inv(matrix, modulus):
    det = int(np.round(np.linalg.det(matrix)))
    det_inv = mod_inverse(det, modulus)
    matrix_modulus_inv = det_inv * np.round(det * np.linalg.inv(matrix)).astype(int) % modulus
    return matrix_modulus_inv

def hill_encrypt(plain_text, key_matrix):
    alphabet = "abcdefghijklmnopqrstuvwxyz"
    modulus = len(alphabet)
    plain_text = plain_text.replace(" ", "").lower()
    if len(plain_text) % 2 != 0:
        plain_text += "x"  # Adiciona um caractere de preenchimento se necessário

    encrypted_text = ""
    for i in range(0, len(plain_text), 2):
        pair = plain_text[i:i + 2]
        vector = np.array([alphabet.index(pair[0]), alphabet.index(pair[1])])
        encrypted_vector = np.dot(key_matrix, vector) % modulus
        encrypted_text += alphabet[encrypted_vector[0]] + alphabet[encrypted_vector[1]]

    return encrypted_text

def hill_decrypt(cipher_text, key_matrix):
    alphabet = "abcdefghijklmnopqrstuvwxyz"
    modulus = len(alphabet)
    inverse_key_matrix = matrix_mod_inv(key_matrix, modulus)

    decrypted_text = ""
    for i in range(0, len(cipher_text), 2):
        pair = cipher_text[i:i + 2]
        vector = np.array([alphabet.index(pair[0]), alphabet.index(pair[1])])
        decrypted_vector = np.dot(inverse_key_matrix, vector) % modulus
        decrypted_text += alphabet[decrypted_vector[0]] + alphabet[decrypted_vector[1]]

    return decrypted_text

# Exemplo de uso
plain_text = "meetmeattheusualplace"
key_matrix = np.array([[3, 3], [2, 5]])

encrypted_text = hill_encrypt(plain_text, key_matrix)
print(f"Texto encriptado: {encrypted_text}")

decrypted_text = hill_decrypt(encrypted_text, key_matrix)
print(f"Texto decriptado: {decrypted_text}")


```