<h2>Const Usages</h2> 

<h3>1) Declaring a constant variable</h3> it can be used before and after the data type 
ex:

 ```
 int const x = 5;
 or
 const int x = 5;
 ```

 the value of the variable is specified in the declaration; there's no way to set it later!
<hr>
<br>
                                                                      
 <h3>2) Const Pointer</h3>
 The syntax for declaring a pointer to constant data is :
 
 ```
 const int *p_int;
 ```
 
 
 You can think of this as reading that *p_int is a "const int". So the pointer may be changeable,
 but you definitely can't touch what p_int points to. The key here is that the const appears before the *. 

  if you just want the address stored in the pointer itself to be const, then you have to put const after the *:
  
  ```
  int x
  int* const p_int = &x;
  ```
  

<p>You can make const pointer and at the same type points to a const data using this syntax</p>

```
const int* const p_int; 
```
<p>in this case we cant change the pointer or the pointee</p>
<br>
<br>
<hr>
<h3>3) It's particularly useful to declare reference parameters to functions as const references</h3>
ex:

```
 bool verifyObjectCorrectness (const myObj& obj);
```

Here, a myObj object is passed by reference into verifyObjectCorrectness. 
For safety's sake, const is used to ensure that verifyObjectCorrectness cannot change the object.
<br>
<br>
<br>
<hr>
<h3>4) Const Functions</h3>
 Once you have a const object,
 it cannot be assigned to a non-const reference or use functions that are known to be capable of changing the state of the object
 it means you need a way to state that a function should not make changes to an object ,this way can be achieved by declaring the function constant
 "const functions" are the only functions that can be called on a const object.
 to declare the function const you should put const at the end of the function.
 example:

```
#include <iostream>
using namespace std;
 
class Car {
    int value;
 
public:
    Car(int v = 0) { value = v; }
 
    int getValue() const {
    return value; }
};
 
int main()
{
    Car c(20);
    cout << c.getValue();
    return 0;
}
```

important notes:
.Const functions can always be called
.Non-const functions can only be called by non-const objects
<br>
<br>
<br>
<hr>
<h3>5) Const Overloading</h3>
C++ allows member methods to be overloaded on the basis of const type.
Overloading on the basis of const type can be useful when a function return reference or pointer.
We can make one function const, that returns a const reference or const pointer,
other non-const function, that returns non-const reference or pointer.
ex:

```
#include<iostream>
using namespace std;

class Happy
{
protected:
	int x;
public:
	Happy (int i):x(i) { }
	void fun() const
	{
		cout << "fun() const called " << endl;
	}
	void fun()
	{
		cout << "fun() called " << endl;
	}
};

int main()
{
	Happy H1 (10);
	const Happy H2 (20);
	H1.fun();
	H2.fun();
	return 0;
}

```

```
output:
fun() called
fun() const called
```

‘const void fun()’ is called on const object and ‘void fun()’ is called on non-const object
<br>
<br>
<hr>
<h3>6) Const Iterators</h3>
A const iterator points to an element of constant type which means the element which is being pointed to by a const_iterator can’t be modified.
Though we can still update the iterator(i.e., the iterator can be incremented or decremented but the element it points to can not be changed). 
It can be used for access only, and can’t be used for modification. 
If we try to modify the value of the element using const iterator then it generates an error.
ex:

```
#include <iostream>
#include <iterator>
#include <vector>
using namespace std;

// Function that demonstrate const iterators
void constIterator(vector<int>& v1)
{
	// Declare a const_iterator to a vector
	vector<int>::const_iterator c;

	// Printing the elements of the
	// vector v1 using regular iterator
	for (c = v1.begin(); c < v1.end(); c++) {


		//*c += 1;   ->This line would gives us an error because we are trying to modify the vector element using const iterator 

		cout << *c << " ";
	}
}

int main()
{
	// Declaring  vector
	vector<int> v = { 7, 2, 4 };

	
	//demonstrates Const iterator
	constIterator(v);
	return 0;
}

```

<br>
<hr>
<h3>7) Const cast</h3>
const_cast is used to cast away the constness of variables.
const_cast can be used to pass const data to a function that doesn’t receive const.
For example, in the following program Val() receives a normal pointer, but a pointer to a const can
be passed with the help of const_cast.
ex:

```
#include <iostream>
using namespace std;
  
int Val(int* pntr)
    {
    return (*pntr + 5);
    }
    
int main(void)
{
    const int value = 5;
    const int *ptnr = &value;
    int *pntr1 = const_cast <int *>(pntr);
    cout << Val(pntr1);
    return 0;
}
```

```
Output:
10
```

It is undefined behavior to modify a value which is initially declared as const.


```
#include <iostream>
using namespace std;
  
int Val(int* pntr)
{
    *ptr = *pntr + 10;
    return (*ptr);
}
  
int main(void)
{
    const int val = 10;
    const int *pntr = &val;
    int *pntr1 = const_cast <int *>(pntr);
    fun(ptr1);
    cout << val;
    return 0;
}
```

```
Output:
 Undefined Behavior 

reason -> The variable ‘val’ is a const variable and the call ‘Val(ptrn1)’ tries to modify ‘val’ using const_cast.
```

<hr>
<h3>8)Const class data member</h3>
These are data variables in class which are defined using const keyword. 
They are not initialized during declaration.
Their initialization is done in the constructor.
Ex:

```
class Car
        {

const int type;
public:

Car(int n): type(n)   //initializer list
{
    cout << "\ni value set: " << i;
}

   };

    int main()
  {

Car c1(10);
Car c2(20);
     }
```

<hr>
<h2>& Usage</h2>
<h3>1) Logical AND</h3>
  
 - 
  ```
  if(x < 10 && y < 10)
  ```

  
  <hr>  
  
  <h3>2) Bitwise AND</h3>
  
  
  ```
  z = (x & y); Corresponding bits are and'ed (e.g. 1&0 -> 0)
  ```
  
  
  <hr>
  
<h3>3) Bitwise AND Assignment</h3>
 
  
 ```
 a &= b; the same as a = a & b;
  ```
 
  <hr>
  <h3>4) Address-of</h3>
  
  
  ``` 
  int x =5;
  int* ptr = &x;
  ```
  
  ```
  x=&y;
  that means that the two variables have the same address;
 const int *p_int;
 ```
  
  <br>
  <hr>
  <h3>Pass By Reference</h3>
  <p>You can pass a reference to the function. This can be useful when you need to change the value of the arguments</p> 
  
```
  void swapNums(int &x, int &y) {
  int z = x;
  x = y;
  y = z;
}

int main() {
  int firstNum = 10;
  int secondNum = 20;

  cout << "Before swap: " << "\n";
  cout << firstNum <<' '<< secondNum << "\n";

  // Call the function, which will change the values of firstNum and secondNum
  swapNums(firstNum, secondNum);

  cout << "After swap: " << "\n";
  cout << firstNum <<' '<< secondNum << "\n";

  return 0;
}
  ```
  
