#include <stdio.h>
#include <stdlib.h>
#include <conio.h>
int width = 20, height = 20;
int gameover;
int x, y, fruitX, fruitY, score, flag; //x and y for snakes head
void setup()
{
   gameover = 0;
   x = width / 2;
   y = height / 2;
label1: //so that fruit stay within the sqr
   fruitX = rand() % 20;
   if (fruitX == 0)
      goto label1;
label2:
   fruitY = rand() % 20;
   if (fruitY == 0)
      goto label2;
   score = 0;
}

void draw()
{
   int i, j;
   system("cls");
   for (i = 0; i < width; i++)
   {
      for (j = 0; j < height; j++)
      {
         if (i == 0 || i == height - 1 || j == 0 || j == width - 1)
         {
            printf("*");
         }
         else
         {
            if (i == x && j == y)
               printf("0");
            else if (i == fruitX && j == fruitY)
               printf("F");
            else
               printf(" ");
         }
      }
      printf("\n");
   }
}
void input()
{
   if (kbhit)
   {
      switch (getch())
      {
      case 'a':
         flag = 1;
         break;
      case 's':
         flag = 2;
         break;
      case 'w':
         flag = 3;
         break;
      case 'z':
         flag = 4;
         break;
      case 'x':
         gameover = 1;
         break;
      }
   }
}
void MakeLogic()
{
   switch (flag)

   {
   case 1:
      y--;
      break;
   case 2:
      y++;
      break;
   case 3:
      x--;
      break;
   case 4:
      x++;
      break;

   default:
      break;
   }
}
int main()
{
   setup();
   while (1)
   {
      draw();
      input();
      MakeLogic();
   }

   return 0;
}
