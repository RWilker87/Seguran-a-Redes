

## Perguntas

1. Responda os questionamentos a seguir:
   a) Por que é importante estudar a cifra de Feistel?
   b) Qual é a diferença entre uma cifra de bloco e uma cifra de fluxo?
   c) Por que não é prático usar uma cifra de substituição reversível qualquer do tipo mostrado na Tabela 3.1?
   d) O que é uma cifra de produto?
   e) Qual é a diferença entre difusão e confusão?
   f) Que parâmetros e escolhas de projeto determinam o algoritmo real de uma cifra de Feistel?
   g) Explique o efeito avalanche.

2. Qual(is) dos recursos abaixo estão presentes no projeto da rede de Feistel? Explique.
   a) Tamanho do bloco e da chave;
   b) Função da rodada;
   c) Gerador de sub-chaves;
   d) Todas as alternativas.

3. Qual é o tamanho do texto claro no Data Encryption Standard (DES)? Explique.
   a) 57;
   b) 48;
   c) 32;
   d) 64.

4. A cifra de Feistel do algoritmo de encriptação utilizada no Data Encryption Standard (DES) utiliza quantos S-boxes? Explique.
   a) 8;
   b) 7;
   c) 6;
   d) 5.

5. O Data Encryption Standard possui uma chave de 56 bits, o que torna possível um espaço de 2^56 chaves possíveis. Essa sentença trata de ataque de. . . Explique.
   a) Tempo;
   b) Matemático;
   c) Força-Bruta;
   d) DoS.

6. Demonstre, através de um exemplo, como realizar a cifragem de 16 bits (dois caracteres), em 2 rounds, em seguida, decifre o texto cifrado. Explique o processo passo a passo. Forneça um código Python/Sagemath com sua solução.

7. Considere uma cifra de Feistel composta de 16 rodadas com tamanho de bloco de 128 bits e tamanho de chave de 128 bits. Suponha que, para determinado k, o algoritmo de escalonamento de chave defina valores às oito primeiras chaves de rodada, k1, k2, ..., k8, e depois estabeleça
   k9 = k8, k10 = k7, k11 = k6, ..., k16 = k1
   Admita que você tenha um texto cifrado S. Explique como, com acesso a um oráculo de encriptação, você pode decriptar c e determinar m usando apenas uma única consulta a ele. Isso mostra que tal cifra é vulnerável a um ataque de texto claro escolhido. (Um oráculo de encriptação pode ser imaginado como um dispositivo que, dado um texto claro, retorna o texto cifrado correspondente. Os detalhes internos do dispositivo não são conhecidos, e você não pode abri-lo. Você só consegue obter informações do oráculo fazendo consultas a ele e observando suas respostas.)

## Respostas

1. a) Porque ela é a base teórica de muitos algoritmos de criptografia modernos, incluindo o DES (Data Encryption Standard). Ela oferece um modelo robusto e eficiente para realizar operações de cifragem e decifragem de forma segura, utilizando estruturas simples de rede de Feistel.

   b) Uma cifra de bloco cifra dados em blocos de tamanho fixo, enquanto uma cifra de fluxo cifra dados byte a byte.

   c) Porque ela é vulnerável a análise de frequência e padrões previsíveis.

   d) É combinar operações simples, como substituições e permutações, para melhorar a segurança. As cifras de produto iteradas realizam a encriptação em várias rodadas, cada uma usando uma subchave derivada da chave original.

   e) **Confusão:** É como criar um texto criptografado desorientado. A confusão torna difícil deduzir a chave, pois relaciona as estatísticas do texto criptografado com a chave de forma complexa.
   
      **Difusão:** Aqui, aumentamos a redundância do texto simples no texto criptografado.

   f) - Tamanho dos blocos: geralmente 64 bits.
      - Tamanho das chaves: chaves maiores significam mais segurança, mas podem afetar a velocidade de execução.
      - Número de rodadas: o tamanho típico é cerca de 16 rodadas.
      - Complexidade da função de rodada: quanto mais complexa, melhor.
      - Geração das sub-chaves: quanto mais complexa, melhor.

   g) O efeito avalanche é uma propriedade desejável em algoritmos criptográficos, como cifras de bloco e funções de hash. Quando você faz uma pequena alteração na entrada (como trocar um único bit), a saída do algoritmo muda drasticamente.

2. **Todas as alternativas:**
   - **Tamanho do bloco e da chave:** A rede de Feistel pode ser projetada para operar com blocos e chaves de tamanhos variáveis.
   - **Função da rodada:** Cada rodada da rede de Feistel utiliza uma função que é aplicada repetidamente para aumentar a confusão e difusão dos dados.
   - **Gerador de sub-chaves:** É necessário gerar sub-chaves a partir da chave principal para cada rodada da rede de Feistel.

3. **64 bits:** Um bloco de texto claro de 64 bits para cada operação de criptografia.

4. **8 S-boxes:** Em cada rodada do processo de encriptação. Cada S-box recebe uma entrada de 6 bits e produz uma saída de 4 bits.

5. **Força bruta:** Pois o atacante teria que tentar uma enorme quantidade de possibilidades até conseguir.

6. *Resposta em desenvolvimento com exemplo e código.*

7. **Estrutura da Cifra:**
   - Tamanho do bloco: 128 bits.
   - Tamanho da chave: 128 bits.
   - As primeiras oito chaves de rodada são denotadas como k1, k2, ..., k8.
   - As chaves subsequentes são derivadas de forma circular: k9 = k8, k10 = k7, k11 = k6, ..., k16 = k1.
   
   **Ataque de Texto Claro Escolhido:**
   - Começamos escolhendo um texto claro e arbitrário, que chamaremos de “m”.
   - Consultamos o oráculo de encriptação com o texto claro “m” e obtemos o texto cifrado correspondente, que chamaremos de “c”.
   
   **Processo de Decriptação:**
   - Para decriptar o texto cifrado “c”, precisamos encontrar as chaves de rodada correspondentes.
   - Felizmente, temos acesso ao oráculo de encriptação, o que nos permite fazer uma consulta com o texto claro “m” e obter o texto cifrado.
   
   **Estratégia de Decriptação:**
   - Calculamos a chave k9 a partir de k8 (usando a relação circular).
   - Em seguida, calculamos k10 a partir de k9 e continuamos até chegarmos a k16.
   - Finalmente, aplicamos as chaves de rodada na ordem inversa (de k16 a k1) para decriptar o texto cifrado “c” e obter o texto claro “m”.

   Com apenas uma consulta ao oráculo de encriptação, podemos determinar as chaves de rodada e decriptar o texto cifrado. Isso revela que essa cifra de Feistel é vulnerável a um ataque de texto claro escolhido, pois podemos recuperar o texto original sem conhecer as chaves diretamente.
