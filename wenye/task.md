```c
#include<stdio.h>
#include<string.h>
#include<stdlib.h>

typedef struct BOOK
{
    char *name;
    int number;
    int flag;
    struct BOOK *next;
}book;
book list[50];
int i,j=0;
void input();
book creat(int n);
void print(int);
void modify(int);
int menu(void);
int main()
{
    printf()
	int i,m,s=0;
	for(i=0;i<50;i++)
	{
		list[i].name=(char *)malloc(20*sizeof(char));
		list[i].number=i+1;
		list[i].flag=0;
	}
	for(i=0;;)
	{
		switch(menu())
		{
		case 1:
			input();
			break;
		case 2:
			printf("input the number\n");
	        scanf("%d",&m);
			print(m);
			break;
		case 3:
			printf("input the number");
	        scanf("%d",&s);
			modify(s);
			break;
		case 4:
			s=1;
			break;
		}
		if(s==1)
			break;
	}
	printf("thanks\n");
	for(i=0;i<50;i++)
	{
		free(list[i].name);
	}

	return 0;
}
int menu(void)
{
	char c,str[20];
	printf("\t\t  1 add\n");
	printf("\t\t  2 show\n");
	printf("\t\t  3 modify\n");
	printf("\t\t  4 quit\n");
	fflush(stdin);
	gets(str);
	c=str[0];
	while(c<'1'||c>'4')
	{
		printf("error   input again\n");
		gets(str);
		c=str[0];
	}
	return c-'0';
}
void input()
{
	char a,str[20],sign='n',*p;
    printf("input the name %d\n",j+1);
	while(scanf("%s",str)==1)
	{
		a=str[0];
		if(a=='*')
			break;
		strcpy(list[j].name,str);
		list[j].flag++;
		j++;
		printf("print * to quit\n");
		printf("input the name %d\n",j+1);
		fflush(stdin);
	}

}
void print(int n)
{

	if(n>0&&n<50)
	printf("%d    %s\n",list[n-1].number,list[n-1].name);
	else
		printf("error");
	if(list[n].flag==0)
		printf("no exist\n");
}
void modify(int n)
{
	char str[20];
	fflush(stdin);
	print(n);
	printf("modify it\n");
	gets(str);
	strcpy(list[n-1].name,str);
	print(n);
}*/
book creat(int n)
{
    book *head,*end,*node;
    char str[20];
    head=(book *)malloc(sizeof(book));
    end=head;
    printf("input the name %d\n",j+1);
    for(;j<n;j++)
    {
        printf("please input the name %d\n",j);
        scanf("%s",str);
        strcpy(node->name,str);
        fflush(stdin);
        end->next=node;
        end=node;
    }
    end->next=NULL;
}

```

