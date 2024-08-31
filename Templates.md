stack
```cpp
#include<iostream>

using namespace std;

template<class T>

class st{

private:

T arr[3];

int top;

public:

st(){top=-1;}

void push (T data){

arr[++top]=data;

}

T pop(){

return arr[top--];

}

int size();

};

template<class T>

int st <T>:: size(){

return (top+1);

}

int main(){

st<int>s1;

s1.push(2);

s1.push(4);

cout<<s1.pop()<<endl;

cout<<s1.pop()<<endl;

st <float>s2;

s2.push(3.3);

s2.push(4.4);

s2.push(2.2);

cout<<"size: "<<s2.size();

cout<<s2.pop()<<endl;

cout<<s2.pop()<<endl;

cout<<s2.pop()<<endl;

return 0;

}
```



Function template
```cpp
#include<iostream>

using namespace std;

template<class T>

T maxi( T a, T b){

if(a>b)

return a;

else

return b;

}

int main(){

cout<<maxi(5, 6);

cout<<endl;

cout<<maxi(6.6, 6.5);

return 0;

  

}
```

Lab 10 templates
```cpp
//wap that will illustrate the overloading of a functin template with both normal and a function template

#include<iostream>

using namespace std;

template<class T>

void display(T a){

cout<<a<<endl;

}

template<class T1, class T2>

void display(T1 a, T2 b){

cout<<a<<"\t"<<b<<endl;

}

void display( int a){

cout<<a<<endl;

}

int main(){

float x=10.12, y=11.24;

int m=10;

display(x);

display(x, y);

display(m);

return 0;

}
Output:
10.12
10.12 11.24
10
```

Q.2
```cpp
#include <iostream>

  

using namespace std;

  

template <typename T>

void findSumAndAverage(T arr[], int n) {

T sum = 0;

for (int i = 0; i < n; i++) {

sum += arr[i];

}

  

T average = static_cast<T>(sum) / n;

  

cout << "Sum: " << sum << endl;

cout << "Average: " << average << endl;

}

  

int main() {

int intArr[] = {10, 20, 30, 40, 50};

double doubleArr[] = {1.5, 2.5, 3.5, 4.5, 5.5};

  

findSumAndAverage(intArr, sizeof(intArr) / sizeof(intArr[0]));

cout << endl;

findSumAndAverage(doubleArr, sizeof(doubleArr) / sizeof(doubleArr[0]));

  

return 0;

}
```

```cpp
//wap with a class template to represent array and add member function to find maximum, minimum and sort the generic array.

#include<iostream>

using namespace std;

template<class T, const int size=5>

class operation {

private:

T arr[size];

public:

operation(){

for (int i=0; i<5; i++){

cout<<"enter data"<<endl;

cin>>arr[i];

}

}

void sort(){

for (int i =0; i<size-1; i++){

for ( int j = i+1; j<size; j++){

if (arr[i]>arr[j]){

arr[i]=arr[i]+arr[j];

arr[j]=arr[i]-arr[j];

arr[i]=arr[i]-arr[j];

}

}

}

cout<<"sorted: "<<endl;

for (int i=0; i<5; i++){

cout<<arr[i]<<endl;

}

cout<<"maximum:"<<arr[size-1]<<endl;

cout<<"minimum:"<<arr[0]<<endl;

  

}

};

int main(){

operation<int>a;

a.sort();

operation<float>b;

b.sort();

return 0;

}
```

```cpp
//wap using a template to add two numbers. use the function template to pass integer, char, float and double. display the returned result

#include<iostream>

#include<cstring>

using namespace std;

template<class T>

T add(T a, T b){

return a+b;

}

char* add(const char* a, const char* b){

int len=(strlen(a) + strlen(b));

char *str=new char[len+1];

strcat(str, a);

strcat(str, b);

return str;

}

int main(){

int p=10, q=20;

cout<<"sum: "<<add(p, q)<<endl;

float x=1.1, y=2.2;

cout<<"sum: "<<add(x, y)<<endl;

double g=100, h=900;

cout<<"sum: "<<add(g, h)<<endl;

cout<<"sum: "<<add("HELLO", "world")<<endl;

cout<<"sum: "<<add('a', 'B');

return 0;

}
```