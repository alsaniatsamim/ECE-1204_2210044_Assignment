## **Assignment No : 01**

## **Assignment Name : Error Detection and Correction in C++ Programs**

## **Submission Date : September 16, 2024**

---

## **Theory :**
<div align="justify">
  
In C++, a class is like a template that groups related data and functions together. The functions inside a class are called methods, and they define how the class behaves.<br>
There are three types of access specifiers in C++ : 
- **Private:** Only the class itself can use these members. <br>
- **Protected:** The class and its child classes can use these members. <br>
- **Public:** Anyone can use these members. <br>

A friend function is a special function that can access the private parts of a class, even though it is not part of that class. Similarly, a friend class can access another class's private data when it is allowed to do so.
</div>

## **Code 1 (With Error) :**
```C++
#include<iostream>
#include<string>
using namespace std;

int main(){
    string name;
    cout << "Enter your name: ";
    getline(name, cin); 
    cout << "Output: " << name << endl;
    return 0;
}
```

## **Error :** 
**Mistake : Passing cin incorrectly to getline**
<p align="center">
<img width="410" height="130" alt="Screenshot 2024-09-16 at 4 00 16 PM" src="https://github.com/user-attachments/assets/69188a41-486d-41f1-89fa-ba112c290a0e">
</p>

## **Discussion :**
<div align="justify">

In this case, the error happens because the arguments to getline are in the wrong order. The correct way is getline(cin, name). If the arguments are reversed, it will cause a compile-time error, meaning the function doesn’t match the expected types. This shows how important it is to put the arguments in the right order when calling a function.
</div>

## **Code 1 (Corrected) :**
```C++
#include<iostream>
#include<string>
using namespace std;

int main(){
    string name;
    int age;
    cout << "Enter your name: ";
    getline(cin, name);
    cout << "Output: " << name << endl;
    return 0;
}
```

## **Output :** 
<p align="center">
<img width="410" height="130" alt="Screenshot 2024-09-16 at 4 08 47 PM" src="https://github.com/user-attachments/assets/0ca00544-75bd-4cd4-aa64-2a1c66a6db68">
</p>

## **Code 2 (With Error) :**
```C++
#include<iostream>
#include<string>
using namespace std;

class MyClass{
    private: 
    int myNum;
    string myString;
};

int main(){
    MyClass myobj;
    myobj.myNum = 15;      
    myobj.myString = "Some Text";
    
    cout << myobj.myNum << "\n";
    cout << myobj.myString;
    return 0;
}
```

## **Error :** 
**Mistake : Accessing private members outside the class**
<p align="center">
<img width="450" height="200" alt="Screenshot 2024-09-16 at 4 13 49 PM" src="https://github.com/user-attachments/assets/16a9f5da-294d-46db-a08e-70c8459add4e">
</p>

## **Discussion :**
<div align="justify">
In this case, the members myNum and myString are private. Accessing or modifying them from outside the class results in a compile-time error. This illustrates the concept of access specifiers in C++ and highlights the difference between public and private members.
</div>

## **Code 2 (Corrected) :**
```C++
#include<iostream>
#include<string>
using namespace std;

class MyClass{
    public:
    int myNum;
    string myString;
};
int main(){
    MyClass myobj;
    myobj.myNum = 15;
    myobj.myString = "Some Text";
    
    cout << myobj.myNum << "\n";
    cout << myobj.myString;
    return 0;
}
```

## **Output :** 
<p align="center">
<img width="410" height="110" alt="Screenshot 2024-09-16 at 4 17 08 PM" src="https://github.com/user-attachments/assets/f38c7f5f-65dc-4391-a7dd-f6eb2296bf78">
</p>

## **Code 3 (With Error) :**
```C++
#include<iostream>
#include<string>
using namespace std;

class myClass{
    public:
    int x;
    private:
    int y;
};
int main(){
    myClass myobj;
    myobj.x = 25;
    myobj.y = 50;
    return 0;
}
```

## **Error :** 
**Mistake 1 : Accessing private members outside the class**<br>
**Mistake 2 : Missing cout to Print Values**
<p align="center">
<img width="410" height="150" alt="Screenshot 2024-09-16 at 4 27 46 PM" src="https://github.com/user-attachments/assets/b2ed2796-fcb7-46cf-a3f8-61f961f0d236">
</p>

## **Discussion :**
<div align="justify">
The variable y is private in the class myClass. Private members cannot be accessed directly from outside the class, including in main(). This causes a compile-time error. In C++, private members should be accessed using public methods like getter and setter functions to keep the object's internal state safe.

