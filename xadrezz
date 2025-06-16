#include <stdio.h>
#include <string.h>

#define TAM 8

void inicializarTabuleiro(char tabuleiro[TAM][TAM]) {
    for (int i = 0; i < TAM; i++) 
        for (int j = 0; j < TAM; j++) 
            tabuleiro[i][j] = '.'; 
    }
    
    tabuleiro[0][0] = 'T';
    tabuleiro[2][2] = 'B';
    tabuleiro[3][3] = 'R';
}

void mostrarTabuleiro(char tabuleiro[TAM][TAM]) {
    printf("\n   ");
    for (int j = 0; j < TAM; j++) {
        printf("%d  ", j + 1);
    }
    printf("\n");
    for (int i = 0; i < TAM; i++) {
        printf("%c  ", 'A' + i);
        for (int j = 0; j < TAM; j++) {
            printf("%c  ", tabuleiro[i][j]);
        }
        printf("\n");
    }
}

int moverTorre(char tabuleiro[TAM][TAM], int linhaOrigem, int colunaOrigem, int linhaDestino, int colunaDestino) {
    if (linhaOrigem != linhaDestino && colunaOrigem != colunaDestino) 
        printf("Movimento inválido para a Torre! Deve ser horizontal ou vertical.\n");
        return 0;
    
    if (tabuleiro[linhaOrigem][colunaOrigem] != 'T') 
        printf("Nenhuma Torre na posição de origem!\n");
        return 0;
    

    if (linhaOrigem == linhaDestino) 
        int passo = (colunaDestino > colunaOrigem) ? 1 : -1;
        int j = colunaOrigem + passo;
        for (; j != colunaDestino; j += passo) 
            printf("Torre moveu-se para a casa (%c, %d) - Direção: %s\n", 
                   'A' + linhaOrigem, j + 1, passo > 0 ? "Direita" : "Esquerda");
            if (tabuleiro[linhaOrigem][j] != '.') return 0;
        
    }
    else {
        int passo = (linhaDestino > linhaOrigem) ? 1 : -1;
        int i = linhaOrigem + passo;
        for (; i != linhaDestino; i += passo)
            printf("Torre moveu-se para a casa (%c, %d) - Direção: %s\n", 
                   'A' + i, colunaOrigem + 1, passo > 0 ? "Cima" : "Baixo");
            if (tabuleiro[i][colunaOrigem] != '.') return 0;
    }

    if (tabuleiro[linhaDestino][colunaDestino] != '.') return 0;
    tabuleiro[linhaOrigem][colunaOrigem] = '.';
    tabuleiro[linhaDestino][colunaDestino] = 'T';
    printf("Torre moveu-se para a casa (%c, %d) - Direção: Final\n", 'A' + linhaDestino, colunaDestino + 1);
    return 1;
}

int moverBispo(char tabuleiro[TAM][TAM], int linhaOrigem, int colunaOrigem, int linhaDestino, int colunaDestino) {
    if (abs(linhaDestino - linhaOrigem) != abs(colunaDestino - colunaOrigem)) 
        printf("Movimento inválido para o Bispo! Deve ser diagonal.\n");
        return 0;

    if (tabuleiro[linhaOrigem][colunaOrigem] != 'B') 
        printf("Nenhum Bispo na posição de origem!\n");
        return 0;
    

    int passoLinha = (linhaDestino > linhaOrigem) ? 1 : -1;
    int passoColuna = (colunaDestino > colunaOrigem) ? 1 : -1;
    int i = linhaOrigem + passoLinha;
    int j = colunaOrigem + passoColuna;
    int contador = 0;
    while (i != linhaDestino && j != colunaDestino)
        printf("Bispo moveu-se para a casa (%c, %d) - Direção: Diagonal %s-%s\n", 
               'A' + i, j + 1, passoLinha > 0 ? "Cima" : "Baixo", passoColuna > 0 ? "Direita" : "Esquerda");
        if (tabuleiro[i][j] != '.') return 0;
        i += passoLinha;
        j += passoColuna;
        contador++;
    }

    if (tabuleiro[linhaDestino][colunaDestino] != '.') return 0;
    tabuleiro[linhaOrigem][colunaOrigem] = '.';
    tabuleiro[linhaDestino][colunaDestino] = 'B';
    printf("Bispo moveu-se para a casa (%c, %d) - Direção: Final\n", 'A' + linhaDestino, colunaDestino + 1);
    return 1;
}

int moverRainha(char tabuleiro[TAM][TAM], int linhaOrigem, int colunaOrigem, int linhaDestino, int colunaDestino) {
    if (tabuleiro[linhaOrigem][colunaOrigem] != 'R') 
        printf("Nenhuma Rainha na posição de origem!\n");
        return 0;
    int deltaLinha = abs(linhaDestino - linhaOrigem);
    int deltaColuna = abs(colunaDestino - colunaOrigem);
    if (deltaLinha != 0 && deltaColuna != 0 && deltaLinha != deltaColuna) 
        printf("Movimento inválido para a Rainha! Deve ser horizontal, vertical ou diagonal.\n");
        return 0;
    

    int passoLinha = (linhaDestino > linhaOrigem) ? 1 : (linhaDestino < linhaOrigem) ? -1 : 0;
    int passoColuna = (colunaDestino > colunaOrigem) ? 1 : (colunaDestino < colunaOrigem) ? -1 : 0;
    int i = linhaOrigem + passoLinha;
    int j = colunaOrigem + passoColuna;
    int contador = 0;
    do
        if (i == linhaDestino && j == colunaDestino) break;
        printf("Rainha moveu-se para a casa (%c, %d) - Direção: %s%s\n", 
               'A' + i, j + 1, 
               passoLinha != 0 ? (passoLinha > 0 ? "Cima" : "Baixo") : "",
               passoColuna != 0 ? (passoColuna > 0 ? "Direita" : "Esquerda") : "");
        if (tabuleiro[i][j] != '.') return 0;
        i += passoLinha;
        j += passoColuna;
        contador++;
    } while (i != linhaDestino || j != colunaDestino);

    if (tabuleiro[linhaDestino][colunaDestino] != '.') return 0;
    tabuleiro[linhaOrigem][colunaOrigem] = '.';
    tabuleiro[linhaDestino][colunaDestino] = 'R';
    printf("Rainha moveu-se para a casa (%c, %d) - Direção: Final\n", 'A' + linhaDestino, colunaDestino + 1);
    return 1;
}

