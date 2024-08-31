database
```cpp

#include<iostream>

#include<fstream>

#include<stdlib.h>

using namespace std;

const char * datafile ="record.dat";

class student{

private:

char name[25];

int roll, telephone, score;

public:

void readData(){

cout<<endl;

cout<<"enter roll, name, telephone, score"<<endl;

cin>>roll>>name>>telephone>>score;

}

void display(){

cout<<endl;

cout<<"Roll: "<<roll<<endl;

cout<<"Name: "<<name<<endl;

cout<<"Telephone "<<telephone<<endl;;

cout<<"Score: "<<score<<endl;;

}

void write(){

ofstream outfile(datafile, ios::binary|ios::app);

readData();

outfile.write(reinterpret_cast<char*>(this), sizeof(*this));

}

void access(){

int n;

ifstream infile(datafile, ios::binary);

if(!infile){

cout<<"file not found"<<endl;

return;

}

cout<<"\n enter roll number: "<<endl;

cin>>n;

infile.seekg((n-1)*sizeof(*this));

infile.read(reinterpret_cast<char*>(this), sizeof(*this));

display();

}

void accessAll(){

ifstream infile(datafile, ios::binary);

if(!infile){

cout<<"file not found"<<endl;

return;

}

infile.seekg(0, ios::end);

int count=infile.tellg()/sizeof(*this);

cout<<"no. of records present: "<<count<<endl;

cout<<"\n data from file"<<endl;

while (!infile.eof()){

if(infile.read(reinterpret_cast<char*>(this), sizeof(*this)))

display();

}

}

void edit(){

int n;

fstream iofile(datafile, ios::in| ios::binary);

if(!iofile){

cout<<"file not found"<<endl;

return;

}

iofile.seekg(0, ios::end);

int count=iofile.tellg()/sizeof(*this);

cout<<"\n enter roll number to be edited: "<<endl;

cin>>n;

iofile.seekg((n-1)*sizeof(*this));

iofile.read(reinterpret_cast<char*>(this), sizeof(*this));

display();

iofile.close();

iofile.open(datafile, ios::out|ios::in|ios::binary);

iofile.seekp((n-1)*sizeof(*this));

cout<<"enter modifications:"<<endl;

readData();

iofile.write(reinterpret_cast<char*>(this),sizeof(*this));

}

void removee(){

int n;

char temp[]="temp.dat";

ifstream infile(datafile, ios::binary);

if(!infile){

cout<<"file not found"<<endl;

return;

}

infile.seekg(0, ios::end);

int count=infile.tellg()/sizeof(*this);

cout<<"no. of records present: "<<count<<endl;

cout<<"enter the roll no. to be removed: "<<endl;

cin>>n;

fstream tempfile(temp, ios::out|ios::binary);

infile.seekg(0);

for (int i=0; i<count; ++i){

infile.read(reinterpret_cast<char*>(this), sizeof(*this));

if(i==n-1)

continue;

tempfile.write(reinterpret_cast<char*>(this), sizeof(*this));

}

infile.close();

tempfile.close();

ofstream outfile(datafile, ios::binary);

tempfile.open(temp, ios::in|ios::binary);

for (int i=0; i<count-1; ++i){

tempfile.read(reinterpret_cast<char*>(this), sizeof(*this));

outfile.write(reinterpret_cast<char*>(this), sizeof(*this));

}

tempfile.close();

remove(temp);

}

  
  

};

int main(){

student s;

int choice;

cout<<"student record"<<endl;

while(true){

cout<<"\n Select one of below:";

cout<<"\n1 enter a record:";

cout<<"\n2 find a record:";

cout<<"\n3 display all record:";

cout<<"\n4 edit record:";

cout<<"\n5 delete record";

cout<<"\n6 exit";

cout<<"\n enter a choice";

cin>>choice;

switch(choice){

case 1:

s.write();

break;

case 2:

s.access();

break;

case 3:

s.accessAll();

break;

case 4:

s.edit();

break;

case 5:

s.removee();

break;

case 6:

exit(0);

break;

default:

cout<<"no choice available"<<endl;

exit(0);

break;

}

}

return 0;

}
```

files explicitly
```cpp
#include<iostream>

#include<fstream>

using namespace std;

int main(){

string name, email;

string nameo, emailo;

ofstream outfile;

outfile.open("contact.txt");

cout<<"enter name and email"<<endl;

cin>>nameo>>emailo;

outfile<<nameo<<endl<<emailo<<endl;

outfile.close();

ifstream infile;

infile.open("contact.txt");

infile>>name>>email;

cout<<"Name: "<<name<<endl;

cout<<"Email: "<<email<<endl;

infile.close();

return 0;

}
```

files using constructor
```cpp
#include<iostream>

#include<fstream>

using namespace std;

int main(){

string name;

string name2;

float cost;

ofstream outfile("data.txt");

cout<<"enter name"<<endl;

cin>>name;

outfile<<name<<"\n";

outfile.close();

ifstream infile("data.txt");

infile>>name2;

cout<<"name: "<<name2<<endl;

infile.close();

return 0;

}
```

formatted
```cpp
#include<iostream>

using namespace std;

int main() {

cout.width(10);

cout<<101<<endl;

cout.width(5);

cout<<101<<endl;

cout.width(5);

cout.fill('*');

cout<<101<<endl;

float a=1.123456789;

cout<<a<<endl;

cout.precision(2);

cout<<a<<endl;

double b =1.123456789;

cout.precision(10);

cout<<b<<endl;

return 0;

}
```