The code doesn’t include cout to print the values of x and y. Even though values are assigned, they aren't displayed. Using cout helps check if the values are correctly assigned by showing them to the user.
</div>

## **Code 3 (Corrected) :**
```C++
#include<iostream>
#include<string>
using namespace std;

class myClass{
    public:
    int x;
    private:
    int y;
    public:
    void sety(int value){
        y = value;
    }
    int show(){
        return y;
    }
};
int main(){
    myClass myobj;
    myobj.x = 25;
    myobj.sety(50);
    
    cout << "x: " << myobj.x << endl;
    cout << "y: " << myobj.show() << endl;
    return 0;
}
```

## **Output :** 
<p align="center">
<img width="410" height="90" alt="Screenshot 2024-09-16 at 4 33 01 PM" src="https://github.com/user-attachments/assets/65263138-8da3-480a-82b8-3ef9fe69663c">
</p>

## **Code 4 (With Error) :**
```C++
#include<iostream>
#include<string>
using namespace std;

class Car{
    public:
    string brand;
    string model;
    int year;
};

int main(){
    Car carObj1;
    carObj1.brand = "BMW";
    carObj1.model = "X5";
    carObj1.year = "1999"; 

    Car carObj2;
    carObj2.brand = "Ford";
    carObj2.model = "Mustang";
    carObj2.year = 1969;

    cout << carObj1.brand << " " << carObj1.model << " " << carObj1.year << "\n";
    cout << carObj2.brand << " " << carObj2.model << " " << carObj2.year << "\n";
    
    return 0;
}
```

## **Error :** 
**Mistake : Data Type Mismatch**<br>
<p align="center">
<img width="410" height="130" alt="Screenshot 2024-09-16 at 4 36 18 PM" src="https://github.com/user-attachments/assets/a7d32df6-4384-4d71-b89f-2623d8502213">
</p>

## **Discussion :**
<div align="justify">
In this case, carObj1.year is an int, but the code tries to assign a string ("1999") to it, causing a type mismatch error. C++ is strict about data types and doesn't allow automatic conversion from string to int. This shows the need to match data types correctly when assigning values.
</div>

## **Code 4 (Corrected) :**
```C++
#include<iostream>
#include<string>
using namespace std;

class Car{
    public:
    string brand;
    string model;
    int year;
};
int main(){
    Car carObj1;
    carObj1.brand = "BMW";
    carObj1.model = "X5";
    carObj1.year = 1999;
    
    Car carObj2;
    carObj2.brand = "Ford";
    carObj2.model = "Mustang";
    carObj2.year = 1969;

    cout << carObj1.brand << " " << carObj1.model << " " << carObj1.year << "\n";
    cout << carObj2.brand << " " << carObj2.model << " " << carObj2.year << "\n";
    return 0;
}
```

## **Output :** 
<p align="center">
<img width="410" height="90" alt="Screenshot 2024-09-16 at 4 39 40 PM" src="https://github.com/user-attachments/assets/20570674-7573-4541-a9cc-9dcb5fdeb2c2">
</p>

## **Code 5 (With Error) :**
```C++
#include<iostream>
#include<string>
using namespace std;

class MyClass{
    public:
    void myMethod(){
        cout << "Hello World!";
    }
};

int main(){
    MyClass myObj;
    myObj.myMethod;
    return 0;
}
```

## **Error :** 
**Mistake : Missing function call parentheses**<br>
<p align="center">
<img width="410" height="150" alt="Screenshot 2024-09-16 at 4 42 03 PM" src="https://github.com/user-attachments/assets/fb543c5e-0125-4069-adbe-cfe5febdaac4">
</p>

## **Discussion :**
<div align="justify">
The statement myObj.myMethod; is missing parentheses (), so the method isn't called. In C++, functions must be called with parentheses. Without them, the code compiles, but myMethod() won’t run, and "Hello World!" won’t print. This highlights the need for correct syntax when calling functions.
</div>

## **Code 5 (Corrected) :**
```C++
#include<iostream>
#include<string>
using namespace std;

class MyClass{
    public:
    void myMethod(){
        cout << "Hello World!";
    }
};
int main(){
    MyClass myObj;
    myObj.myMethod();
    return 0;
}
```

## **Output :** 
<p align="center">
<img width="410" height="90" alt="Screenshot 2024-09-16 at 4 45 09 PM" src="https://github.com/user-attachments/assets/7b327c00-31c2-4b1e-a67e-13d18f03f5cf">
</p>

