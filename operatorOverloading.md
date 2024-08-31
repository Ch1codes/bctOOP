Write a program to add two string.
```cpp
#include <iostream>

#include <string>

using namespace std;

class add{

private:

string name;

public:

add () {}

add(string s){

name =s;

}

add operator +(add st){

add temp;

temp.name = name + st.name;

return temp.name;

}

void display() {

cout<<"final "<<name<<endl;

}

};

int main() {

add a("Heil"), b("Hitler"), c;

// a.display();

// b.display();

c=a+b;

c.display();

return 0;

}
```

Write a program to overload insertion and extraction operators
```cpp
#include<iostream>

using namespace std;

class myclass{

private:

int x;

public:

myclass(){}

friend istream& operator >> (istream &input, myclass &obj);

friend ostream& operator <<(ostream &output, myclass &obj);

};

istream& operator >> (istream &input, myclass &obj){

input>>obj.x;

return input;

}

ostream& operator <<(ostream &output, myclass &obj){

output<<obj.x;

return output;

}

int main() {

myclass m;

cout<<"enter: \n";

cin>>m;

cout<<"display: \n";

cout<<m;

return 0;

}
```

Write a program to overload relational operators
```cpp


#include<iostream>

using namespace std;

class rel{

private:

int x;

public:

rel (){}

rel (int n){

x =n;

}

int display(){

return x;

}

bool operator >= (rel &a){

if (x>=a.x)

return true;

else

return false;

}

bool operator <= (rel &a){

if (x<=a.x)

return true;

else

return false;

}

bool operator == (rel &a){

if (x==a.x)

return true;

else

return false;

}

bool operator >(rel &a){

if (x>a.x)

return true;

else

return false;

}

bool operator < (rel &a){

if (x<a.x)

return true;

else

return false;

}

bool operator != (rel &a){

if (x!=a.x)

return true;

else

return false;

}

  

};

int main(){

rel d(10), e(20);

if (d>e)

cout<<d.display()<<" is greater than "<<e.display()<<endl;

else if (d<e)

cout<<d.display()<<" is smaller than "<<e.display()<<endl;

else

cout<<d.display()<<" is equal to "<<e.display()<<endl;

  

}
```

Write a program to compare two strings
```cpp
#include <iostream>

#include <string>

using namespace std;

class add{

private:

string str, result;

public:

add () {}

add(string s){

str =s;

}

bool operator ==(add n){

if (str == n.str){

return true;

}

else {

return false;

}

}

};

int main() {

add a("chandish"), b("chandish");

if (a==b){

cout<<"equal"<<endl;

}

else {

cout<<"unequal"<<endl;

}

return 0;

}
```

Write a program to overload unary operators
```cpp
//wap to overload prefix and postfix operators
//we will do prefix operators using member functions
//we will do postfix operators using friend functions
#include<iostream>
using namespace std;
class myclass{
private:
int a;
public:
myclass (int n=0) {
a=n;
}
myclass& operator -(){
a=-a;
return *this;
myclass& operator ++(){
a=++a;
return *this;
}
myclass& operator --(){
a=--a;
return *this;
}
friend myclass operator --(myclass& b, int c);
friend myclass operator ++ (myclass& b, int c);
void display() {
cout<<a<<endl;
}
};
myclass operator --(myclass& b, int c) {
myclass temp(b.a);
temp.a=b.a--;
return temp;
}
myclass operator ++ (myclass& b, int c) {
myclass temp(b.a);
temp.a=b.a++;
return temp;
}
int main() {
myclass m(10), n(20), o(30), p(40), q(50);
cout<<"the values are: "<<endl;
m.display();
n.display();
o.display();
p.display();
q.display();
m=-m;
n=++n;
o=--o;
p=p++;
q=q++;
cout<<"the values after unary operations are:"<<endl;
m.display();
n.display();
o.display();
p.display();
q.display();
return 0;
}
```

 Write a program to add two land measures using the concept of operator overloading
```cpp
#include <iostream>

using namespace std;

class landMeasure{

private:

int ropani, ana, paisa, dam;

public:

landMeasure(int r=0, int a=0, int p=0, int d=0):ropani(r), ana(a), paisa(p), dam(d){

}

void display(){

cout<<"ropani:\t"<<ropani<<"\tana:\t"<<ana<<"\tpaisa:\t"<<paisa<<"\tdam:\t"<<dam<<endl;

}

landMeasure operator + (landMeasure l){

landMeasure t;

t.dam=dam+l.dam;

t.ropani=ropani+l.ropani;

t.paisa=paisa + l.paisa;

t.ana=ana + l.ana;

if (t.dam>=4){

t.paisa+=(t.dam/4);

t.dam=(t.dam%4);

}

if (t.paisa>=4){

t.ana+=(t.paisa/4);

t.paisa=(t.paisa%4);

}

if (t.ana>=16){

t.ropani+=(t.ana/16);

t.ana=(t.ana)%16;

}

return t;

}

};

int main(){

landMeasure l1(16,16,16,16), l2(1, 1, 1, 1), l3;

l3=l1+l2;

l3.display();

return 0;

}
```

 Write a program to overload *  to multiply two 3 *  3 matrices
