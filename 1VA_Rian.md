# Verificação de Aprendizagem - CCMP3079

## 1. Avaliação de Impacto

### a) Uma organização gerenciando informações públicas em seu servidor web

- **Confidencialidade**: Baixo. As informações são públicas, portanto, a perda de confidencialidade não causa grandes transtornos.
- **Integridade**: Alta. Apesar de serem públicas, os dados devem estar corretos e não devem ser alterados indevidamente.
- **Disponibilidade**: Alto. A disponibilidade contínua é crucial para o acesso às informações.

### b) Uma organização de aplicação da lei gerindo informações de investigação extremamente sensíveis

- **Confidencialidade**: Alto. A divulgação não autorizada pode comprometer a segurança e a eficácia das investigações.
- **Integridade**: Alto. Modificações não autorizadas podem levar a decisões incorretas e comprometer investigações.
- **Disponibilidade**: Alto. A indisponibilidade pode atrasar ou comprometer o andamento das investigações.

### c) Uma organização financeira gerenciando informações administrativas rotineiras

- **Confidencialidade**: Moderado. Informações administrativas geralmente não são sensíveis, mas ainda assim, sua exposição pode ser indesejável.
- **Integridade**: Moderado. Alterações podem causar transtornos administrativos.
- **Disponibilidade**: Moderado. A indisponibilidade pode afetar a eficiência administrativa, mas não é crítica.

### d) Sistema de informação utilizado para grandes aquisições

#### Dados Sensíveis da Fase de Pré-Solicitação

- **Confidencialidade**: Alto. A divulgação pode comprometer o processo de aquisição.
- **Integridade**: Alto. Modificações podem distorcer o processo de aquisição.
- **Disponibilidade**: Alto. A indisponibilidade pode atrasar processos de aquisição.

#### Dados Administrativos Rotineiros

- **Confidencialidade**: Baixo. Informações geralmente não são sensíveis.
- **Integridade**: Moderado. Modificações podem causar transtornos administrativos.
- **Disponibilidade**: Moderado. A indisponibilidade afeta a eficiência.

#### Sistema de Informação Único

- **Confidencialidade**: Alto. A combinação de dados sensíveis e administrativos requer proteção robusta.
- **Integridade**: Alto. A integridade dos dados é crítica tanto para processos críticos quanto para operações administrativas.
- **Disponibilidade**: Alto. A interrupção afeta tanto processos críticos quanto operações administrativas.

### e) Indústria de energia com sistema SCADA

#### Sensores de Dados em Tempo Real

- **Confidencialidade**: Moderado. Dados podem revelar padrões de operação que devem ser protegidos.
- **Integridade**: Alto. Modificações podem causar falhas operacionais graves.
- **Disponibilidade**: Alto. A indisponibilidade pode interromper a distribuição de energia.

#### Informações das Rotinas Administrativas

- **Confidencialidade**: Moderado. Pode conter dados sensíveis sobre operações e manutenção.
- **Integridade**: Alto. Modificações podem afetar a eficiência e segurança operacional.
- **Disponibilidade**: Alta. A indisponibilidade afeta a administração e operações contínuas.

#### Sistema de Informação Único

- **Confidencialidade**: Alto. Integra dados operacionais e administrativos que podem ser sensíveis.
- **Integridade**: Alto. A integridade é crítica para operações seguras e eficientes.
- **Disponibilidade**: Alto. A disponibilidade contínua é crucial para a operação e administração.

## 2. Conceitos de Criptografia

### a) Elementos Essenciais de uma Cifra Simétrica

- **Texto Pleno (Plaintext)**: Mensagem original que precisa ser cifrada.
- **Algoritmo de Cifragem**: Conjunto de regras matemáticas usadas para transformar o texto pleno em texto cifrado.
- **Chave (Key)**: Valor secreto usado pelo algoritmo para cifrar e decifrar o texto.
- **Texto Cifrado (Ciphertext)**: Resultado da aplicação do algoritmo ao texto pleno usando a chave.

### b) Funções Básicas dos Algoritmos de Encriptação

- **Substituição**: Substitui cada elemento do texto pleno por outro. Exemplo: Cifra de César.
- **Transposição**: Rearranja os elementos do texto pleno. Exemplo: Cifra de transposição.

### c) Número de Chaves em uma Cifra Simétrica

- **Número de Chaves**: Duas pessoas precisam de uma única chave secreta compartilhada para se comunicar. Ambas podem cifrar e decifrar usando essa chave.

### d) Técnicas de Ataque em uma Cifra

- **Criptoanálise**: Uso de métodos matemáticos para encontrar a chave ou reduzir a segurança da cifra. Exemplo: Análise de frequência.
- **Ataque de Força Bruta**: Testa todas as combinações possíveis de chaves até encontrar a correta. Exemplo: Testar todas as chaves em uma cifra curta.

### e) Definições e Diferenças

