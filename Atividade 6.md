# Atividade: Operação de Cifra de Bloco

### 1 - O que é encriptação tripla?

**Encriptação tripla** (conhecida como Triple DES ou 3DES) é uma técnica de aumentar a segurança do algoritmo DES (Data Encryption Standard) aplicando-o três vezes a cada bloco de dados, utilizando chaves diferentes. Isso melhora a resistência do DES contra ataques. Existem duas variações principais:

* **3DES com três chaves distintas (DES-EDE3):** Cada etapa usa uma chave diferente (K1, K2, K3).
* **3DES com duas chaves (DES-EDE2):** A primeira e a última chaves são as mesmas (K1, K2, K1).

### 2 - O que é ataque meet-in-the-middle?

O **ataque meet-in-the-middle** é uma técnica criptanalítica aplicada em esquemas de criptografia que envolvem várias etapas, como o 3DES. Este ataque explora a possibilidade de calcular um estado intermediário tanto do texto claro quanto do texto cifrado. Isso permite ao atacante combinar esses resultados intermediários para descobrir as chaves com menos esforço computacional do que tentar todas as combinações possíveis.

### 3 - Quantas chaves são usadas na encriptação tripla?

A encriptação tripla pode utilizar duas ou três chaves diferentes:

* No caso do **3DES com três chaves distintas (DES-EDE3)**, são utilizadas três chaves (K1, K2, K3).
* No **3DES com duas chaves (DES-EDE2)**, duas chaves são usadas (K1, K2), onde a primeira e a terceira são idênticas.

### 4 - Por que a parte do meio do 3DES é decriptação, em vez de encriptação?

A **decriptação na fase intermediária** do 3DES (DES-EDE) é usada para manter a compatibilidade com o DES original. Dessa maneira, ao aplicar a mesma chave nas três fases (encriptação, decriptação, encriptação), o 3DES se comporta de maneira idêntica ao DES, facilitando a interoperabilidade entre sistemas que utilizam DES e 3DES.

### 5 - Por que alguns modos de operação de cifra de bloco só utilizam a encriptação, enquanto outros empregam encriptação e decriptação?

Modos de operação de cifra de bloco, como **Electronic Codebook (ECB)** e **Cipher Block Chaining (CBC)**, utilizam encriptação e decriptação dependendo dos requisitos de segurança e do objetivo do esquema. No ECB, cada bloco é encriptado independentemente, enquanto no CBC tanto a encriptação quanto a decriptação são usadas para garantir que uma alteração em um bloco afete os blocos subsequentes, proporcionando maior segurança.

### 6 - Você deseja construir um dispositivo de hardware para realizar encriptação de bloco no modo cipher block chaining (CBC) usando um algoritmo mais forte do que DES. 3DES é um bom candidato. A Figura 1 mostra duas possibilidades, ambas acompanhando a definição do CBC. Qual das duas você escolheria:

#### a - Por segurança?

A opção **(b) CBC com três ciclos** oferece maior segurança. Isso ocorre porque cada fase da operação é processada separadamente, o que aumenta a complexidade do sistema e dificulta ataques como o ataque meet-in-the-middle. Como cada etapa utiliza uma chave diferente (K1, K2, K3), o sistema é mais resistente.

#### b - Por desempenho?

A opção **(a) CBC com um ciclo** seria mais eficiente em termos de desempenho. Isso ocorre porque todas as operações (EDE) são executadas dentro de um único bloco, reduzindo o tempo de processamento. Isso simplifica a implementação e diminui a quantidade de operações, tornando o dispositivo mais rápido.

### 7 - Crie um software que possa encriptar e decriptar no modo cipher block chaining usando uma das seguintes cifras: módulo affine 256, módulo Hill 256, S-DES, DES. Teste os dados para S-DES usando um vetor de inicialização binário de 1010 1010. Um texto claro binário de 0000 0001 0010 0011 encriptado com uma chave binária de 01111 11101 deverá dar um texto claro binário de 1111 0100 0000 1011. A decriptação deverá funcionar de modo correspondente.
