# bignum
https://mrdcvlsc.github.io/bignum/
## bignum - c++ for big number computation (arbitrary-precision arithmetic).

### **SUPPORTS OPERATION ON INTEGER AND RATIONAL NUMBERS IN DECIMAL FORM** ###

#### SEE the branch "bignum-v2.2.1(stable)" if you are having problems/bugs with the latest version in master branch
-------------------------------------------------------------------

## Download It Here - [Github Repo - source codes](https://github.com/mrdcvlsc/bignum)

------------------------------------------------------------------

### TO USE :

-------------------------------------------------------------------

**For beginners that uses IDE**

  1. put the **bignum.h** and all the **.cpp** files that is inside the ***source*** folder to your project folder.

  2. add **```#include "bignum.h"```** in your ***main.cpp*** file.
  
  3. select and add the files on your project in your IDE.

  4. then compile and run.
  
-------------------------------------------------------------------

**For those who know "make" / makefiles you can use the static library for faster compilation**

  1. open the **cmd** or ***command line terminal**.
  
  2. change directory to this folder in the command line using **```cd your/directory/path/bignum```**
  
  3. enter the commad **```make```** to generate "***bignum.lib***"

  4. now you can put the ***bignum.h*** and the ***bignum.lib*** in your project folder then include the header files in your main.cpp file and link the static libray bignum.lib, see the **"FACTORIAL SAMPLE CODE** on this page below.

  5. or put the bignum.lib and bignum.h in your project folder then add it to your project in IDE the build and run (for IDE users)
  
**Test the generated library (optional)**

  -use the **```make test```** command after **```make```** to run the test program if you want**
  
-------------------------------------------------------------------

### bignum initialization (using double quote "" is more recommended)
    
   ```c++
   // use string or const char* for big values
   bignum var1 = "23234.78634";
   bignum var2 = "-67864254234324234";
   
   // you can also use constant integers up to 18.4e+18
   bignum var3  = -57232;
   bignum var4 = 96725372372ll;
   
   // or float and doubles
   // for very long rational numbers use strings instead to avoid automatic rounding
   bignum var5 = 7676434.2323234L; // long doubles
   bignum var6 = -76734.57623f;
   
   // copy bignum
   bignum var7 = var1;
   var3 = var4 = 65652.762;
   ```
-------------------------------------------------------------------

### SUPPORTED OPERATIONS (FOR INTEGERS AND RATIONAL NUMBERS/DECIMAL FORM)

   **[done] Addition (+)**
   
   ```c++   
   cout<< var1 + var3 <<endl;
   cout<< var3 + "56756.4645" <<endl;
   cout<< 7567634 + var1 <<endl;
   ```
   
   **[done] Subtraction (-)**
   
   ```c++
   cout<< var2 - var1 <<endl;
   cout<< var4 - 74672323232ull <<endl;
   cout<< "656422" - var3 <<endl;
   ```

   **[done] Multiplication (x)**
   
   ```c++
   cout<< var1 * var3 <<endl;
   cout<< var2 * 2234544.65 <<endl;
   cout<< "64652823.42" * var3 <<endl;
   ```
   
   **[optimize later] Division (/)**
   
   ```c++
   cout<< var2 / var6 <<endl;
   cout<< var3 / "521321" <<endl;
   cout<< "652323" / var1 <<endl;
   ```

   **[optimize later] Modulo (%)**
   
   ```c++
   cout<< var2 % var1 <<endl
   ```
-------------------------------------------------------------------

## FACTORIAL SAMPLE CODE

  ```c++
  // main.cpp
  
  #include <iostream>
  #include "bignum.h"

  using namespace std;

  int main(){

    // A very slow factorial

    cout<<"FACTORIAL OF A NUMBER : "<<endl;

    bignum limit = 1000;
    
    bignum n = limit, fac = "1";

    for(bignum i=1; i<=limit; ++i)
    {
      fac = fac*i;
    }

    cout<<"Answer to factorial of 1000 is : "<<fac<<endl;

    return 0;
  }
  ```