- **Cifra de César**: Substitui cada letra do texto pleno por outra que está um número fixo de posições à frente no alfabeto.
- **Cifra de Hill**: Usa álgebra linear e matrizes invertíveis para cifrar blocos de texto.
- **Cifra de Feistel**: Estrutura que divide o texto pleno em duas metades e aplica uma função de mistura repetidamente. Importante para construir cifras seguras e eficientes.
- **Diferença entre DES, Rijndael e AES**:
  - **DES (Data Encryption Standard)**: Usa uma chave de 56 bits e tornou-se inseguro devido à chave curta.
  - **Rijndael**: Algoritmo que foi selecionado como AES, usa tamanhos de bloco e chave variáveis.
  - **AES (Advanced Encryption Standard)**: Padrão que usa Rijndael com tamanhos de chave de 128, 192, ou 256 bits. É seguro e amplamente utilizado.

## 3. Decodificação de Mensagem

Mensagem cifrada com Playfair e chave 'royal new zealand navy': 

obtive a seguinte mensagem: KING NEW ZEALAND NAVY HELP WOUNDED TO RESCUE PT BOAT


## 4. Aplicação da Cifra de Hill 2 × 2

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
        plain_text += "x"

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
plain_text = "OlaMundo"
key_matrix = np.array([[3, 3], [2, 5]])

encrypted_text = hill_encrypt(plain_text, key_matrix)
print(f"Texto encriptado: {encrypted_text}")

decrypted_text = hill_decrypt(encrypted_text, key_matrix)
print(f"Texto decriptado: {decrypted_text}")
```


## 5. Responda, resumidamente, as questões a seguir:

### a) Qual é a diferença entre uma cifra de bloco e uma cifra de fluxo?

- **Cifra de Bloco**: Processa o texto claro em blocos de tamanho fixo (por exemplo, 64 ou 128 bits) de uma vez. Cada bloco é cifrado separadamente.
- **Cifra de Fluxo**: Cifra o texto claro um bit ou byte de cada vez, gerando um fluxo contínuo de texto cifrado.

### b) O que é uma cifra de produto?

Uma **cifra de produto** combina duas ou mais operações de criptografia para aumentar a segurança. As operações podem incluir substituição, transposição e outras técnicas de cifragem.

### c) Qual é a diferença entre difusão e confusão? Explique.

- **Difusão**: Espalha a influência de um único bit do texto claro em muitos bits do texto cifrado, escondendo as relações entre o texto claro e o texto cifrado.
- **Confusão**: Torna a relação entre a chave de cifragem e o texto cifrado o mais complexa possível para dificultar a criptoanálise.

### d) Quais parâmetros e escolhas de projeto determinam o algoritmo real de uma cifra de Feistel?

- **Número de Rodadas**: Quantas vezes a função de cifragem será aplicada.
- **Função de Rodada**: A operação específica aplicada em cada rodada, incluindo substituição e permutação.
- **Tamanho do Bloco**: O tamanho dos blocos de dados processados pelo algoritmo (ex.: 64 bits, 128 bits).
- **Tamanho da Chave**: O comprimento da chave de cifragem.
- **Chave de Agendamento**: O método para gerar chaves de rodada a partir da chave principal.

### e) Explique o efeito avalanche.

O **efeito avalanche** refere-se à propriedade de um algoritmo criptográfico onde uma pequena mudança no texto claro ou na chave resulta em uma mudança significativa e imprevisível no texto cifrado.

## 6. Encontre o inverso multiplicativo de cada elemento diferente de zero em Z5

* **1**: O inverso multiplicativo é **1**, pois \( 1 X 1 = 1 mod 5 \).
* **2**: O inverso multiplicativo é **3**, pois \( 2 X 3 = 6 = 1 mod 5 \).
* **3**: O inverso multiplicativo é **2**, pois \( 3 X 2 = 6 = 1 mod 5 \).
* **4**: O inverso multiplicativo é **4**, pois \( 4 X 4 = 16 = 1 mod 5 \).

## 7. Para a aritmética de polinômios com coeficientes em Z10, realize os seguintes cálculos:

1. −x² + 7x − 3

2. 30x⁴ + 5x³ + 22x² + 2x + 6


## 8. Use a chave 1010 0111 0011 1011 para encriptar o texto claro "ok" conforme expresso em ASCII, ou seja, 0110 1111 0110 1011. Os projetistas do S-AES obtiveram o texto cifrado 0000 0111 0011 1000. E você?

Obtive o seguinte texto cifrado: `0110 0001 0010 0010`.

## 9. Compare AES com DES. Para cada um dos seguintes elementos do DES, indique o elemento comparável no AES ou explique por que ele não é necessário no AES.

### a) XOR do material da subchave com a entrada da função f

- **DES**: A subchave gerada para cada rodada é aplicada à entrada da função f usando a operação XOR.
- **AES**: A subchave é combinada com o estado usando a operação XOR em cada rodada. O AES também utiliza XOR para combinar subchaves com os dados.

### b) XOR da saída da função f com a metade esquerda do bloco

- **DES**: A saída da função f é combinada com a metade esquerda do bloco usando a operação XOR.
- **AES**: O AES não divide o bloco em metades; em vez disso, o estado inteiro é tratado como uma matriz de bytes, e as operações de mistura e transformação ocorrem em toda a matriz.

### c) Função f

- **DES**: A função f do DES envolve expansão, aplicação de subchave, substituição através de S-boxes e permutação.
- **AES**: O AES não possui uma função f específica; em vez disso, tem várias operações de transformação em cada rodada, incluindo SubBytes, ShiftRows, MixColumns e AddRoundKey.

### d) Permutação P

- **DES**: A permutação P é uma permutação fixa aplicada após a substituição de S-boxes na função f.
- **AES**: No AES, não há uma permutação fixa diretamente comparável à permutação P de DES.

### e) Troca de metades do bloco

- **DES**: No final de cada rodada, as metades do bloco são trocadas.
- **AES**: No AES, não há troca de metades do bloco; o AES trata o bloco como uma única matriz de bytes.

## 10. Calcule a saída da transformação MixColumns para a sequência de bytes de entrada `67 89 AB CD`. Aplique a transformação InvMixColumns ao resultado obtido para verificar seus cálculos. Altere o primeiro byte da entrada de `67` para `77`, realize a transformação MixColumns novamente para a nova entrada e determine quantos bits mudaram na saída.

```python
def gf_mult(a, b):
    """Multiplicação no corpo finito GF(2^8)"""
    p = 0
    while b:
        if b & 1:
            p ^= a
        a <<= 1
        if a & 0x100:
            a ^= 0x11B
        b >>= 1
    return p & 0xFF

