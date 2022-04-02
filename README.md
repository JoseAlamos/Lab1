/******************************************************************************

                            Online C Compiler.
                Code, Compile, Run and Debug C program online.
Write your code in this editor and press "Run" button to compile and execute it.

*******************************************************************************/

#include <stdio.h>

int main() {
    
    char matriz[3][3], nombre_1[50], nombre_2[50];
    int i, j;
    
    printf("¡Que comience el juego! \n\n");
    for(i=0;i<3;i++){
        for(j=0;j<3;j++){
            matriz[i][j] = ' ';
       }
    }
    
    printf("A continuación se muestran las posiciones para elegir \n\n"); 
    printf("   C0 C1 C2 \n"); 
    printf("F0[1][2][3] \n"); 
    printf("F1[4][5][6] \n");
    printf("F2[7][8][9] \n"); 
    printf("\n");
    
    
    do{
        printf("Jugador 1 ingrese su nombre: ");
        scanf("%s" ,nombre_1);
        printf("Jugador 2 ingrese su nombre: ");
        scanf("%s" ,nombre_2);
    if(nombre_1 == nombre_2){
        printf("Ingrese un nombre distinto al Jugador 1");
    }
    }while(nombre_1 == nombre_2);
    
    int fila,col, ganador=0, turno=1;
    do{
        if(turno%2==1){
        
				do{
					printf("\n Turno de %s: \n",nombre_1);
					printf("Ingrese un número de fila: ");
					scanf("%d", &fila);
					printf("Ingrese un número de columna: ");
					scanf("%d", &col);
					
					if(matriz[fila][col] == 'X' || matriz[fila][col] == 'O' || fila > 2 || col > 2){
						printf("\nEspacio ocupado, pruebe otra vez.\n");
					}
				}while(matriz[fila][col] == 'X' || matriz[fila][col] == 'O' || fila > 2 || col > 2);
				
				matriz[fila][col]='X';
        for(i=0;i<3;i++){
            for(j=0;j<3;j++){
                printf("[%c]", matriz[i][j]);
            }
            printf("\n");
        } 
        turno++;
        }else if(turno%2==0){
        
				do{
					printf("\n Turno de %s: \n", nombre_2);
					printf("Ingrese un número de fila: ");
					scanf("%d", &fila);
					printf("Ingrese un número de columna: ");
					scanf("%d", &col);
					
					if(matriz[fila][col] == 'X' || matriz[fila][col] == 'O' || fila > 2 || col > 2){
						printf("\nEspacio ocupado, pruebe otra vez.\n");
					}
				} while(matriz[fila][col] == 'X' || matriz[fila][col] == 'O' || fila > 2 || col > 2);
				
				matriz[fila][col]='O';
        
        for(i=0;i<3;i++){
            for(j=0;j<3;j++){
                printf("[%c]", matriz[i][j]);
            }
            printf("\n");
        }
        turno++;
    }
    
			if(matriz[0][0] == 'X' && matriz[0][0] == matriz[0][1] && matriz[0][0] == matriz[0][2]
			|| matriz[1][0] == 'X' && matriz[1][0] == matriz[1][1] && matriz[1][0] == matriz[1][2]
			|| matriz[2][0] == 'X' && matriz[2][0] == matriz[2][1] && matriz[2][0] == matriz[2][2]
			
			|| matriz[0][0] == 'X' && matriz[0][0] == matriz[1][0] && matriz[0][0] == matriz[2][0]
			|| matriz[0][1] == 'X' && matriz[0][1] == matriz[1][1] && matriz[0][1] == matriz[2][1]
			|| matriz[0][2] == 'X' && matriz[0][2] == matriz[1][2] && matriz[0][2] == matriz[2][2]
			
			|| matriz[0][0] == 'X' && matriz[0][0] == matriz[1][1] && matriz[0][0] == matriz[2][2]
			|| matriz[0][2] == 'X' && matriz[0][2] == matriz[1][1] && matriz[0][2] == matriz[2][0]){
				ganador=1;
				printf("\nFelicidades! Gano el jugador 1.\n");
			}
			
			if(matriz[0][0] == 'O' && matriz[0][0] == matriz[0][1] && matriz[0][0] == matriz[0][2]
			|| matriz[1][0] == 'O' && matriz[1][0] == matriz[1][1] && matriz[1][0] == matriz[1][2]
			|| matriz[2][0] == 'O' && matriz[2][0] == matriz[2][1] && matriz[2][0] == matriz[2][2]
			
			|| matriz[0][0] == 'O' && matriz[0][0] == matriz[1][0] && matriz[0][0] == matriz[2][0]
			|| matriz[0][1] == 'O' && matriz[0][1] == matriz[1][1] && matriz[0][1] == matriz[2][1]
			|| matriz[0][2] == 'O' && matriz[0][2] == matriz[1][2] && matriz[0][2] == matriz[2][2]
			
			|| matriz[0][0] == 'O' && matriz[0][0] == matriz[1][1] && matriz[0][0] == matriz[2][2]
			|| matriz[0][2] == 'O' && matriz[0][2] == matriz[1][1] && matriz[0][2] == matriz[2][0]){
				ganador=1;
				printf("\nFelicidades! Gano el jugador 2.\n");
			}    
    
    
    }while(ganador!=1);
    
    return 0;
}
