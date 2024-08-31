```cpp
//define a class named Car with attributes make, model and year. creat an instance of the class and print the attributes

#include<iostream>

using namespace std;

class Car{

private:

string make;

string model;

int year;

public:

Car(string ma="", string mo="", int y=0):make(ma), model(mo), year(y){

cout<<"Make: "<<make<<endl;

cout<<"Model: "<<model<<endl;

cout<<"Year: "<<year<<endl;

}

~Car(){}

};

int main(){

Car a("Ford", "Mustang", 2024);

return 0;

}
```

```cpp
//calculate area and perimeter through method of a class Rectangle with initialized length and width. 
#include<iostream>

using namespace std;

class Rectangle{

private:

float length;

float width;

public:

Rectangle(float l=0, float w=0):length(l), width(w){}

void area(){

cout<<"Area: "<<(length*width)<<endl;

}

void perimeter(){

cout<<"Perimeter: "<<(2*(length+width))<<endl;

}

};

int main(){

Rectangle a(2.2, 3.3);

a.area();

a.perimeter();

return 0;

}
```