### FACTORIAL SAMPLE CODE: Folder Structure of the code above

- Main_Folder
  - main.cpp
  - bignum.h
  - bignum.lib

### FACTORIAL SAMPLE CODE: compilation `g++ -o output.exe main.cpp bignum.lib -O3`

-------------------------------------------------------------------

### CURRENTLY SUPPORTED OPERATORS (bignumber overloaded operators)

   **IO : <<, >> operator for "cout" output and "cin" input is supported.**
   
   ```c++
   cout << abigintvariable << endl; 
   cin >> abigintvar;
   ```
   
   **COMPARISON : <, >, <=, >=, ==, != (these comparison operators are also available) note: always enclose two bignum values when you are using comparison operators ex:**
   
   ```c++
   bignum large_number = "2887382", big_number = "2367232";
   cout<< (large_number != bignum); //allowed
   ```
   
*Comparison between a bignum variable and a string value or const char* is possible, but you should enclose it with ()*
   
   ```c++
   bignum variable1 = "72736273";
   cout<<(variable1 <= "81283798237")<<endl; // allowed 
   cout<<(-76323.6763f > variable1)<<endl;  // allowed
   ```
   
*WARNING: Do not expect when comparing two "const char*" to behave like two bignum values*
   
   ```c++
   cout<<("76327323" < "2837283"); // this is not allowed
   ```
      
**The increment and decrement operators, postfix and pre-fix form is available.**

  ```c++
  bignum up=0, down="2";
  up++;
  ++up;
  --down;
  down--;
  ```     

### **SUPPORTS INTEGER AND RATIONAL NUMBERS(DECIMAL FORM)** ###

-------------------------------------------------------------------

### HOW?

###### This library uses c++ class to encapsulate methods/function to perform operations on big numbers/large numbers.

## JUST STRINGS

###### This implementation uses string data type to store large numbers/big numbers.

## ELEMENTRAY TECHNIQUES

###### The four basic arithmetic operations are implemented using plain old, slightly tweeked elementary techniques in addition, subtraction, multiplication, and division... yeah that division, addition, subtraction and multiplication where you put the numbers on top of each other to compute the answer, that technique you are doing when you are in grade school, that is what this library is using... nothing fancy like using bitwise operations(idk), and other advance concept.

## IMPLEMENTATION

###### For addition, subtraction, and multiplication every 9 digits (4 digits for multiplication) in the string value of the bignumber is then converted into a long int number then stored into an array of long ints, then arithmetic operations are applied on each index of the array, the results are then processed then each index is converted back and joined into a string... this is how this library mainly works

***The "bignum" user made data type provided by the library enables you to:***

   1. store very large numbers in a variable.   
   
   2. treat it like a normal/primitive data type.
   
   3. perform arithmetic and other operations with it.
   
   4. IDK... you can do anything with it.

[Github Repo - source codes](https://github.com/mrdcvlsc/bignum)

---------------------------------------------------------

### PLANNED UPCOMMING SUPPORTS FOR THE FUTURE

   **operations :**
   
   [ ] POWER FUNCTION
   
   [ ] FACTORIAL FUNCTION (I NEED A FAST ONE - prime swing or multithreading)
   
   [ ] cNr FUNCTION
   
   [ ] pNr FUNTION
   
   [ ] bitwise operators
   
   [ ] cube root / square root / root (fast one)
    
---------------------------------------------------------


### PLANNED IMPROVEMENTS
    
   ***KEEP REDUCING CODE CLUTTER***
   
   ***IMPLEMENT FASTER APPROACHES***
    
---------------------------------------------------------

## WHY I CREATED THIS?
  
   If you're asking...
   I know there are some C++ libraries out there that supports operations for larger integer values
   But I created this as a challenge to myself;
   to gain experience, to practice how to improve existing code, to learn more things along the development process.
   
   *started in 2020, 2nd year CS personal project*
   
# A C++ Class Library that you can use for computing big numbers, using this library you can add, subtract, multiply, divide very large numbers in C++
 
## LICENCE - MIT

