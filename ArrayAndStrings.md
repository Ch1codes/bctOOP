Array can also be made from user defined types such as structures and objects. 
Array groups items of the same type such that they are accessed by an index number. 
```cpp
varType name [size];
//array declaration 
```
size must be a constant or a an expression that evaluates to a constant and should also be an integer. 
The items in an array are called elements. By conventional approach, memory grows downwards such that the first array elements are on the top of the page and later elements extend downward. 
We do not need to use the array size when we initialize all the array elements. If there are too few initializers, the missing elements will be set to 0.  If there are too many, an error is signaled.
```cpp
int num[]={1, 2, 3}
```
The array name actually represents the memory address of the array such that the array elements are not copied into the function. the function works with the original array although it may be referred to by a differessssssnt name. It is because of the possibly large size of array.
#### Multidimensional Arrays
```cpp
int man[district][age]={{1,2,3}, {4,5,6}};
```

#### Passing Arrays to Functions
Arrays can be used as arguments to functions. 
We need to write the array data type along with its size as arguments while declaring and defining the function but just writing the name in the argument will suffice when calling it. 
In a multidimensional array, just writing the size of the last dimension will work. It follows that if we were declaring a function that used a one dimensional array as an argument, we would not need to use the array size at all.
References to array elements in the function use the function's name for the array. 

#### Arrays of Structure. 
Array can contain structures of simple data types. 
The syntax to access data item that is a member of a structure that itself is an element of an array is :
```cpp
arrayName[index].dataMemberName;
```