## **Code 6 (With Error) :**
```C++
#include<iostream>
#include<string>
using namespace std;

class MyClass{
    public:
    void myMethod();
};

void MyClass:myMethod(){  
    cout << "Hello World!";
}

int main(){
    MyClass myObj;
    myObj.myMethod();
    return 0;
}
```

## **Error :** 
**Mistake : Using a colon insead of scope resolution operator**<br>
<p align="center">
<img width="410" height="120" alt="Screenshot 2024-09-16 at 4 48 50 PM" src="https://github.com/user-attachments/assets/7fba98b9-6b5d-48ca-9e24-58bb05f85c16">
</p>

## **Discussion :**
<div align="justify">
A colon (:) is incorrectly used instead of the scope resolution operator (::). This causes a syntax error because the compiler won't link the method to MyClass. The correct syntax is required to associate the method with its class.
</div>

## **Code 6 (Corrected) :**
```C++
#include<iostream>
#include<string>
using namespace std;

class MyClass{
    public:
    void myMethod();
};
void MyClass::myMethod(){
    cout << "Hello World!";
}
int main(){
    MyClass myObj;
    myObj.myMethod();
    return 0;
}
```

## **Output :** 
<p align="center">
<img width="410" height="90" alt="Screenshot 2024-09-16 at 4 45 09 PM" src="https://github.com/user-attachments/assets/7b327c00-31c2-4b1e-a67e-13d18f03f5cf">
</p>

## **Code 7 (With Error) :**
```C++
#include<iostream>
using namespace std;

class Car{
    public:
    int speed(int maxSpeed); 

void Car::speed(int maxSpeed){  
    return maxSpeed;  
}

int main(){
    Car myObj;
    cout << myObj.speed(200);
    return 0;
}
```

## **Error :** 
**Mistake : Using void instead of int**<br>
<p align="center">
<img width="410" height="180" alt="Screenshot 2024-09-16 at 4 55 14 PM" src="https://github.com/user-attachments/assets/aa84ddef-2011-4801-a033-7c8eca178e0b">
</p>

## **Discussion :**
<div align="justify">
The method is incorrectly defined as void, but it tries to return maxSpeed. A void function can't return any value, leading to an error. This shows the importance of matching the return type with the function's declaration.
</div>

## **Code 7 (Corrected) :**
```C++
#include<iostream>
using namespace std;
class Car{
    public:
    int speed(int maxSpeed);
};
int Car::speed(int maxSpeed){
    return maxSpeed;
}
int main(){
    Car myObj;
    cout<<myObj.speed(200);
    return 0;
}
```

## **Output :** 
<p align="center">
<img width="410" height="90" alt="Screenshot 2024-09-16 at 5 00 47 PM" src="https://github.com/user-attachments/assets/4eea9619-4dba-41f4-ad20-40d94be3202f">
</p>

## **Code 8 (With Error) :**
```C++
#include<iostream>
using namespace std;

class Box{
    private:
    double width;
    public:
    void setWidth(double w){
        width = w;
    }
    friend void printWidth(Box &b);  
};

void printWidth(Box b){  
    cout << endl << "Width: " << b.width << endl;  
}

int main(){
    Box myBox;
    myBox.setWidth(10.0);
    printWidth(myBox);
    return 0;
}
```

## **Error :** 
**Mistake : Mismatched Parameter Type for Friend Function**<br>
<p align="center">
<img width="410" height="150" alt="Screenshot 2024-09-16 at 5 03 37 PM" src="https://github.com/user-attachments/assets/62b76138-5bf7-4221-a085-c899949f18b5">
</p>

## **Discussion :**
<div align="justify">
The function is defined with a parameter type of Box (by value) instead of Box & (by reference). This mismatch causes the compiler to not recognize the function as the one declared as a friend. Because printWidth(Box b) isn’t a friend, it can’t access the private members of Box.
</div>

## **Code 8 (Corrected) :**
```C++
#include<iostream>
using namespace std;
class Box{
    private:
    double width;
    public:
    void setWidth(double w){
        width = w;
    }
    friend void printWidth(Box& b);
};
void printWidth(Box& b){
    cout << endl << "Width: " << b.width << endl;
}
int main(){
    Box myBox;
    myBox.setWidth(10.0);
    printWidth (myBox);
    return 0;
}
```

## **Output :** 
<p align="center">
<img width="410" height="100" alt="Screenshot 2024-09-16 at 5 06 13 PM" src="https://github.com/user-attachments/assets/8e47df42-0137-4106-939c-a727082463d2">
</p>

