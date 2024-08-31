exception handling regardless of throw
```cpp
#include<iostream>

using namespace std;

void calculate(int a, int b){

cout<<"inside function"<<endl;

if (b==0)

throw b;

cout<<"quotient: "<<a/b<<endl;

}

int main(){

try{

calculate(2,3);

calculate(1, 0);

}

catch(int c){

cout<<"exception"<<endl;

}

cout<<"end of program"<<endl;

}
```

uncaught exception
```cpp
#include <exception>

#include<iostream>

using namespace std;

void test_handler(){

cout<<"inside test handler"<<endl;

}

int main(){

set_terminate(test_handler);

//set_unexpected(test_handler); for unexpected exception but this function has been depreceated;

try{

cout<<"inside try block"<<endl;

throw 10;

}

catch(char c){

cout<<"character exception"<<endl;

}

return 0;

}
```

exception class but along with arguments
```cpp
#include<iostream>

using namespace std;

const int n=3;

class stack{

int A[n];

int top;

public:

class outOfRange{

public:;

string message;

outOfRange(string name){

message=name;

}

  

};

stack(){top=-1;}

void push(int data){

if (top==n-1)

throw outOfRange("stack overflow");

else {

top++;

A[top]=data;

}

}

void pop(){

if (top<0)

throw outOfRange("stack underflow");

cout<<A[top--]<<endl;

}

};

int main(){

stack a;

try{

a.push(1);

a.push(2);

a.push(3);

//a.push(0);

a.pop();

a.pop();

a.pop();

//a.pop();

}

catch(stack::outOfRange b){

cout<<"out of range:"<<b.message<<endl;

}

cout<<"end of program"<<endl;

return 0;

}
```

re-throwing exception
```cpp
#include<iostream>

using namespace std;

void calculate(int a, int b){

try{

cout<<"inner try"<<endl;

if (b==0)

throw b;

cout<<"coeff:"<<a/b<<endl;

}

catch(int b){

cout<<"inner catch"<<endl;

throw;

}

}

int main(){

try{

cout<<"outer try"<<endl;

calculate(1, 2);

calculate(2, 0);

}

catch(int c){

cout<<"outer catch"<<endl;

}

cout<<"end of program"<<endl;

return 0;

}
```

catch all exception
```cpp
#include<iostream>
using namespace std;

void test(int b){

try{

if (b==0)

throw b;

if (b==1)

throw 1.0;

if (b==2)

throw 'a';

}

catch(...){

cout<<"exception"<<endl;

}

}

int main(){

test(0);

test(1);

test(2);

test(3);

cout<<"end of program"<<endl;

return 0;

}
```