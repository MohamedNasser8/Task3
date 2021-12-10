<h2>Const Usages</h2> 

1) Declaring a constant variable it can be used before and after the data type 
ex:

  ![This is an image](/Const_A.png)

 the value of the variable is specified in the declaration; there's no way to set it later!

<br>
                                                                      
 2) Const Pointer
 The syntax for declaring a pointer to constant data is :
 const int *p_int;

 You can think of this as reading that *p_int is a "const int". So the pointer may be changeable,
 but you definitely can't touch what p_int points to. The key here is that the const appears before the *. 

  if you just want the address stored in the pointer itself to be const, then you have to put const after the *:
  
  ![This is an image](/Const_BA.png)
  
<br>
3)It's particularly useful to declare reference parameters to functions as const references:
ex:

```
 bool verifyObjectCorrectness (const myObj& obj);
```

Here, a myObj object is passed by reference into verifyObjectCorrectness. 
For safety's sake, const is used to ensure that verifyObjectCorrectness cannot change the object.
<br>
4)hConst Functions:
 Once you have a const object,
 it cannot be assigned to a non-const reference or use functions that are known to be capable of changing the state of the object
 it means you need a way to state that a function should not make changes to an object ,this way can be achieved by declaring the function constant
 "const functions" are the only functions that can be called on a const object.
 to declare the function const you should put const at the end of the function.
 example:

![This is an image](/Const_fun.png) 


important notes:
.Const functions can always be called
.Non-const functions can only be called by non-const objects
<br>
<br>
5)Const Overloading
C++ allows member methods to be overloaded on the basis of const type.
Overloading on the basis of const type can be useful when a function return reference or pointer.
We can make one function const, that returns a const reference or const pointer,
other non-const function, that returns non-const reference or pointer.
ex:

![This is an image](/Const_ov.png) 

output:
fun() called
fun() const called
‘const void fun()’ is called on const object and ‘void fun()’ is called on non-const object
<br>
<br>
6)Const Iterators:
A const iterator points to an element of constant type which means the element which is being pointed to by a const_iterator can’t be modified.
Though we can still update the iterator(i.e., the iterator can be incremented or decremented but the element it points to can not be changed). 
It can be used for access only, and can’t be used for modification. 
If we try to modify the value of the element using const iterator then it generates an error.
ex:

![This is an image](/Const_it.png) 

<br>

7)Const cast:
const_cast is used to cast away the constness of variables.
const_cast can be used to pass const data to a function that doesn’t receive const.
For example, in the following program fun() receives a normal pointer, but a pointer to a const can
be passed with the help of const_cast.
ex:

![This is an image](/Const_cast.png)


It is undefined behavior to modify a value which is initially declared as const.
Consider the following program. The output of the program is undefined.
The variable ‘val’ is a const variable and the call ‘fun(ptr1)’ tries to modify ‘val’ using const_cast.

![This is an image](/Const_casta.png)

<h1>& Usage</h1>