def mix_single_column(a):
    """Transformação MixColumns para uma única coluna"""
    b = [0] * 4
    b[0] = gf_mult(0x02, a[0]) ^ gf_mult(0x03, a[1]) ^ a[2] ^ a[3]
    b[1] = a[0] ^ gf_mult(0x02, a[1]) ^ gf_mult(0x03, a[2]) ^ a[3]
    b[2] = a[0] ^ a[1] ^ gf_mult(0x02, a[2]) ^ gf_mult(0x03, a[3])
    b[3] = gf_mult(0x03, a[0]) ^ a[1] ^ a[2] ^ gf_mult(0x02, a[3])
    return b

def inv_mix_single_column(a):
    """Transformação InvMixColumns para uma única coluna"""
    b = [0] * 4
    b[0] = gf_mult(0x0e, a[0]) ^ gf_mult(0x0b, a[1]) ^ gf_mult(0x0d, a[2]) ^ gf_mult(0x09, a[3])
    b[1] = gf_mult(0x09, a[0]) ^ gf_mult(0x0e, a[1]) ^ gf_mult(0x0b, a[2]) ^ gf_mult(0x0d, a[3])
    b[2] = gf_mult(0x0d, a[0]) ^ gf_mult(0x09, a[1]) ^ gf_mult(0x0e, a[2]) ^ gf_mult(0x0b, a[3])
    b[3] = gf_mult(0x0b, a[0]) ^ gf_mult(0x0d, a[1]) ^ gf_mult(0x09, a[2]) ^ gf_mult(0x0e, a[3])
    return b

def mix_columns(state):
    """Transformação MixColumns para a matriz de estado completa"""
    for i in range(4):
        column = state[i*4:(i+1)*4]
        new_column = mix_single_column(column)
        state[i*4:(i+1)*4] = new_column
    return state

def inv_mix_columns(state):
    """Transformação InvMixColumns para a matriz de estado completa"""
    for i in range(4):
        column = state[i*4:(i+1)*4]
        new_column = inv_mix_single_column(column)
        state[i*4:(i+1)*4] = new_column
    return state

def print_state(state):
    for i in range(4):
        print(' '.join(f'{b:02x}' for b in state[i*4:(i+1)*4]))

# Entrada
input_bytes = [0x67, 0x89, 0xAB, 0xCD, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00]

# Transformação MixColumns
output = mix_columns(input_bytes.copy())
print("Saída de MixColumns:")
print_state(output)

# Verificação com InvMixColumns
recovered = inv_mix_columns(output.copy())
print("Entrada recuperada:")
print_state(recovered)

# Alterando o primeiro byte e calculando novamente
input_bytes[0] = 0x77
new_output = mix_columns(input_bytes.copy())
print("Nova saída de MixColumns:")
print_state(new_output)

# Contando as diferenças de bits
count = 0
for i in range(16):
   for j in range(8):
       if (output[i] >> j) & 1 != (new_output[i] >> j) & 1:
           count += 1
print("Número de bits alterados:", count)


  