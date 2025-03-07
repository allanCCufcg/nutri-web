A inserção em um ArrayList tem um tempo de execução O(1) amortizado, mas para entender isso, precisamos analisar como o ArrayList gerencia sua capacidade interna.
🔹 Como funciona a inserção em um ArrayList?

Um ArrayList em Java é uma estrutura baseada em array dinâmico, ou seja, ele mantém um array interno e aumenta sua capacidade conforme necessário. O tempo de inserção depende de onde a inserção ocorre e se há necessidade de realocação de memória.

    Caso sem redimensionamento (Custo O(1)):
        Se ainda houver espaço disponível no array interno, a inserção ocorre no final e custa O(1), pois basta escrever o novo elemento na próxima posição livre.

    Caso com redimensionamento (Custo O(n)):
        Quando o array interno atinge sua capacidade máxima, o ArrayList precisa criar um novo array maior e copiar todos os elementos antigos para ele.
        Essa cópia tem um custo O(n), pois cada elemento precisa ser movido para o novo array.

🔹 Por que O(1) amortizado?

Embora o redimensionamento ocasional tenha custo O(n), ele não ocorre a cada inserção, mas sim esporadicamente. Se analisarmos o número total de operações em uma sequência de inserções, veremos que o custo médio por inserção é O(1).

Exemplo prático:

    Criamos um ArrayList com capacidade inicial de 4.
    Inserimos 4 elementos → Custo O(1) por inserção.
    Ao inserir o 5º elemento:
        O ArrayList dobra de tamanho (capacidade passa para 8).
        Todos os 4 elementos anteriores são copiados (custo O(4)).
        A nova inserção é feita.
    Novos elementos são inseridos normalmente até atingir a capacidade (8), sem realocações.

Agora, se fizermos n inserções, veremos que o número total de cópias feitas ao longo do tempo é menor que n, o que resulta em um custo médio O(1).
