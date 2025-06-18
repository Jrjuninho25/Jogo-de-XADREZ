# Jogo-de-XADREZ
#include <stdio.h>

// Função para mostrar o tabuleiro
void mostrarTabuleiro(char tabuleiro[8][8]) {
    printf("  A B C D E F G H\n");
    for (int i = 0; i < 8; i++) {
        printf("%d ", 8 - i);
        for (int j = 0; j < 8; j++) {
            printf("%c ", tabuleiro[i][j]);
        }
        printf("%d\n", 8 - i);
    }
    printf("  A B C D E F G H\n");
}

int main() {
    // Cria o tabuleiro e preenche com espaços
    char tabuleiro[8][8];
    for (int i = 0; i < 8; i++)
        for (int j = 0; j < 8; j++)
            tabuleiro[i][j] = '.';

    // Posiciona peças no tabuleiro
    tabuleiro[7][0] = 'T'; tabuleiro[7][1] = 'C'; tabuleiro[7][2] = 'B';
    tabuleiro[7][3] = 'D'; tabuleiro[7][4] = 'R'; tabuleiro[7][5] = 'B';
    tabuleiro[7][6] = 'C'; tabuleiro[7][7] = 'T';

    for (int i = 0; i < 8; i++) {
        tabuleiro[6][i] = 'P'; // peões
    }

    // Loop do jogo (1 movimento por vez)
    char origemColuna, destinoColuna;
    int origemLinha, destinoLinha;

    while (1) {
        mostrarTabuleiro(tabuleiro);

        printf("\nDigite a posição de origem (ex: E2): ");
        scanf(" %c%d", &origemColuna, &origemLinha);

        printf("Digite a posição de destino (ex: E4): ");
        scanf(" %c%d", &destinoColuna, &destinoLinha);

        // Converte letras e números para índices
        int oCol = origemColuna - 'A';
        int oLin = 8 - origemLinha;
        int dCol = destinoColuna - 'A';
        int dLin = 8 - destinoLinha;

        // Verifica se está dentro do tabuleiro
        if (oCol < 0 || oCol > 7 || dCol < 0 || dCol > 7 ||
            oLin < 0 || oLin > 7 || dLin < 0 || dLin > 7) {
            printf("Posição inválida. Tente novamente.\n");
            continue;
        }

        // Move a peça
        char peca = tabuleiro[oLin][oCol];
        tabuleiro[oLin][oCol] = '.';
        tabuleiro[dLin][dCol] = peca;

        printf("Peça '%c' movida de %c%d para %c%d\n",
               peca, origemColuna, origemLinha, destinoColuna, destinoLinha);
    }

    return 0;
}
