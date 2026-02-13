# ProjetoPseudoAleatoriedade
Projeto Próprio com foco em testes para geração aleatória de dados para jogos de mesa
-------------------------------------------------------------------------------------------------

CryptoRPG Dice Engine
Uma biblioteca de alto desempenho em C++ projetada para processar e executar expressões complexas de dados de RPG (sistema XdY). O motor prioriza a integridade estatística, utilizando fontes de entropia do sistema operacional para garantir resultados verdadeiramente imprevisíveis.

Destaques do Projeto
Interpretador de Expressões: Processa múltiplas cadeias de dados em uma única entrada (ex: 3d8+2d10+1d12).

Aleatoriedade de Classe Criptográfica: Implementação baseada em std::random_device, acessando o hardware/SO para gerar entropia real.

Transparência de Resultados: Exibição detalhada de cada face sorteada antes do cálculo da soma total.

Código Moderno: Desenvolvido seguindo padrões do C++17 para máxima eficiência e portabilidade.

-------------------------------------------------------------------------------------------------
Arquitetura e Funcionamento
O motor opera em duas camadas principais:

1. Análise Sintática (Parsing)
O sistema tokeniza a string de entrada utilizando o delimitador +. Cada token é validado e decomposto no formato padrão da indústria:

X (quantidade) d Y (faces)

2. Geração de Números Aleatórios (RNG)
Diferente de geradores simples baseados no tempo do sistema (time(0)), este motor utiliza:

Linux/macOS: /dev/urandom
Windows: Windows Cryptographic API (através da abstração do compilador)

Isso mitiga padrões previsíveis, tornando-o ideal para sistemas de apostas ou plataformas multiplayer competitivas.

-------------------------------------------------------------------------------------------------

Especificações Técnicas

Linguagem:	C++17 ou superior
Biblioteca Padrão:	<random>, <string>, <vector>, <sstream>
Gerador	std::random_device
Complexidade:	O(n) onde n é o número de dados total

-------------------------------------------------------------------------------------------------

Compilar e Executar
Pré-requisitos
Compilador com suporte a C++17 (GCC 7+, Clang 5+, ou MSVC 19.14+).

Instruções de Compilação

# Clone o repositório
git clone https://github.com/seu-usuario/CryptoRPG.git

# Compile (Linux/macOS)
g++ -std=c++17 main.cpp -o dice_engine

# Execute
./dice_engine

-------------------------------------------------------------------------------------------------

Exemplo de Uso
Entrada do Usuário:

3d8+2d10

-------------------------------------------------------------------------------------------------

Segurança e Entropia
Este motor foi desenhado para ser resiliente a ataques de previsão de estado.

IMPORTANTE!
Embora o std::random_device forneça entropia não-determinística na maioria das plataformas modernas, o comportamento exato depende da implementação do compilador. Para sistemas que exigem conformidade com normas militares ou financeiras, recomenda-se a integração direta com APIs nativas (como a BCrypt no Windows).

