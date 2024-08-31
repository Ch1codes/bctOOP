Abstract class: whose objects are never instantiated and only exist as a parent to the derived classes from which the objects are instantiated; base class with at least one pure virtual function. 
Concrete class: classes whose objects can be created.

Pure virtual function: virtual function with null body

Pointer to object
```cpp
#include<iostream>

using namespace std;

class A{

public:

void display(){

cout<<"A"<<endl;

}

};

class B: public A{

public:

void display(){

cout<<"B"<<endl;

}

};

int main(){

A *a;

B b;

a= &b;

a->display(); //A

a= new B;

a->display(); //A

return 0;

}
```

pointer to object with virtual
```cpp
#include<iostream>

using namespace std;

class A{

public:

virtual void display(){

cout<<"A"<<endl;

}

};

class B: public A{

public:

void display(){

cout<<"B"<<endl;

}

};

int main(){

A *a;

B b;

a= &b;

a->display(); //B

a= new B;

a->display(); //B

return 0;

}
```

Virtual function
```cpp
#include<iostream>

using namespace std;

class A{

public:

virtual void display(){

cout<<"A"<<endl;

}

};

class B: public A{

public:

void display(){

cout<<"B"<<endl;

}

};

class C: public A{

public:

void display(){

cout<<"C"<<endl;

};

};

int main(){

A *a;

a= new B;

a->display(); //B

a = new C;

a->display(); //C

return 0;

}
```

reinterpret_cast
```cpp
#include <iostream>

  

int main() {

int x = 42;

  

// Reinterpreting the integer as a floating-point number (unsafe and usually not meaningful)

float* fp = reinterpret_cast<float*>(&x);

std::cout << *fp << std::endl; // Output will be undefined behavior

int* y=reinterpret_cast<int*>(fp);

std::cout<<*y<<std::endl;
//changing float pointer back to int pointer

  

// Reinterpreting a pointer to an integer as a pointer to a character (for byte-level access)

char* cp = reinterpret_cast<char*>(&x);

for (int i = 0; i < sizeof(int); ++i) {

std::cout << static_cast<int>(cp[i]) << " "; // Printing individual bytes

}

std::cout << std::endl;

  

return 0;

}
```

typeid
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
typeid2
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
Dynamic casting
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

d=dynamic_cast<Dog*>(a);

if(d){

cout<<"Cast succeeded"<<endl;//true

}

else{

cout<<"Cast failed"<<endl;

}

return 0;

}
```

Run Time Type Information: ability of finding the object's type and changing the type of object at runtime.If the base class pointer is holding the address of objects of its derived classes then the type of object the base class pointer points is known at the runtime only since it may be use to point various objects making it not always possible to know in advance the type of object the base class pointer is pointing to. 
Dynamic casting can convert a base class pointer to derived class pointer if the the object that is being pointed to by the base class pointer actually is the derived class object. 