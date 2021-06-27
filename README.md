# my-repo
#include<stdio.h>
#include<malloc.h>
#include<conio.h>

struct LLnode{
       int coeff;
       int pow;
       struct LLnode *next;
       };

struct LLnode *poly1=NULL,*poly2=NULL,*poly=NULL;
void create(struct LLnode *node)
{
 char ch;
 do
 {
  printf("\n enter coeff:");
  scanf("%d",&node->coeff);
  printf("\n enter power:");
  scanf("%d",&node->pow);
  node->next=(struct LLnode*)malloc(sizeof(struct LLnode));
  node=node->next;
  node->next=NULL;
  printf("\n continue(y/n):");
  ch=getch();
 }
 while(ch=='y' || ch=='Y');
}

void show(struct LLnode *node)
{
 while(node->next!=NULL)
 {
  printf("%dx^%d",node->coeff,node->pow);
  node=node->next;
  if(node->next!=NULL)
   printf("+");
 }
}
void polyadd(struct LLnode *poly1,struct LLnode *poly2,struct LLnode *poly)
{
     while(poly1->next &&  poly2->next)
     {
      if(poly1->pow>poly2->pow)
      {
       poly->pow=poly1->pow;
       poly->coeff=poly1->coeff;
       poly1=poly1->next;
       }
      else if(poly1->pow<poly2->pow)
      {
       poly->pow=poly2->pow;
       poly->coeff=poly2->coeff;
       poly2=poly2->next;
       }
      else
      {
       poly->pow=poly1->pow;
       poly->coeff=poly1->coeff+poly2->coeff;
       poly1=poly1->next;
       poly2=poly2->next;
       }
      poly->next=(struct LLnode *)malloc(sizeof(struct LLnode));
      poly=poly->next;
      poly->next=NULL;
     }
     while(poly1->next || poly2->next)
     {
      if(poly1->next)
      {
       poly->pow=poly1->pow;
       poly->coeff=poly1->coeff;
       poly1=poly1->next;
       }
      if(poly2->next)
      {
       poly->pow=poly2->pow;
       poly->coeff=poly2->coeff;
       poly2=poly2->next;
       }
       poly->next=(struct LLnode *)malloc(sizeof(struct LLnode));
       poly=poly->next;
       poly->next=NULL;
       }
}
main()
{
      char ch;
      do{
      poly1=(struct LLnode *)malloc(sizeof(struct LLnode));
      poly2=(struct LLnode *)malloc(sizeof(struct LLnode));
      poly=(struct LLnode *)malloc(sizeof(struct LLnode));
      printf("\nenter 1st Polynomial:");
      create(poly1);
      printf("\nenter 2nd Polynomial:");
      create(poly2);
      printf("\n1st Number:");
      show(poly1);
      printf("\n2nd Number:");
      show(poly2);
      polyadd(poly1,poly2,poly);
      printf("\nAdded polynomial:");
      show(poly);
      printf("\n add two more numbers:");
      ch=getch();
      }
      while(ch=='y' || ch=='Y');
}
