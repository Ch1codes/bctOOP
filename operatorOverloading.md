###### Write a program to add two string.
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

###### Write a program to overload insertion and extraction operators
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

###### Write a program to overload relational operators
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

###### Write a program to compare two strings
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

###### Write a program to overload unary operators
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

###### Write a program to add two land measures using the concept of operator overloading
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