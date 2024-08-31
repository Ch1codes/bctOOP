Write a program to convert usd into npr and vice versa using constructor as well as casting operator
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

Write a program to convert between tola and gram
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

Write a program to convert polar coordinates to cartesian
```cpp
#include<iostream>
#include<math.h>
using namespace std;
double toRadian = M_PI/180;
class rectangle{
private:
float x;
float y;
public:
rectangle (float a=0, float b=0):x(a), y(b){
}
void display(){
    cout<<"x: "<<x<<" y: "<<y<<endl;
}
};
class polar{
private:
float r;
float a;
public:
polar() {
    cout<<"enter radial value and angle in degrees"<<endl;
    cin>>r>>a;
    a=a*toRadian;
}
operator rectangle (){
return rectangle(r*cos(a), r*sin(a));
}
};
int main() {
    polar m;
    rectangle n;
    n=m;
    n.display();
    return 0;
}
```

Write a program to convert Cartesian coordinates to polar. 
```cpp
#include<iostream>

#include<math.h>

using namespace std;

float toDegrees=180/M_PI;

class Polar{

private:

float r;

float a;

public:

Polar(float c=0, float b=0):r(c), a(b){}

void display(){

cout<<"r: "<<r<<" angle in degrees: "<<a*toDegrees<<endl;

}

};

class Rectangle{

private:

float x;

float y;

public:

Rectangle(){

cout<<"enter the x and y coordinates"<<endl;

cin>>x>>y;

}

operator Polar(){

double rho= sqrt(pow(x, 2)+pow(y,2));

double ang= atan(y/x);

return Polar(rho, ang);

}

};

int main(){

Polar m;

Rectangle n;

m=n;

m.display();

return 0;

}
```

Basic to User Defined: promotion, uses constructor placed at destination
```cpp
#include<iostream>

using namespace std;

class num{

private:

int n;

public:

num(int x=0){

n=x;

}

void display(){

cout<<n<<endl;

}

};

int main(){

int a=10;

num b;

b=a;

b.display();

return 0;

}
```

User Defined to Basic: uses casting operator, placed at destination
```cpp
#include<iostream>

using namespace std;

class num{

private:

int n;

public:

num(int x=0){

n=x;

}

operator int(){

return n;

}

};

int main(){

int a;

num b=10;

a=b;

cout<<a<<endl;

return 0;

}
```

explicit conversion
```cpp
#include<iostream>

using namespace std;

int main(){

float fvalue=1.12;

int ivalue;

ivalue=static_cast<int>(fvalue);

cout<<fvalue<<endl;

cout<<ivalue<<endl;

return 0;

}

//destructive conversion when converting from higher to lower data type
```

