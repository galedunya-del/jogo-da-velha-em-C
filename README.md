# jogo-da-velha-em-C
#include <stdio.h>

int main()
{
    char tabu[3][3];
    char marcador;
    int lin, col;

    for (int i = 0; i < 3; i++)
    {
        for (int j = 0; j < 3; j++)
        {
            tabu[i][j] = '+';
        }
    }

    int jgds = 0;
    int jAtual = 1;
    int jgAtivo = 1;
    int ganhou = 0;

    printf("===JOGO DA VELHA===\n");
    printf("Jogador 1 : `X` || Jogador 2 : `O`\n");

    while (jgAtivo == 1 && jgds < 9)
    {
        if (jAtual == 1)
        {
            marcador = 'X';
        }
        else
        {
            marcador = 'O';
        }
        printf("Jogador %d (%c), digite a linha e a coluna (Ex: 1 1): ", jAtual, marcador);
        scanf("%d %d", &lin, &col);

        if (lin >= 0 && lin < 3 && col >= 0 && col < 3 && tabu[lin][col] == '+')
        {
            tabu[lin][col] = marcador;

            printf("Jogada be sucedida!!\n");

            for (int i = 0; i < 3; i++)
            {
                for (int j = 0; j < 3; j++)
                {
                    printf(" %c ", tabu[i][j]);
                }
                printf("\n");
            }
            printf("\n");

            ganhou = 0;

            for (int k = 0; k < 3; k++)
            {
                if ((tabu[k][0] == marcador && tabu[k][1] == marcador && tabu[k][2] == marcador) || (tabu[0][k] == marcador && tabu[1][k] == marcador && tabu[2][k] == marcador))
                {
                    ganhou = 1;
                }
            }
            if ((tabu[0][0] == marcador && tabu[1][1] == marcador && tabu[2][2] == marcador) || (tabu[0][2] == marcador && tabu[1][1] == marcador && tabu[2][0] == marcador))
            {
                ganhou = 1;
            }

            if (ganhou == 1)
            {
                printf("Parabens! O jogador %d ganhou!! \n", jAtual);
                jgAtivo = 0;
            }
            else
            {
                jgds++;
                if (jAtual == 1)
                {
                    jAtual = 2;
                }
                else
                {
                    jAtual = 1;
                }
            }
        }
        else
        {
            printf("Jogada invalida!! Tente novamente! \n\n");
        }
    }
    if (jgds == 9 && jgAtivo == 1)
    {
        printf("Empate!!\n");
    }
    return 0;
}
