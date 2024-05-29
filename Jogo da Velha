#include <stdio.h>
#include <stdlib.h>
#include <ctype.h>
#include <time.h>

char quadro[3][3];
const char player = 'X';
const char comp = 'O';

void resetQuadro();
void printQuadro();
int  checkEspacoBranco();
void playerMove();
void compMove();
char checkVencedor();
void printVencedor(char);

int main(){
   char vencedor = ' ';
   char resposta = ' ';

   do{
      vencedor = ' ';
      resposta = ' ';
      resetQuadro();

      while(vencedor == ' ' && checkEspacoBranco() != 0){
         printQuadro();

         playerMove();
         vencedor = checkVencedor();
         if(vencedor != ' ' || checkEspacoBranco() == 0){
            break;
         }

         compMove();
         vencedor = checkVencedor();
         if(vencedor != ' ' || checkEspacoBranco() == 0){
            break;
         }
      }

      printQuadro();
      printVencedor(vencedor);

      printf("\nVoce quer jogar de novo? (S/N): ");
      scanf("%c");
      scanf("%c", &resposta);
      resposta = toupper(resposta);
   } while (resposta == 'S');

   printf("Obrigado(a) por jogar!");

   return 0;
}

void resetQuadro(){
   for(int i = 0; i < 3; i++)
   {
      for(int j = 0; j < 3; j++)
      {
         quadro[i][j] = ' ';
      }
   }
}

void printQuadro(){
   printf(" %c | %c | %c ", quadro[0][0], quadro[0][1], quadro[0][2]);
   printf("\n---|---|---\n");
   printf(" %c | %c | %c ", quadro[1][0], quadro[1][1], quadro[1][2]);
   printf("\n---|---|---\n");
   printf(" %c | %c | %c ", quadro[2][0], quadro[2][1], quadro[2][2]);
   printf("\n");
}
int checkEspacoBranco(){
   int espacosLivres = 9;

   for(int i = 0; i < 3; i++)
   {
      for(int j = 0; j < 3; j++)
      {
         if(quadro[i][j] != ' ')
         {
            espacosLivres--;
         }
      }
   }
   return espacosLivres;
}

void playerMove(){
   int x;
   int y;

   do
   {
      printf("Escolha a linha #(1-3): ");
      scanf("%d", &x);
      x--;
      printf("Escolha a coluna #(1-3): ");
      scanf("%d", &y);
      y--;

      if(quadro[x][y] != ' '){
         printf("Movimento invalido!\n");
      }
      else{
         quadro[x][y] = player;
         break;
      }
   } while (quadro[x][y] != ' ');

}

void compMove(){
   srand(time(0));
   int x;
   int y;

   if(checkEspacoBranco() > 0){
      do{
         x = rand() % 3;
         y = rand() % 3;
      } while (quadro[x][y] != ' ');

      quadro[x][y] = comp;
   }
   else{
      printVencedor(' ');
   }
}

char checkVencedor(){
   //verificar linhas
   for(int i = 0; i < 3; i++){
      if(quadro[i][0] == quadro[i][1] && quadro[i][0] == quadro[i][2]){
         return quadro[i][0];
      }
   }
   //verificar colunas
   for(int i = 0; i < 3; i++){
      if(quadro[0][i] == quadro[1][i] && quadro[0][i] == quadro[2][i]){
         return quadro[0][i];
      }
   }
   //verificar diagonais
   if(quadro[0][0] == quadro[1][1] && quadro[0][0] == quadro[2][2]){
      return quadro[0][0];
   }
   if(quadro[0][2] == quadro[1][1] && quadro[0][2] == quadro[2][0]){
      return quadro[0][2];
   }

   return ' ';
}

void printVencedor(char vencedor){
   if(vencedor == player){
      printf("VOCE GANHOU!");
   }else if(vencedor == comp){
      printf("VOCE PERDEU!");
   }else{
      printf("EMPATOU!");
   }
}
