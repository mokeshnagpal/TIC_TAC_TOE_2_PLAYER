#include <stdio.h>
#include <ctype.h>
#include <stdlib.h>
#include <conio.h>
#include <graphics.h>
#include <string.h>
#include <math.h>
class ttt
{
  int xmax,ymax,p;
  char arr[10],as[7],bs[7];
  char a[80],b[80];
  int gmode,errorcode,gdriver;
  public:
  ttt()
  {
    bs[0]=bs[1]=bs[2]=bs[3]=bs[4]=bs[5]=bs[6]='\0';
    as[0]=as[1]=as[2]=as[3]=as[4]=as[5]=as[6]='\0';
    arr[0]=arr[1]=arr[2]=arr[3]=arr[4]=arr[5]=arr[6]=arr[7]=arr[8]=arr[9]='\0';
    p=0;
    gdriver=DETECT;
    gmode=0,errorcode=0;
    initgraph(&gdriver,&gmode,"C:\\TURBOC3\\BGI");
    errorcode=graphresult();
    if(errorcode!=grOk)
    {
      printf("Graphics error : %s\n",grapherrormsg(errorcode));
      printf("Press any key to exit\n");
      getch();
      exit(0);
    }
    xmax=getmaxx();
    ymax=getmaxy();
    setfillstyle(1,7);
    setcolor(RED);
  }
  int winner(char *);
  int checkenter(char);
  void detail();
  void box();
  void play();
  ~ttt()
  {
  }
};
void ttt::detail()
{
  printf("Input your name player 1 (Person won wants to play first)\n");
  scanf("%[^\n]",a);
  fflush(stdin);
  printf("Input your name player 2\n");
  scanf("%[^\n]",b);
  fflush(stdin);
  clrscr();
  a[0]=toupper(a[0]);
  b[0]=toupper(b[0]);
}
int ttt::checkenter(char ch)
{
  int i=0;
  int l=strlen(arr);
  for(i=0;i<l;i++)
  {
    if(arr[i]==ch)
      return 0;
  }
  arr[l]=ch;
  return 1;
}
int ttt::winner(char *q)
{
  char *ptr5=strchr(q,'5');
  char *ptr1=strchr(q,'1');
  char *ptr9=strchr(q,'9');
  if(ptr5!=NULL)
  {
    if(ptr1!=NULL&&ptr9!=NULL)
    {
      line(190,70,450,330);
      return 0;
    }
    else if(strchr(q,'4')!=NULL&&strchr(q,'6')!=NULL)
    {
      line(190,200,450,200);
      return 0;
    }
    else if(strchr(q,'2')!=NULL&&strchr(q,'8')!=NULL)
    {
      line(320,70,320,330);
      return 0;
    }
    else if(strchr(q,'7')!=NULL&&strchr(q,'3')!=NULL)
    {
      line(450,70,190,330);
      return 0;
    }
  }
  else if(ptr9!=NULL)
  {
    if(strchr(q,'3')!=NULL&&strchr(q,'6')!=NULL)
    {
      line(420,70,420,330);
      return 0;
    }
    else if(strchr(q,'7')!=NULL&strchr(q,'8')!=NULL)
    {
      line(190,300,450,300);
      return 0;
    }
  }
  else if(ptr1!=NULL)
  {
    if(strchr(q,'2')!=NULL&&strchr(q,'3')!=NULL)
    {
      line(190,100,450,100);
      return 0;
    }
    else if(strchr(q,'7')!=NULL&&strchr(q,'4')!=NULL)
    {
      line(220,70,220,330);
      return 0;
    }
  }
  return 1;
}
void ttt::box()
{
  bar(0,0,xmax,ymax);
  outtextxy(xmax/2-60,10,"TIC TAC TOE GAME");
  line(170,50,170,350);
  line(170,350,470,350);
  line(470,350,470,50);
  line(470,50,170,50);
  line(270,50,270,350);
  line(370,50,370,350);
  line(170,150,470,150);
  line(170,250,470,250);
  outtextxy(180,140,"1");
  outtextxy(280,140,"2");
  outtextxy(380,140,"3");
  outtextxy(180,240,"4");
  outtextxy(280,240,"5");
  outtextxy(380,240,"6");
  outtextxy(180,340,"7");
  outtextxy(280,340,"8");
  outtextxy(380,340,"9");
}
void ttt::play()
{
  int w=1,x=10,y=10;
  char c='\0';
  char txt[80];
  while(1)
  {
    if(p==0)
    {
      strcpy(txt,a);
      strcat(txt,", Input where you want to place cross(X) from 1-9");
    }
    else
    {
      strcpy(txt,b);
      strcat(txt,", Input where you want to place circle(O) from 1-9");
    }
    outtextxy(10,400,txt);
    while(1)
    {
      c=getch();
      if((int)c<49||(int)c>57)
      {
	bar(0,380,xmax,ymax);
	outtextxy(10,400,"Wrong input !!!");
	outtextxy(10,415,"Please try again.");
	outtextxy(10,430,txt);
      }
      else if(checkenter(c)==0)
      {
	bar(0,380,xmax,ymax);
	outtextxy(10,400,"Already filled !!!");
	outtextxy(10,415,"Please try again.");
	outtextxy(10,430,txt);
      }
      else
	break;
    }
    bar(0,380,xmax,ymax);
    switch(c)
    {
      case '1':
      x=0,y=0;
      break;
      case '2':
      x=1,y=0;
      break;
      case '3':
      x=2,y=0;
      break;
      case '4':
      x=0,y=1;
      break;
      case '5':
      x=1,y=1;
      break;
      case '6':
      x=2,y=1;
      break;
      case '7':
      x=0,y=2;
      break;
      case '8':
      x=1,y=2;
      break;
      case '9':
      x=2,y=2;
      break;
    }
    if(p==0)
    {
      line(190+100*x,70+100*y,190+60+100*x,70+60+100*y);
      line(190+60+100*x,70+100*y,190+100*x,70+60+100*y);
      as[strlen(as)]=c;
      w=winner(as);
      if(w==0)
      {
	bar(0,380,xmax,ymax);
	strcpy(txt,"GAME IS WON BY ");
	strcat(txt,a);
	outtextxy(10,400,txt);
	getch();
	closegraph();
	exit(0);
      }
      p=1;
    }
    else
    {
      circle(220+100*x,100+100*y,30);
      bs[strlen(bs)]=c;
      w=winner(bs);
      if(w==0)
      {
	bar(0,380,xmax,ymax);
	strcpy(txt,"GAME IS WON BY ");
	strcat(txt,b);
	outtextxy(10,400,txt);
	getch();
	closegraph();
	exit(0);
      }
      p=0;
    }
    if((int)arr[8]>=49&&(int)arr[8]<=57)
    {
      bar(0,380,xmax,ymax);
      outtextxy(10,400,"GAME IS DRAW");
      getch();
      closegraph();
      exit(0);
    }
  }
}
void main()
{
  ttt z;
  z.detail();
  z.box();
  z.play();
}