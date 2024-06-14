###### Write a program to convert usd into npr and vice versa using constructor as well as casting operator
```cpp
#include <iostream>

using namespace std;

class dollar{

private:

float usd;

public:

dollar (float d=0):usd(d){}

void showDollar(){

cout<<"Dollar Amount: \t"<<usd<<endl;

}

float getDollar(){

return usd;

}

};

class rupee{

private:

float npr;

public:

rupee (float r=0):npr(r){}

void showRupee(){

cout<<"Rupee Amount: \t"<<npr<<endl;

}

rupee(dollar d){

npr=d.getDollar()*132.94;

}

operator dollar(){

return dollar(npr/132.94);

}

};

int main(){

dollar d1(100), d2;

rupee r1, r2(100000);

cout<<"using constructor"<<endl;

d1.showDollar();

r1=d1;

r1.showRupee();

cout<<"using casting operator"<<endl;

r2.showRupee();

d2=r2;

d2.showDollar();

return 0;

}
```

###### Write a program to convert between tola and gram
```cpp
#include<iostream>

using namespace std;

class International {

private:

float gram;

public:

International (float i=0):gram (i){}

void DisplayI(){

cout<<"Gram: "<<gram<<endl;

}

};

class Nepal {

private:

float tola;

public:

Nepal (float t): tola(t){

}

operator International(){

return International(tola * 11.664);

}

void DisplayN(){

cout<<"Tola: "<<tola<<endl;

}

};

int main() {

Nepal a(2);

International b;

b = a;

b.DisplayI();

return 0;

}
```