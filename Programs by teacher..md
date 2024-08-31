Address
```cpp
#include <iostream>

using namespace std;
void swap(int& ,int &);
int main(){
 int a=5, b=6;
 cout<<"Before swapping: a="<<a<<" and b="<<b<<endl;
 swap(a,b);
 cout<<"After swapping: a="<< a<<" and b="<<b<<endl;
 return 0;
}
 void swap(int &x,int &y){
 int temp;
 temp=x;
 x=y;
 y=temp;
}

```

Passing obj
```cpp
#include <iostream>

using namespace std;
class Account{
private:
    int balance;
    static float roi;
public:
    void setbalance(int b){
    balance=b;
    }
    static void setroi(float r){
    roi=r;
    cout<<"roi is:"<<roi;
    }
    };

    float Account::roi;

    int main(){
   // Account a1,a2;
    //a1.setroi(4.5f);
    Account::setroi(5.5f);
    return 0;
    }
```
return ref
```cpp
#include <iostream>

using namespace std;
int &max(int &x,int &y){
if(x>y)
    return x;
    else
        return y;
}

int main()
{
    int a=5,b=10;
    cout<<"\n Before calling a="<<a<<"and b="<<b;
    max(a,b)=100;
    cout<<"\n After calling a="<<a<<"and b="<<b;
    return 0;
}
```
namespace
```cpp
#include <iostream>

using namespace std;
//defining a namespace.
namespace Name1{
double x=4.56;
int m=100;
//nesting namespace.
namespace Name2{
double y=1.23;
}
}
//unnamed namespace.
namespace Name3{
int m=200;
int n=300;
}

int main()
{

using namespace Name1;
  cout<<"x="<<Name1::x<<"\n"; //x is qualified
  cout<<"m="<<Name1::m<<"\n";
  cout<<"y="<<Name1::Name2::y<<"\n"; //y is fully qualified.
  using Name3::n;
   cout<<"m="<<Name3::m<<"\n";
   cout<<"n="<<n<<"\n";
    return 0;
}
```
object pointer
```cpp
#include <iostream>

using namespace std;
class ABC{
int a,b,c;
public:
    void setdata(int a,int b,int c){
    this->a=a;
    this->b=b;
    this->c=c;
    }
    void showdata(){
    cout<<"\n a "<<a<<" b "<<b<<" c "<<c<<endl;
    }
};

int main()
{
   ABC abc;
    abc.setdata(1,2,3);
    abc.showdata();

//    ABC *p,abc;
//    p=&abc;
//    p->setdata(1,2,3);
//    p->showdata();
    return 0;
}

```
static class
```cpp
#include <iostream>

using namespace std;
class Account{
private:
    int balance;
    static float roi;
public:
    void setbalance (int b){
    balance=b;
    cout<<"Balance is:"<<balance<<endl;
    }
    static void setroi (float r){
    roi=r;
 cout<<"roi is:"<<roi;
}};

 float Account::roi;
    int main(){
    Account a1;//,a2;
    //Account::setbalance(5000);
     a1.setbalance(34000);
   // a1.setroi(4.5f);  //if object exist.
    Account::setroi(5.5f);  //if there is no object.
    return 0;
    }
```
this pointer
```cpp
#include <iostream>

using namespace std;
class ABC{
int a,b,c;
public:
void setdata(int a,int b,int c){
this->a=a;
this->b=b;
this->c=c;
/*a=a;
b=b;
c=c;*/
}
void showdata(){
cout<<"\n a "<<a<<" b "<<b<<" c "<<c<<endl;
}
};

int main()
{
    ABC abc;
    abc.setdata(1,2,3);
    abc.showdata();
    return 0;
}
```
static cast
```cpp
#include <iostream>

using namespace std;

int main()
{
    float quot;
    int num1=7,num2=9;
    quot=num1/num2;
    cout<<"Without casting:quot="<<quot<<endl;//Wrong result displays 0.
    quot=static_cast<float>(num1)/num2;
    cout<<"After Casting:quot="<<quot<<endl; //right answer.
    return 0;
}
```
mutable
```cpp
#include <iostream>

using namespace std;
class A{

    public:
        mutable int x;
        mutable int y;
        A() : x(4), y(5) { };

  void showdata(){
  cout<<" x: "<<x<<" y: "<<y<<endl;
  }
};

int main()
{
    const A a1;
  a1.x = 345;
  a1.y = 2345;
  cout<<a1.x<<endl;
  cout<<a1.y<<endl;
    return 0;
}
```
assign
```cpp
#include <iostream>

using namespace std;
class Test{
int *a;
public:
    Test(int x=0):a{new int(x)}{}
    void setdata(int x){
    *a=x;
    }
    void showdata(){
    cout<<"Result:"<<*a<<endl;
    }
    ~Test(){
    delete a;
    }
   /* Test & operator =(const Test& t){
    if(this!=&t)
        *a=*t.a;
    return *this;
    }*/
};

int main()
{
    Test t1(20);
    Test t2;
    t2=t1;
    t1.setdata(30);
    t1.showdata();
    t2.showdata();
    return 0;
}
```
Addition of string
```cpp
#include <iostream>

using namespace std;
class Test{
int *a;
public:
    Test(int x=0):a{new int(x)}{}
    void setdata(int x){
    *a=x;
    }
    void showdata(){
    cout<<"Result:"<<*a<<endl;
    }
    ~Test(){
    delete a;
    }
   /* Test & operator =(const Test& t){
    if(this!=&t)
        *a=*t.a;
    return *this;
    }*/
};

int main()
{
    Test t1(20);
    Test t2;
    t2=t1;
    t1.setdata(30);
    t1.showdata();
    t2.showdata();
    return 0;
}
```
Ambiguity
```cpp
#include <iostream>

using namespace std;
class Base1{
public:
    void display(){
    cout<<"This is Base1"<<endl;
    }
};
class Base2{
public:
    void display(){
    cout<<"This is Base2"<<endl;
    }
};
class Derived:public Base1,public Base2{
public:
    //void derive_display(){
//  display();   //error,ambigious which display to call.
    //Base1::display();   //ok base class name is specified.
    //Base2::display();   //ok base class name is specified.
 /* cout<<"*******************************"<<endl;
    cout<<"Here me derived";
    */
    //}//
};

int main()
{
    Derived D;
    //D.derive_display();
 //D.display();   //error ambigious which display to call.
    D.Base1::display();   //display()of Base1 class is called.
    D.Base2::display();   // display() of Base2 class is called.
/*cout<<"*********************************"<<endl;
D.derive_display();*/

    return 0;
}
```
DMA in OO
```cpp
#include <iostream>

using namespace std;
class A
{
	 public:
       	A() {
    	  cout << "Constructor" << endl;
      	}
       	~A() {
    	   cout << "Destructor" << endl;
        }
        void showdata(){
        cout<<"Hello World;";
        }
};

int main()
{
	A* a = new A[4];
	A *b=new A;

	delete b;
	delete [] a; // Delete array
	return 0;
}
```
DynCon
```cpp
#include <iostream>

using namespace std;
class A{
public:
    int *p;
    A(){
    p=new int;
    *p=10;
    }
    A(int y){
    p=new int;
    *p=y;
    }
    int show(){return (*p);}
};

int main()
{
     A a;
     cout<<a.show()<<endl;
     A a1(2);
     cout<<a1.show()<<endl;
    return 0;
}
```
Userpripro
```cpp
#include <iostream>

using namespace std;
class Array{
private:
    int a[10];
public:
    void insert(int index,int value){
    a[index]=value;
    }
};
class Stack:private Array{
int top;
public:
    void push(int value){
    insert(top,value);
    }
};

int main()
{
    Stack s1;
    s1.push(10);
   s1.insert(2,40);
    return 0;
}
```
Pure Derived class
```cpp
#include <iostream>

using namespace std;
class Base
{
              public:
              int x;
              void display ()
              {
                        cout<<"X="<<x<<endl;
              }
};
class Derive: public Base
{
              public:
              int y;
              void display ()
              {
                        cout<<"X="<<x<<endl;
                        cout<<"Y="<<y<<endl;
              }
};
int main ()
{
              Base B1;
              Base *ptr;
              ptr = &B1;
              ptr->x = 10;
              ptr->display();
              Derive D1;
              ptr=&D1;
              ptr->x=20;
              ptr->display();
             // ptr->y=20;
             Derive *ptr1;
              ptr1 = &D1;
              ptr1->x = 10;
              ptr1->y = 20;
              ptr1->display ();
              return 0;
}
```
Pure Virtual Class
```cpp
#include <iostream>

using namespace std;
//Necessary:
//A pure virtual function is implemented by classes which are derived from a Abstract class.
//pure virtual function should be override in derived.
//abstract class object cannot be created.
//But pointer of such class can be made..its okay to do.

//class Base
//{
//   int x;
//public:
//     virtual void fun()=0;//{
//     //cout<<"Hello me"<<endl;}
//     //pure vir fun.
//    int getdata() {
//        return x;
//        }
//};
////
////// This class inherits from Base and implements fun()
//class Derived: public Base
//{
//    int y;
//    private:
//   void fun() {
//       cout << "Derived";
//        }
//};
//
//int main()
//{
//    Base *b;
//    Derived d;
//    //d.fun();
//     b=&d;
//    b->fun();
//    return 0;
//}
#include<iostream>
using namespace std;

class Base
{
public:
    virtual void fun() = 0;
};

class Derived: public Base
{
public:
    void fun() { cout << "In Derived \n"; }
};

int main()
{
    Base *bp = new Derived();
//    Base *bp;
//    Derived obj;
//    bp=&obj;
    bp->fun();
    return 0;
}
/*Output:

In Derived */

```
typeid
```cpp
#include <iostream>
#include<typeinfo>

using namespace std;
class Base{
public:
    virtual void display(){
    cout<<"Here is base class."<<endl;
    }
};
class Derived:public Base{
void display(){
cout<<"Here is derived class."<<endl;
}
};
class Derived1:public Base{
void display(){
cout<<"Here is derived class."<<endl;
}
};
int main()
{
    int mark,roll;
    float avg;
    char *str;
    Base *b;
    Derived d;
    Derived1 d1;
    cout<<"\n Finding types with typeid"<<endl;
    cout<<"-----------------"<<endl;
    cout<<"type of marks is:"<<typeid(mark).name()<<endl;
    cout<<"type of roll is:"<<typeid(roll).name()<<endl;
    cout<<"type of avg is:"<<typeid(avg).name()<<endl;
    cout<<"type of *str is:"<<typeid(*str).name()<<endl;
    cout<<"type of str is:"<<typeid(str).name()<<endl;
    cout<<"type of b is:"<<typeid(b).name()<<endl;
    cout<<"type of d is:"<<typeid(d).name()<<endl;
    cout<<"type of d1 is:"<<typeid(d1).name()<<endl;
    cout<<"\n Finding types with polymorphic types"<<endl;
    cout<<"--------------------"<<endl;
    b=&d;
    cout<<"types of *b when pointing to d is"<<typeid(*b).name()<<endl;
    b=&d1;
    cout<<"types of *b when pointing to d1 is"<<typeid(*b).name()<<endl;

    return 0;
}
```
typeidoperator
```cpp
#include <iostream>
#include<typeinfo>

using namespace std;
class Animal{
public:
    virtual void display(){
    cout<<"Animal Class";
    }
};
class Human:public Animal{
public:
    void display(){
    cout<<"\nHuman Class";
    }
};
class Cow:public Animal{
public:
    void display(){
    cout<<"\n Cow Class";
    }
};
void check(Animal *A1){
cout<<"\n Animal class pointing to object of type"<<typeid(*A1).name();
}

int main()
{
    check (new Human());
    check (new Cow());
    check (new Animal());
    return 0;
}
```
Virtual Destructor
```cpp
#include <iostream>

using namespace std;
class Base{
public:
    Base(){
    cout<<"Base class constructor"<<endl;
    }
   virtual void display(){
    cout<<"Base class display"<<endl;
    }
    virtual ~Base(){
    cout<<"Base class destructor"<<endl;
    }
};
class Derived:public Base{
public:
    Derived(){
    cout<<"Derived class constructor"<<endl;
    }
    void display(){
    cout<<"Derived class display"<<endl;
    }
    ~Derived(){
    cout<<"Derived class Destructor"<<endl;
    }
};

int main()
{
    Base *bp;
//    cout<<"pointer pointing to the base class object"<<endl;
//    bp=new Base;
//    bp->display();
//    delete bp;

    cout<<"pointer pointing to the derived class object"<<endl;
    bp=new Derived;
    bp->display();
    delete bp;
    return 0;
}
```
ConsCast
```cpp
#include <iostream>

using namespace std;
class student
{
private:
    int roll;
public:
    // constructor
    student(int r):roll(r) {}

    // A const function that changes roll with the help of const_cast
    void fun() const
    {
        ( const_cast <student*> (this) )->roll = 5;
    }

    int getRoll()  { return roll; }
};

int main(void)
{
    student s(3);
    cout << "Old roll number: " << s.getRoll() << endl;

    s.fun();

    cout << "New roll number: " << s.getRoll() << endl;

    return 0;
}
```
Stream
```cpp
#include <iostream>

using namespace std;
class Base{
public:
    virtual void display(){
    cout<<"Hello i m base class"<<endl;
    }
};
class Derived:public Base{
public:
    void display(){
    cout<<"Here i m derived class"<<endl;
    }
};
class Derived1:public Base{
public:
    void display(){
    cout<<"Here i m derived 1 class"<<endl;
    }
};

int main()
{
    Base *b,bb;
    Derived *c,d;
    //Derived1 d1;
    b=&bb;
    c=dynamic_cast<Derived *>(b);
    if(c){
        cout<<"Cast succedded"<<endl;
    }
    else{
        cout<<"Cast fails"<<endl;
    }

    return 0;
}
```
UpDown
```cpp
#include <iostream>

using namespace std;
class Parent {
public:
    void sleep() { cout<<"I m sleeping"<<endl;}
};

class Child: public Parent {
public:
  void gotoSchool(){cout<<"I m going to school"<<endl;}
};

int main()
{
    Parent p;
  Child c;

  // upcast - implicit type cast allowed
 Parent *pp = &c;

  // downcast - explicit type case required
   Child *cp =  (Child *) &p;
    //Child *cp=dynamic_cast<Child *>(pp);

  pp -> sleep();
  cp -> gotoSchool();
    return 0;
}
```
ArrayPoint
```cpp
#include <iostream>

using namespace std;
class Shape{
public:
    virtual void display(){
    cout<<"Shape"<<endl;
    }
};
class Triangle:public Shape{
public:
    void display(){
    cout<<"Triangle"<<endl;
    }
};
class Rectangle:public Shape{
public:
   void display(){
    cout<<"Rectangle"<<endl;
    }
};

int main()
{
    Shape sh;
    Triangle t;
    Rectangle r;
    Shape *bptr[]={&sh,&t,&r};
    cout<<"Base pointer does:"<<endl;
    for(int i=0;i<3;i++)
        bptr[i]->display();
    return 0;
}
```
ConCo
```cpp
#include <iostream>

using namespace std;

int main()
{
    //When the actual referred object/variable is not const.

    const int a=1;
    const int *b=&a;
    int *c=const_cast<int*>(b);
    *c=2;  //invalid and undefined behaviour.
    cout<<" a "<<a<<endl;
    cout<<" *c "<<*c<<endl;

   int a1=4;
    const int *b1=&a1;
    int *c1=const_cast<int *>(b1);
    *c1=5;  //valid code
     cout<<" a1 "<<a1<<endl;
    cout<<" *c1 "<<*c1<<endl;
    return 0;
}
//When we need to call some 3rd party library where it is taking variable/object as non const but changing that.
/*void A(int *x){
int k=12;
cout<<k+*(x);
}
int main(){
const int x=10;
const int *p=&x;
A(const_cast<int *>(p));
}*/
```
DynamicCast
```cpp
#include <iostream>

using namespace std;
class Animal{
public:
    virtual void display(){
    cout<<"Here is a display of base"<<endl;
}
};
class Dog:public Animal{
public:
    virtual void display(){
    cout<<"Here is a dog's display"<<endl;
}
};
class Cow:public Animal{
public:
    void display(){
    cout<<"Here is the cow's display"<<endl;
    }
};
int main()
{
    Animal *a,b;
    Dog *d,e;
    a=&e;
    d=dynamic_cast<Dog*>(&b);
    if(d){
        cout<<"Cast succeeded"<<endl;
    }
    else{
        cout<<"Cast failed"<<endl;
    }
    return 0;
}
```
virtu
```cpp
#include <iostream>

using namespace std;


int main()
{
    int a=10;
    float *d=reinterpret_cast<float *>(a);
    int f=reinterpret_cast<int>(d);
    cout<<d<<" "<<f<<" "<<a<<" "<<&a<<" "<<&f;
    return 0;
}
```
VirtualFunction
```cpp
#include <iostream>

using namespace std;
class A{
public:
    virtual void display(){    //virtual function.
    cout<<"Base class"<<endl;
    }
};
class A1:public A{
public:
    void display(){
    cout<<"Derived class 1"<<endl;
    }
};
class A2:public A{
public:
    void display(){
    cout<<"Derived class 2"<<endl;
    }
};
class A3:public A{
public:
    void display(){
    cout<<"Derived class 3"<<endl;
    }
};

int main()
{
    A *ptr,a;
    A1 obj1;
    A2 obj2;
    A3 obj3;
    ptr=&a;
    ptr->display();
    ptr=&obj1;
    ptr->display();
    ptr=&obj2;
    ptr->display();
    ptr=&obj3;
    ptr->display();
    return 0;
}
```
errorwork
```cpp
#include <iostream>
#include<fstream>

using namespace std;

int main()
{
	char fileName[] = "data.txt";
	ifstream infile(fileName);

	if(infile)
		cout << infile.rdbuf();
	else
		cerr << "Error while opening the file " << fileName <<endl;
       /* int integerValue;


     // display results of cin functions
     cout << "Before a bad input operation:"

        << "\ncin.rdstate(): " << cin.rdstate()
         << "\n    cin.eof(): " << cin.eof()
        << "\n   cin.fail():"<<cin.fail();*/
    return 0;
}
```
Formatted
```cpp
#include <iostream>

using namespace std;

int main()
{
    int y=1234;
    float x=5.3400;
    cout.setf(ios::internal,ios::adjustfield);//left justified.
    //cout.setf(ios::hex,ios::basefield);
    //cout.setf(ios::scientific,ios::floatfield);
    //cout.setf(ios::showbase);
    //cout.setf(ios::uppercase);
          //cout.setf(ios::boolalpha);
         //cout<<true<<endl;
        // cout.setf(ios::showpos);
        //cout.unsetf(ios::left);
    //cout.width(4);
   // cout.fill('*');
   // cout<<345;
    cout.width(6);
    cout.fill('#');
    cout<<y<<endl;
    cout.precision(4);
    cout.setf(ios::showpoint);
    cout<<"x="<<x<<endl;
    return 0;
}
```
get
```cpp
#include <iostream>
#include<cstring>

using namespace std;
const int Max=50;
char str1[Max];
char str2[Max];

int main()
{
//    cout<<"Enter a string terminated by newline:"<<endl;
//    cin.get(str1,Max);
//    cin.ignore(5,'*');
//    cout<<"Enter multiline string terminated by ,"<<endl;
    cin.getline(str2,Max,'*');
    cout<<"String you entered are:"<<endl;
   // cout<<"String1:"<<str1<<endl;
    cout<<"String2:"<<str2<<endl;
    return 0;
}

//int main(){
//    char str[]="GNU is not linux";
//   cout.write(str,1);
//   cout.write(str,strlen(str));
//    for(int i=1;i<=strlen(str);i++){
//        cout.write(str,i);
//        cout<<endl;
//    }
//return 0;
//}
```
getandput
```cpp
#include <iostream>
#include<string.h>


using namespace std;

int main()
{
    //char a;
  char str[20];
    cout<<"Enter a character:";
//    a=cin.get();
//    cout.put(a);

    cout<<"\n The entered character is:";

    for( int i=0;i<strlen(str);i++)
   {cin.get(str[20]);
       cout.put(str[i]);}
//    cout<<"enter the string :"<<endl;
//    cin>>str;
//    cout<<"entered text is :";
//    cout<<str;
    return 0;
}
```
ifstream
```cpp
#include <iostream>
#include<fstream>
#include<conio.h>

using namespace std;

int main()
{
     char ch;
     ifstream fin("abcd.txt",ios_base::in|ios_base::ate);
     fin>>ch;
    while(!fin.eof()){
        cout<<ch;
        fin>>ch;
        break;
     }
     fin.close();
     getch();
    return 0;
}
```
iostream
```cpp
#include <iostream>

using namespace std;
class Test{
int x;
public:
   // Test(int x=0):x{x}{}
    Test(){x=0;}
    friend istream & operator >>(istream &,Test &t1);
    friend ostream & operator <<(ostream &,Test &t1);
};
istream & operator >>(istream &input ,Test &t1){
input>>t1.x;
return input;
}
ostream & operator <<(ostream & output,Test &t1){
output<<t1.x;
return output;
}
int main()
{
    Test t;
    cout<<t;
    //cout<<t;     cout//operator.<<(cout,t);
    cin>>t;
    cout<<"Result is";
    cout<<t;     //operator.>>(cin,t);
    return 0;
}
```
manip
```cpp
#include<iostream>
#include<iomanip>   //for setw()


using namespace std;

int main()
{
    int num1=12345,num2=2356;
    float num=70.6776;
    int Basic=20,Allowance=95,Total=1045;
    cout<<"num1"<<setw(20)<<setfill('*')<<num1<<endl;
    cout<<"num2="<<setfill('$')<<setw(8)<<num2<<endl;

    cout<<setw(10)<<"Basic"<<setw(12)<<Basic<<endl
        <<setw(10)<<"Allowance"<<setw(10)<<Allowance
        <<setw(10)<<"Total"<<setw(10)<<Total<<endl;
    cout<<"Number with precision three="<<setprecision(3)<<num<<endl;

       return 0;
}
```
Manipulator
```cpp
#include <iostream>
#include<iomanip>

using namespace std;

int main()
{
    int a=10;
    cout<<setw(2)<<"HI"<<setw(8)<<"HELLO"<<endl
    <<setw(2)<<"ME"<<setw(8)<<a<<endl;
    return 0;
}
```
Manipulators
```cpp
#include <iostream>
#include<iomanip>
using namespace std;

//userdefined manipulator.
ostream & pro(ostream &output)
{
    output.setf(ios::showpoint);
    output<<setprecision(8);
    output<<setfill('*');
    output.width(15);
    return output;
    }
    int main()
    {
        cout<<pro<<100.00<<endl;
        cout<<pro<<12000.00;
         return 0;
    }
    /*int x=1234;
    char str[]={'n','e','p','a','l'};
    cout<<str<<ends;
    cout<<hex<<x<<endl;
   /* char name[20];
    cout<<"Enter name:"<<endl;
    cin>>name;
    cout<<"Name is:"<<name<<endl;
    cin.ignore(15,'i');
    cout<<"Enter name again:"<<endl;
    cin.getline(name,15);
    cout<<"Now name is:"<<name<<endl;
     cout<<"Enter another name again:"<<endl;
    cin.getline(name,15);
    cout<<"Now new name is:"<<name<<endl;*/
//    return 0;
//}
```
uff
```cpp
#include <iostream>

using namespace std;

int main()
{
    char str[20];
    cout<<"Enter text:"<<endl;
    cin.get(str,20);
    cout<<"Text is:"<<endl;
   // cout.put(c);
   cout<<str<<endl;
    cout.precision(4);
    cout<<2.234242422;

    return 0;
}
```
unformatted
```cpp
#include <iostream>
#include<cstring>

using namespace std;

int main()
{

 //use of getline()
 char ch='t';
  char s[10];
  cout<<"Enter text and terminate by t:"<<endl;
  cin.getline(s,10,ch);
  cout<<s;


 // use of ignore()
//  int a;
//  char str[20];
//  cout<<"Enter number:"<<endl;
//  cin>>a;
//  cin.ignore();
//  cout<<"Enter text:"<<endl;
//  cin.getline(str,20);
//  cout<<str;
//  cout<<a;


  //use of write()
 /* char name[20];
  cout<<"Enter your name";
  cin.getline(name,10);
  cout<<"\n Name:"<<endl;
  cout.write(name,20);
  cout<<"\n Name:"<<name<<endl;*/


  //use of read()
  char str[10];
  cout<<"Enter a string:"<<endl;
  cin.read(str,10);
  //str[9]='\0';
  cout<<"You entered:"<<str<<endl;


    return 0;
}
```
compu
```cpp
#include <iostream>
#include<fstream>
#include<iomanip>
using namespace std;
class Product{
char name[20];
int price;
int code;
public:
    void getdata(){
    cout<<"Enter name,price and code of product:"<<endl;
    cin>>name>>price>>code;
    }
    void putdata(){
    cout<<setw(10)<<name<<setw(10)<<setprecision(4)<<price<<setw(10)<<code<<endl;
    }
};

int main()
{
    Product P;
    fstream iofile;    //input/output file.
    iofile.open("Item.txt",ios::in|ios::out|ios::ate|ios::binary);
    iofile.seekg(0,ios::beg);    //go to start.
    cout<<"Current Items:"<<endl;
    while(iofile.read((char*)&P,sizeof(P))){
        P.putdata();
          }
          iofile.close();
          cout<<"Add more items:"<<endl;
    P.getdata();
        char ch;
    cin.get(ch);
    iofile.write((char*)&P,sizeof(P));
    iofile.seekg(0);  //go to start.

    /*ofstream fout;
    fout.open("Abc.txt");
    fout<<"Hello Here me";
    fout.close();*/
    return 0;
}
```
dddd
```cpp
#include <iostream>
#include<fstream>

using namespace std;

int main()
{
   /* ofstream fout;
    fout.open("etc.txt",ios::out);
    fout<<"Hello there "<<endl;
    fout.close();
    fout.open("etc.txt",ios::out|ios::ate|ios::app);
    fout<<"Hi me here"<<endl;
    fout.close();*/
     fstream file;
    //open file sample.txt in and Write mode
    file.open("show.txt",ios::out);
    if(!file)
    {
        cout<<"Error in creating file";
        return 0;
    }
    //write A to H
    file<<"ABCDEFGH";
    //print the position
    cout<<"Current position is: "<<file.tellp()<<endl;
    file.close();

    //again open file in read mode
    file.open("sample.txt",ios::in);
    if(!file)
    {
        cout<<"Error in opening file";
        return 0;
    }
    cout<<"After opening file position is: "<<file.tellg()<<endl;

    //read characters untill end of file is not found
    char ch;
    while(!file.eof())
    {
        cout<<"At position : "<<file.tellg();   //current position
        file>>ch;   //read character from file
        cout<<" Character \""<<ch<<"\""<<endl;
    }

    //close the file
    file.close();

    return 0;
}
```
ifstream
```cpp
#include <iostream>
#include<fstream>
//#include<iomanip>

using namespace std;

int main()
{
      ofstream myfile;
  myfile.open ("data.txt",ios::out|ios::ate);
 myfile<<"hello me.\n";
 myfile.close();


  myfile.open ("data.txt",ios::out|ios::ate);
 myfile << "I m a programmer.\n";
 myfile.close();
//  myfile.open("date.txt",ios::out);
//  myfile<<"hguwkjbcd"<<endl;
//  ifstream fin("data.txt");
//  fin.seekg(2,ios_base::beg);

//    int a=10;
//    ofstream output;
//    output.open("hello.txt");
//    output<<a;
//    output<<"Hello this is me here"<<endl;
//
//    ifstream input;
//    input.open("hello.txt");
//    input>>a;
//    output<<a;

    return 0;
}
```
ifstream
```cpp
#include <iostream>
#include<fstream>
#include<cstring>

using namespace std;

class Person{
char name[20];
int age;
public:
    Person(){
    strcpy(name,"noname");
    age=0;
    }
    Person(char *name,int age){
    strcpy(this->name,name);
    this->age=age;
    }
    void Hello(){
    cout<<"I am "<<name<<" and i m "<<age<<" years old"<<endl;
    }
};
int main()
{
   Person Ram("Ram",20);
   fstream file("person.txt",ios::out|ios::in|ios::binary|ios::app);
   if(!file.is_open())
    cout<<"error while opening the file";
   else{
   file.write(reinterpret_cast<char*>(&Ram),sizeof(Person));
   //file.seekg(0);
}
   Person Anjali;
   file.read(reinterpret_cast<char*>(&Anjali),sizeof(Person));
   Ram.Hello();
   Anjali.Hello();
    file.close();
    return 0;
}
```