getline and write
```cpp
#include<iostream>

using namespace std;

int main(){

char name[20];

cout<<"enter name"<<endl;

cin.getline(name, 20, '*');

cout.write(name, 20);

return 0;

  

}
```

overload stream operators
```cpp
#include<iostream>

using namespace std;

class rectangular{

private:

float x, y;

public:

rectangular(){x=0, y=0;}

friend istream& operator>>(istream& is, rectangular &a);

friend ostream& operator<<(ostream& os, rectangular &a);

};

istream& operator>>(istream& is, rectangular &a){

is>>a.x>>a.y;

return is;

}

ostream& operator << (ostream& os, rectangular &a){

os<<'('<<a.x<<','<<a.y<<')'<<flush;

return os;

}

int main(){

rectangular c;

cout<<"enter both the coordinates"<<endl;

cin>>c;

cout<<"coordinates:"<<c<<endl;

return 0;

}
```

setf and unsetf
```cpp

#include<iostream>

using namespace std;

int main() {

float a=1.1234;

int b=17;

cout.setf(ios::left, ios::adjustfield);

cout.setf(ios::showpos);

cout.width(10);

cout<<a<<endl;

cout.setf(ios::right, ios::adjustfield);

cout.width(10);

cout<<a<<endl;

cout.setf(ios::internal, ios::adjustfield);

cout.width(10);

cout<<a<<endl;

cout.setf(ios::dec, ios::basefield);\

cout<<b<<endl;

cout.setf(ios::oct, ios::basefield);\

cout.setf(ios::showbase);

cout<<b<<endl;

cout.setf(ios::hex, ios::basefield);\

cout.setf(ios::showbase);

cout<<b<<endl;

cout<<18<<endl;

cout.unsetf(ios::hex);

cout<<18<<endl;

cout.setf(ios::scientific, ios::floatfield);

cout<<a<<endl;

cout.setf(ios::fixed, ios::floatfield);

cout<<a<<endl;

return 0;

}
```

std manipulators
```cpp
#include<iostream>

#include<iomanip>

using namespace std;

int main(){

int a=10;

double b=1.123459999999999;

long double c=1234567898000000000.0000000000;

cout<<setw(7)<<setfill('!')<<a<<endl;

cout<<setprecision(3)<<b<<endl;

cout<<setiosflags(ios::showpos)<<setiosflags(ios::scientific)<<c<<endl<<resetiosflags(ios::showpos)<<c<<endl;

cout<<oct<<unitbuf<<10<<endl;

cout<<resetiosflags(ios::scientific)<<endl;

cout<<setprecision(4)<<123.123<<endl;

return 0;

}
```

user defined manipulators
```cpp
#include<iostream>

using namespace std;

//for parameterized;

class uManipulator{\

private:

int n;

public:

uManipulator(int num):n(num){}

friend ostream& operator <<(ostream&, uManipulator);

};

ostream& operator <<(ostream& ps, uManipulator obj){

for (int i =0; i<obj.n; ++i)

ps<<'\t';

ps<<flush;

return ps;

}

uManipulator ub(int n){

return uManipulator(n);

}

//function for no arguments

ostream& tb(ostream &os){

os<<'\t'<<flush;

return os;

}

int main() {

int a =1, b=2, c=3, d=4;

cout<<a<<tb<<b<<tb<<c<<tb<<d<<endl;

cout<<endl;

cout<<a<<ub(1)<<b<<ub(2)<<c<<ub(3)<<d<<endl;

return 0;

}
```

print a pattern
```cpp
#include<iostream>

#include<cstring>

#include<iomanip>

using namespace std;

int main(){

char str[]="*******";

for (int i=1; i<=strlen(str); ++i){

cout.write(str, i);

cout<<endl;

}

return 0;

}
```


copying
```cpp
#include<iostream>

#include<fstream>

#include<cstring>

using namespace std;

const char* datafile="record3.dat";

const char* anotherfile="record4.dat";

class text{

private:

char t[50];

public:

void readData(){

cout<<"enter data"<<endl;

cin.getline(t, 50);

}

void showData(){

cout<<"text: "<<t<<endl;

}

void writeRec(){

ofstream outfile(datafile, ios::binary|ios::app);

readData();

outfile.write(reinterpret_cast<char*>(this), sizeof(*this));

}

void copyRec(){

ifstream infile(datafile, ios::binary);

ofstream ofile(anotherfile, ios::binary|ios::app);

if (!infile){

cout<<"nothing"<<endl;

return;

}

cout<<"from the file"<<endl;

while(!infile.eof()){

if((infile.read(reinterpret_cast<char*>(this), sizeof(*this)))){

for(int i = 0; i<strlen(t);i++)

t[i]=toupper(t[i]);

ofile.write(reinterpret_cast<char*>(this), sizeof(*this));

}

}

}

void displayRec(){

ifstream infile(anotherfile, ios::binary);

if(!infile){

cout<<"nothing"<<endl;

return;

}

while(!infile.eof()){

if(infile.read(reinterpret_cast<char*>(this), sizeof(*this))){

showData();

}

}

}

};

int main(){

text a;

a.writeRec();

a.copyRec();

a.displayRec();

return 0;

  

}
```