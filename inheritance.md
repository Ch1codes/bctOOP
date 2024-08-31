 Write a program which contains a base class that ask the user to enter complex number and make a derived class that add the complex no. of its own with the base. Finally make a third class that is friend with the derived and calculate the difference between the base complex no. and its own complex no. 
```c++
#include<iostream>
using namespace std;

class C;

class A {

protected:

float ar, ai;

public:

A(){

cout<<"enter the real and imaginary part of the number A"<<endl;

cin>>ar>>ai;

}

};

class B: public A {

protected:

float br, bi;

public:

B(){

cout<<"enter the real and imaginary part of the number B"<<endl;

cin>>br>>bi;

}

void display(){

cout<<"sum is: "<<(ar+br)<<" +i "<<(ai+bi)<<endl;

}

friend class C;

};

class C {

private:

float cr, ci;

public:

C(){

cout<<"enter the real and imaginary part of the number C"<<endl;

cin>>cr>>ci;

}

void display( B m ){

cout<<"the difference is: "<<(m.ar - cr)<<" +i "<<(m.ai - ci)<<endl;

}

};

int main () {

B i;

C j;

i.display();

j.display(i);

return 0;

}
```
 
Write a program to create a derived class by inheriting two base classes with same function name. Your program should be complete and meaningful
 This program depicts the ambiguity problem.
 ```cpp
 #include<iostream>

using namespace std;

class A {

protected:

float m;

public:

void display(){

m=4;

cout<<"A: "<<m<<endl;

}

};

class B {

protected:

float n;

public:

void display(){

n=5;

cout<<"B: "<<n<<endl;

}

};

class C: public A, public B {

private:

float m;

  

public:

C() {

m=0;

}

};

int main(){

C i;

//i.display(); only would be ambigious.

i.A::display();

i.B::display();

return 0;

}
```

Write a program to illustrate the constructor and destructor invocation in multilevel inheritance. 
```cpp
#include<iostream>

using namespace std;

class A {

public:

A() {

cout<<"A is called"<<endl;

}

~A(){

cout<<"A is destroyed"<<endl;

}

};

class B: public A {

public:

B (){

cout<<"B is called"<<endl;

}

~B(){

cout<<"B is destroyed"<<endl;

}

};

class C: public B {

public:

C () {

cout<<"C is called"<<endl;

}

~C(){

cout<<"C is destoyed"<<endl;

}

};

int main() {

C r;

return 0;

}
```
In this program, we see that constructors are called in the order of top to bottom but destructors from bottom to top. 



Write a program to show hybrid Inheritance and solution to diamond problem.
```cpp
#include<iostream>

using namespace std;

class A {

public:

A() {

cout<<"A is called"<<endl;

}

};

class B: virtual public A {

public:

B(){

cout<<"B is called"<<endl;

}

};

class C: virtual public A {

public:

C() {

cout<<"C is called"<<endl;

}

};

class D: public B {

public:

D() {

cout<<"D is called "<<endl;

}

};

class E: public B, public C {

public:

E(){

cout<<"E is called"<<endl;

}

};

int main() {

D d;

cout<<endl;

E e;

return 0;

}
```


Write a program to show multilevel inheritance.
```cpp
#include<iostream>

#include<string>

using namespace std;

class Student {

protected:

string Name;

int roll;

public:

Student(){

cout<<"enter name and roll of the student"<<endl;

cin>>Name>>roll;

}

};

class Test: public Student {

protected:

float math, science, english;

public:

Test (){

cout<<"enter marks in math, science and english"<<endl;

cin>>math>>science>>english;

}

};

class Result: public Test {

private:

float total;

public:

Result() {

total=math+science+english;

cout<<"RESULT"<<endl;

cout<<"Name: "<<Name<<" Roll: "<<roll<<endl;

cout<<"Marks"<<endl<<"Math: "<<math<<endl<<"Science:"<<science<<endl<<"English: "<<english<<endl;

cout<<"Total: "<<total;

}

};

int main() {

Result a;

return 0;

}
```

Write a program to show hierarchical inheritance. 
```cpp
#include<iostream>

#include<string>

using namespace std;

class person {

protected:

string name;

int age;

public:

person () {

cout<<"enter name and age"<<endl;

cin>>name>>age;

}

};

class student: public person {

protected:

string grade;

int roll;

public:

student(){

cout<<"enter grade and roll"<<endl;

cin>>grade>>roll;

}

void display(){

cout<<"Student"<<endl;

cout<<"Name: "<<name<<" Age: "<<age<<endl;

cout<<"Grade: "<<grade<<" Roll: "<<roll<<endl<<endl;

}

};

class teachingStaff: public person {

protected:

string subject;

string qualification;

public:

teachingStaff(){

cout<<"What does the teacher teaches?"<<endl;

cin>>subject;

cout<<"What is his education level?"<<endl;

cin>>qualification;

}

void display() {

cout<<"Teaching Staff"<<endl;

cout<<"Name: "<<name<<" Age: "<<age<<endl;

cout<<"Subject: "<<subject<<" Qualification: "<<qualification<<endl<<endl;

  

}

};

class nonTeachingStaff: public person {

protected:

string position;

string shift;

public:

nonTeachingStaff(){

cout<<"What do they do?"<<endl;

cin>>position;

cout<<"In which shift do they work?"<<endl;

cin>>shift;

}

void display(){

cout<<"Non Teaching Staff"<<endl;

cout<<"Name: "<<name<<" Age: "<<age<<endl;

cout<<"Position: "<<position<<" Shift: "<<shift<<endl<<endl;

}

};

int main() {

student s;

teachingStaff t;

nonTeachingStaff n;

s.display();

t.display();

n.display();

return 0;

}
```

Visibility mode always should be Protected.  Protected made solely for inheritance. 
Can't inherit static, friend and constructor. But constructor called because base should be satisfied 