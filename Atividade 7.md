Criptografia: Conceitos e Algoritmos
Aleatoriedade Estatística vs. Imprevisibilidade

Aleatoriedade Estatística: Refere-se à distribuição dos resultados ao longo do tempo, que deve parecer aleatória para passar testes estatísticos.
Imprevisibilidade: Mesmo conhecendo uma parte da sequência, não é possível prever os próximos resultados.

Considerações de Projeto para Cifras de Fluxo

Sincronização: Emissor e receptor devem manter o estado da chave de fluxo sincronizado.
Chave Única por Fluxo: Cada fluxo de dados deve usar uma chave diferente para evitar ataques de repetição.
Gerador de Chave Segura: A chave de fluxo deve ser gerada por um gerador criptograficamente seguro.
Eficiência: A cifra deve ser eficiente para suportar criptografia em tempo real.
Resistência a Ataques Conhecidos: Deve ser resistente a ataques como análise diferencial e linear.

Reutilização de Chaves em Cifras de Fluxo
Reutilizar uma chave de cifra de fluxo é problemático, pois permite que um atacante que obtenha múltiplas versões cifradas da mesma mensagem derive a chave ou informações sobre os dados originais. Isso é especialmente crítico em cifras de fluxo, onde o mesmo fluxo de chave é combinado com diferentes dados, possibilitando ataques de criptoanálise.
Operações Primitivas no RC4
O algoritmo RC4 utiliza as seguintes operações:

Trocas de Posições (Swap): Durante a permutação da tabela S.
Geração de Sequência Pseudo-Aleatória: Produzindo um fluxo de chave a partir da permutação de S.
XOR: Combinação do fluxo de chave com os dados de entrada para produzir o texto cifrado.

Algoritmo de Congruência Linear
Considerando a fórmula: Xn+1​=(aXn​)mod31


Para (k=1) e (a=3): Sequência: 1, 3, 9, 27, 19, 26, 16, 17, 20, 29, 25, 13, 4, 12, 7, 21, 2, 6, 18, 23, 7, 21, 2, 6, 18, 23, 9, 27, 19, 26, 1 (Período: 30).
Para (k=2) e (a^2=9): Sequência: 1, 9, 19, 16, 19, 16, 19, 16… (Período: 2).
Para (k=3) e (a^3=27): Sequência: 1, 27, 29, 27, 29… (Período: 2).
Para (k=4) e (a^4=16): Sequência: 1, 16, 8, 4, 2, 1… (Período: 5).

Gerador Blum Blum Shub
Dado (p = 499), (q = 503), e (s = 17), a sequência gerada pelo algoritmo Blum Blum Shub com a fórmula (x_i = (x_{i-1}^2) \mod n) é:
Sequência gerada: 289, 253306, 14107, 23546, 67740, 144593, 79829, 46219, 132936, 9863.