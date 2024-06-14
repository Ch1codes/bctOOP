###### Write a program to show how inline function is used. 
```cpp
/*The compiler is most likely to not consider the inlining of a function under certain circumstances that are mentioned here as follows-

  

When a function with a return statement is not returning any value and marked as inline, the compiler does not respond to the programmer’s request of making it an inline function.

When a programmer tries to inline a function containing a loop (for, while, or do-while), the compiler refuses the inline suggestion.

When a function is recursive, it cannot be inlined.

A function containing static variables cannot be made an inline function.

The compiler declines the request of inlining a function if it contains any switch or go-to statements.*/

#include <iostream>

using namespace std;

inline void area ( float length, float breadth){

float a = length * breadth;

cout<<"area: "<<a<<endl;

}

int main (){

area (3, 4);

area ( 4, 5);

return 0;

}
```

###### Write a program to show how namespace works.
```cpp
//show the use of namespace and userdefined namespace

#include<iostream>

using namespace std;

namespace add{

int act(int x, int y){

return x+y;

}

}

namespace subtract {

int act (int x, int y){

return x-y;

}

}

int main (){

int a=10, b=5;

cout<<"the sum is: "<<add::act(a,b)<<endl;

cout<<"the difference is: "<<subtract::act(a,b)<<endl;

return 0;

}

/* in this program, we have two functions having same name and same arguments

and hence cannot be overloaded; we encounter error when we run this program.

to solve this, we define the function under two userdefined namespace such that we can

call both the function through their namespace and using access resolution operation to

avoid the naming collison*/
```

###### Write a program to find the transpose of Matrix which shows array and pointers in class
```cpp
//to find the transpose of a given Matrix using the concpet of class and object

#include<iostream>

using namespace std;

class Matrix{

private:

int rows, columns;

int **mat;

public:

Matrix(int r, int c){

rows=r;

columns=c;

mat = new int* [rows];

for (int i = 0; i<rows; i++){

mat[i]= new int[columns];

}

}

~Matrix() {

for (int i = 0; i < rows; ++i) {

delete[] mat[i];

}

delete[] mat;

}

void data(){

cout<<"enter your matrix"<<endl;

for ( int i = 0; i<rows; i++){

for (int j = 0; j<columns; j++){

cin >> mat[i][j];

}

}

}

void display(){

for ( int i = 0; i<rows; i ++){

for (int j = 0; j<columns; j++)

cout<<" "<<mat[i][j]<<" ";

cout<<"\n";

}

  

}

void transpose (){

Matrix trans(rows, columns);

// Matrix temp(a. rows, a.columns);

for ( int i = 0; i<rows; i ++){

for (int j = 0; j<columns; j++){

trans.mat[i][j] = mat[j][i];

cout<<" "<<trans.mat[i][j];

}

cout<<"\n";

}

}

};

int main (){

Matrix m(3, 3);

m.data();

cout<<"The input Matrix is: "<<endl;

m.display();

cout<<"The transposed matrix is: "<<endl;

m.transpose();

return 0;

}
```

###### Write a program to show the use of dynamic memory allocation inside a class
```cpp
//to use DMA inside a class

#include<iostream>

using namespace std;

class Book{

private:

char *title;

char *author;

float price;

public:

Book(){

int titleSize, authorSize;

cout<<"enter the character length of the title of the book and author?"<<endl;

cin>>titleSize>>authorSize;

title = new char [titleSize];

author = new char [authorSize];

cout<<"enter the title of the book? "<<endl;

cin>>title;

cout<<"enter the name of the author of the book? "<<endl;

cin>>author;

cout<<"enter the price of the book? "<<endl;

cin>>price;

}

void display(){

cout<<"The book "<<title<<" written by "<<author<<" costs "<<price<<endl;

}

~Book(){

delete [] title;

delete [] author;

}

};

int main(){

Book a;

a.display();

return 0;

}
```

###### Write a program to convert volume into feet
```cpp
#include<iostream>

using namespace std;

class volume {

private:

float length, width, height;

public:

volume (float l, float w, float h){

length = l * 3.28084;

width = w * 3.28084;

height = h * 3.28084;

float v = length * width * height;

cout<<"Volume in feet: "<<v<<endl;

}

~volume(){}

};

int main () {

volume a (2, 3, 4);

return 0;

}
```

###### Write a program to show the use of friend function
```cpp
#include <iostream>

#include <string>

using namespace std;

class BookStore;

class Book {

private:

string title;

string author;

float price;

public:

Book (string t ="", string a ="", float p = 0):title(t), author (a), price(p){}

friend class BookStore;

};

class BookStore {

public:

BookStore (){}

void compare(Book m, Book n){

if (m.price>n.price)

cout<<m.title<<" by "<<m.author<<" is more expensive than "<<n.title<<" by "<<n.author<<endl;

else if (m.price<n.price)

cout<<n.title<<" by "<<n.author<<" is more expensive than "<<m.title<<" by "<<m.author<<endl;

else

cout<<m.title<<" by "<<m.author<<" is equal in cost to "<<n.title<<" by "<<n.author<<endl;

}

};

int main() {

Book x("Mein Kampf", "Adolf Hitler", 1000), y("Steve Jobs", "Issac Walterman", 500);

BookStore z;

z.compare(x,y);

return 0;

}
```