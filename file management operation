
#include<stdio.h>
int main(){

 FILE *fp;
 char ch;

 //code to open file for reading
 fp=fopen("test.txt","r");
 
 if(fp==NULL){
     printf("File error");
     exit(0);
 }

 //code to read a character
 ch = fgetc(fp);
  
 printf("%c",ch);
 fclose(fp);
 
 return 0;
}
