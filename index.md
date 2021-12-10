Const Usages: 

1) Declaring a constant variable it can be used before and after the data type 
ex:

![This is an image](/images/Const_A.png)
 the value of the variable is specified in the declaration; there's no way to set it later!






 2) Const Pointer
 The syntax for declaring a pointer to constant data is :
 const int *p_int;

 You can think of this as reading that *p_int is a "const int". So the pointer may be changeable,
 but you definitely can't touch what p_int points to. The key here is that the const appears before the *. 

  if you just want the address stored in the pointer itself to be const, then you have to put const after the *:
  ![This is an image](/images/Const_BA.png)





3)It's particularly useful to declare reference parameters to functions as const references:
ex: bool verifyObjectCorrectness (const myObj& obj);

Here, a myObj object is passed by reference into verifyObjectCorrectness. 
For safety's sake, const is used to ensure that verifyObjectCorrectness cannot change the object.





4)Const Functions:
 Once you have a const object,
 it cannot be assigned to a non-const reference or use functions that are known to be capable of changing the state of the object
 it means you need a way to state that a function should not make changes to an object ,this way can be achieved by declaring the function constant
 "const functions" are the only functions that can be called on a const object.
 to declare the function const you should put const at the end of the function.
 example:

![This is an image](/images/Const_fun.png) 


important notes:
.Const functions can always be called
.Non-const functions can only be called by non-const objects