```cpp
#include<iostream>

using namespace std;

class matrix{

private:

int a[3][3];

public:

void readMatrix(){

for(int i=0; i<3; i++){

for(int j=0; j<3; j++){

cout<<"enter element\n";

cin>>a[i][j];

}

}

}

void displayMatrix(){

for (int i=0; i<3; i++){

for (int j=0; j<3; j++){

cout<<a[i][j]<<"\t";

}

cout<<"\n";

}

}

matrix operator * (matrix n){

matrix temp;

for (int i=0; i<3; i++){

for(int j=0; j<3; j++){

temp.a[i][j]=0;

for (int k=0; k<3; k++){

temp.a[i][j]+=a[i][k]*n.a[k][j];

}

}

}

return temp;

}

};

int main() {

matrix p, q, r;

cout<<"enter first matrix"<<endl;

p.readMatrix();

cout<<"enter second matrix"<<endl;

q.readMatrix();

r=p*q;

cout<<"product: "<<endl;

r.displayMatrix();

return 0;

}
```


Overloading index operator
```cpp
#include<iostream>

using namespace std;

class myclass{

private:

int a[5];

public:

void getData(int n){

cout<<"enter elements of array"<<endl;

for (int i=0; i<n; i++)

cin>>a[i];

}

int operator [](int n){

return a[n];

}

};

int main(){

myclass m;

m.getData(5);

cout<<m[0]<<endl;

cout<<m[3]<<endl;

return 0;

}
//ideal implementation is given below
#include<iostream>

#include<cstdlib>

const int MAX=5;

using namespace std;

class sArray{

private:

int arr[MAX];

public:

int& operator [] (int index){

if (index<0 || index >=MAX){

cout<<"out of bound"<<endl;

exit(1);

}

return arr[index];

}

};

int main(){

sArray sa;

for ( int i=0; i<MAX; i++){

sa[i]=i+2;

}

for ( int i=0; i<MAX; i++){

cout<<sa[i]<<endl;

}

}
```

new and delete operator overloading
```cpp
#include <cstddef>

#include<iostream>

#include<cstdlib>

using namespace std;

class cpoint{

private:

int x;

int y;

public:

cpoint(){}

cpoint(int a, int b) : x(a), y(b){}

void *operator new (size_t size);

void *operator new [] (size_t size);

void operator delete(void *ptr);

void operator delete[] (void *ptr);

void display(){

cout<<x<<'\t'<<y<<endl;

}

};

void *cpoint::operator new (size_t){

cout<<"overloaded operator new called"<<endl;

cpoint *ppoint=::new cpoint;

return ppoint;

}

void *cpoint::operator new[](size_t) {

cout<<"overloaded operator new[] called"<<endl;

cpoint *ppoint=::new cpoint[sizeof(cpoint)];

return ppoint;

}

void cpoint::operator delete(void *ptr){

cout<<"overloaded operator delete called"<<endl;

::delete (cpoint*) ptr;

}

void cpoint::operator delete [](void *ptr){

cout<<"overloaded operator delete[] called"<<endl;

::delete[] (cpoint*) ptr;

}

int main (){

cpoint *p1, *p2;

p1=new cpoint(2,3);

p2=new cpoint[5];

cout<<"value of p1:";(p1->display());

cout<<endl;

for (int i=0; i<5; ++i)

p2[i]=cpoint(i+1, i+i);

for (int i=0; i<5; ++i)

p2[i].display();

delete p1;

delete[]p2;

return 0;

  

}
```

member access through object
```cpp
#include <iostream>

  

class MyClass {

public:

int data;

};

  

class SmartPtr {

public:

SmartPtr(MyClass* ptr) : ptr_(ptr) {}

  

MyClass* operator->() {

return ptr_;

}

  

private:

MyClass* ptr_;

};

  

int main() {

MyClass obj;

obj.data = 10;

SmartPtr sp(&obj);

  

std::cout << sp->data << std::endl; // Output: 10

  

return 0;

}
```

dereference
```cpp
#include <iostream>

  

template <typename T>

class SmartPtr {

public:

SmartPtr(T* ptr) : ptr_(ptr) {}

  

// Overloaded dereference operator

T& operator*() {

return *ptr_;

}

  

// Overloaded arrow operator (often used in conjunction with dereference)

T* operator->() {

return ptr_;

}

  

private:

T* ptr_;

};

  

int main() {

int x = 10;

SmartPtr<int> sp(&x);

  

// Using the overloaded dereference operator

std::cout << *sp << std::endl; // Output: 10

  

// Using the overloaded arrow operator

(*sp)++; // Increment the value pointed to by sp

std::cout << *sp << std::endl; // Output: 11

  

return 0;

}
```

assignment
```cpp
#include<iostream>

#include<cstring>

using namespace std;

class String{

private:

char *str;

public:

String(){str= new char('\0');}

String(const char *s){

int len=strlen(s);

str=new char[len+1];

strcpy(str, s);

}

String(const String& s){

int len=strlen(s.str);

str=new char[len+1];

strcpy(str, s.str);

}

void setvalue(const char *s){

int len=strlen(s);

delete [] str;

str= new char [len+1];

strcpy(str, s);

}

void display() const {

cout<<str<<endl;

}

String operator =(const String s){

int len=strlen(s.str);

delete [] str;

str=new char[len+1];

strcpy(str, s.str);

return *this;

}

~String(){

delete [] str;

}

};

int main(){

String s1("he");

String s2;

s2=s1;

s1.display();

s2.display();

s1.setvalue("hello");

s1.display();

s2.display();

return 0;

}
```

function call overloading
```cpp
#include <iostream>

  

class FunctionCall {

public:

int operator()(int a, int b) {

return a + b;

}

};

  

int main() {

FunctionCall obj;

int result = obj(5, 3);

std::cout << "Result: " << result << std::endl;

return 0;

}
```