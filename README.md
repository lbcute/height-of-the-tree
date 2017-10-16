#include <iostream>
#include<algorithm>
using namespace std;
class Node//定义一个结点类
{
private:
  int element;//element表示该结点存储的数据
  Node *leftchild;//左指针
  Node *rightchild;//右指针
public:
  Node(int data,Node *l=NULL,Node *r=NULL)//结点的初始化
  {
    element=data;
    leftchild=l;
    rightchild=r;
  }
  ~Node()//结点的析构
  {
    if(leftchild!=NULL)
    delete leftchild;
    if(rightchild!=NULL)
    delete rightchild;
    leftchild=rightchild=NULL;
  }
 void addleft(Node *l)//增加左孩子
  {
    leftchild=l;
  }
  void addright(Node *r)//增加右孩子
  {
    rightchild=r;
  }
  int height()//递归求树的高度
  {
    if(this==NULL)
      return 0;
    else
    {
     return max(leftchild->height(),rightchild->height())+1; 
    }
  }
};
int main()
{
  Node *p[100];

int data;
int count=0;
cout<<"请输入数据构造一棵树(输入-1以结束程序，输入数目不超过100)："<<endl;
while(cin>>data)
{
  if(data==-1) break;
  p[count]=new Node(data);
  count++;
  
}
  for(int i=0;i<count;i++)
  {
    if(2*i+1<count)
      p[i]->addleft(p[2*i+1]);
    if(2*i+2<count)
      p[i]->addright(p[2*i+2]);
  }
  cout<<"树的高度是："<<endl;
  cout<<p[0]->height()<<endl;

  
}