## **Code 9 :**
```C++
#include<iostream>
using namespace std;
class Box{
    private:
    double width;
    public:
    friend double getWidth(Box& b);
    void setWidth(double w){
        width = w;
    }
};
double getWidth (Box& b){
    return b.width;

}
int main(){
    Box myBox;
    myBox.setWidth(10.0);
    cout << "Width: " << getWidth(myBox) << endl;
    return 0;
}
```

## **Discussion :**
<div align="justify">
No error is found in this code.
</div>

## **Output :** 
<p align="center">
<img width="410" height="90" alt="Screenshot 2024-09-16 at 5 15 32 PM" src="https://github.com/user-attachments/assets/cfd23860-68d9-4fd6-af6a-ac39a8300f77">
</p>

## **Code 10 (With Error) :**
```C++
#include<iostream>
using namespace std;

class Box{
    private:
    double width;
    public:
    void setWidth(double w);
       
    void printWidth(Box& b);  
};

void Box::setWidth(double w){
    width = w;
}

void printWidth(Box& b){
    cout << endl << "Width: " << b.width << endl;  
}

int main(){
    Box myBox;
    myBox.setWidth(10.0);
    
    printWidth(myBox);  
    return 0;
}
```

## **Error :** 
**Mistake : Omitting the friend Keyword in the Class Declaration**<br>
<p align="center">
<img width="410" height="150" alt="Screenshot 2024-09-16 at 5 33 23 PM" src="https://github.com/user-attachments/assets/81e6cf77-0147-467a-ae42-00583e2dc541">
</p>

## **Discussion :**
<div align="justify">
The friend keyword is missing in the class declaration. Without this, printWidth cannot access the private member width, leading to a compile-time error, as non-friend functions can't access private members.
</div>

## **Code 10 (Corrected) :**
```C++
#include<iostream>
using namespace std;
class Box{
    private:
    double width;
    public:
    void setWidth(double w);
       
    friend void printWidth(Box& b);
};
void Box :: setWidth(double w){
    width = w;
}
void printWidth(Box& b){
    cout << endl << "Width: " << b.width << endl;
}
int main(){
    Box myBox;
    myBox.setWidth(10.0);
    
    printWidth (myBox);
    return 0;
}
```

## **Output :** 
<p align="center">
<img width="410" height="100" alt="Screenshot 2024-09-16 at 5 38 43 PM" src="https://github.com/user-attachments/assets/e16479a1-c317-402f-95b6-8cf51b34e611">
</p>

## **Code 11 (With Error) :**
```C++
#include<iostream>
#include<string>
using namespace std;

class A{
    private:
    int value;
    public:
    A(int v){
        value = v;
    }
    friend class B;
};

class B{
    private:
    int b = 10;
    public:
    void showValue(A& a){
        cout << "Value: " << a.value << endl;
    }
    void show (){
        cout << "Value: " << b << endl;
    }
};

int main(){
    A objA(42);
    B objB;
    
    objA.showValue(); 
    objB.show();
    return 0;
}
```

## **Error :** 
**Mistake : Trying to Call a Method of a Class using an Object of another Class**<br>
<p align="center">
<img width="410" height="120" alt="Screenshot 2024-09-16 at 5 43 30 PM" src="https://github.com/user-attachments/assets/b2972966-114f-4e56-8a71-46811886c346">
</p>

## **Discussion :**
<div align="justify">
In the line objA.showValue();, the code attempts to call the showValue() method on an object of class A. However, showValue() is defined in class B, not A. Since class A does not have a showValue() method, this causes a compilation error.
</div>

## **Code 10 (Corrected) :**
```C++
#include<iostream>
#include<string>
using namespace std;

class A{
    private:
    int value;
    public:
    A(int v){
        value = v;
    }
    friend class B;
};
class B{
    int b=10;
    public:
    void showValue(A& a){
        cout << "Value: " << a.value << endl;
    }
    void show (){
        cout << "Value: " << b << endl;
    }
};
int main(){
    A objA(42);
    B objB;
    
    objB.showValue(objA);
    objB.show();
    return 0;
}
```

## **Output :** 
<p align="center">
<img width="410" height="120" alt="Screenshot 2024-09-16 at 5 47 44 PM" src="https://github.com/user-attachments/assets/9df6c5b7-7b85-4d59-bf29-514b62d39aa4">
</p>


## **Conclusion :**
<div align="justify">
</div>
<br>