int main() {
    char tabuleiro[TAM][TAM];
    char peça[2], origem[3], destino[3];
    int linhaOrigem, colunaOrigem, linhaDestino, colunaDestino;

    inicializarTabuleiro(tabuleiro);
    printf("=== Jogo de Xadrez - Simulação de Movimentos ===\n");
    mostrarTabuleiro(tabuleiro);

    while (1) {
        printf("\nDigite a peça (T para Torre, B para Bispo, R para Rainha) ou 'S' para sair: ");
        scanf("%s", peça);
        if (peça[0] == 'S' || peça[0] == 's') break;

        printf("Digite a posição de origem (ex: A1): ");
        scanf("%s", origem);
        printf("Digite a posição de destino (ex: A2): ");
        scanf("%s", destino);

        linhaOrigem = origem[0] - 'A';
        colunaOrigem = origem[1] - '1';
        linhaDestino = destino[0] - 'A';
        colunaDestino = destino[1] - '1';

        if (linhaOrigem < 0 || linhaOrigem >= TAM || colunaOrigem < 0 || colunaOrigem >= TAM ||
            linhaDestino < 0 || linhaDestino >= TAM || colunaDestino < 0 || colunaDestino >= TAM) {
            printf("Coordenadas inválidas! Tente novamente.\n");
            continue;
        }

        int sucesso = 0;
        if (peça[0] == 'T') {
            sucesso = moverTorre(tabuleiro, linhaOrigem, colunaOrigem, linhaDestino, colunaDestino);
        } else if (peça[0] == 'B') {
            sucesso = moverBispo(tabuleiro, linhaOrigem, colunaOrigem, linhaDestino, colunaDestino);
        } else if (peça[0] == 'R') {
            sucesso = moverRainha(tabuleiro, linhaOrigem, colunaOrigem, linhaDestino, colunaDestino);
        } else {
            printf("Peça inválida! Use T, B ou R.\n");
            continue;
        }

        if (sucesso) {
            printf("Movimento realizado com sucesso!\n");
            mostrarTabuleiro(tabuleiro);
        } else {
            printf("Movimento inválido! Tente novamente.\n");
        }
    }

    printf("Jogo encerrado.\n");
    return 0;
}








#include <stdio.h>

int main() {
    const int casas_baixo = 2;
    const int casas_esquerda = 1;

    printf("\n");

    printf("Movimento do Cavalo:\n");

    for (int i = 0; i < casas_baixo; i++) {
        printf("Baixo\n");
    }

    int j = 0;
    while (j < casas_esquerda) {
        printf("Esquerda\n");
        j++;
    }

    return 0;
}





#include <stdio.h>

void moverTorre(int casas_restantes, const char* direcao)
    if (casas_restantes == 0) {
        return;
    }
    // Imprime a direção do movimento atual.
    printf("%s\n", direcao);
    moverTorre(casas_restantes - 1, direcao);
}
void moverBispo(int casas_restantes, const char* direcao_vertical, const char* direcao_horizontal) {
    if (casas_restantes == 0) {
        return;
    }

    for (int i = 0; i < 1; i++) {
        printf("%s\n", direcao_vertical); // Movimento vertical (externo)

        int j = 0;
        while (j < 1) {
            printf("%s\n", direcao_horizontal);
            j++;
        }
    }

    moverBispo(casas_restantes - 1, direcao_vertical, direcao_horizontal);
}

void moverRainha(int casas_restantes, const char* direcao) {
    if (casas_restantes == 0) {
        return;
    }
    printf("%s\n", direcao);
    
    moverRainha(casas_restantes - 1, direcao);
}

int main() {
    printf("Movimento da Torre:\n");
    
    moverTorre(3, "Cima");

    printf("\n");

    printf("Movimento do Bispo:\n");
  
    moverBispo(2, "Cima", "Direita");
    
    printf("\n");

    printf("Movimento da Rainha:\n");
    moverRainha(4, "Direita");
    printf("\n");

    printf("Movimento do Cavalo:\n");

    const int casas_cima = 2;       // Duas casas para cima
    const int casas_direita = 1;    // Uma casa para a direita

    for (int i = 0; i < casas_cima + casas_direita; ++i) 
        int j = 0;
        int move_vertical = 0;
        int move_horizontal = 0;

        if (i < casas_cima) {
            move_vertical = 1;
        } else {
            move_horizontal = 1;
        }

        while (j < 1)
            if (move_vertical)
                printf("Cima\n");
            } else if (move_horizontal) {
                printf("Direita\n");
                break; // Sai do loop 'while' interno
            }
            j++;
        }
    }

    return 0;
}
