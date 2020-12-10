# Inheritance

Inheritance enables us to define a class that takes all the functionality from a parent class and allows us to add more.

Python Inheritance Syntax
class BaseClass:
  Body of base class
class DerivedClass(BaseClass):
  Body of derived class
Example 


```python
# BaseClass
class Polygon: 
    def __init__(self, no_of_sides):
        self.n = no_of_sides
        self.sides = [0 for i in range(no_of_sides)]

    def inputSides(self):
        self.sides = [float(input("Enter side "+str(i+1)+" : ")) for i in range(self.n)]

    def dispSides(self):
        for i in range(self.n):
            print("Side",i+1,"is",self.sides[i])

# DerivedClass            
class Triangle(Polygon):
    def __init__(self):
        Polygon.__init__(self,3)

    def findArea(self):
        a, b, c = self.sides
        # calculate the semi-perimeter
        s = (a + b + c) / 2
        area = (s*(s-a)*(s-b)*(s-c)) ** 0.5
        print('The area of the triangle is %0.2f' %area)            
```

In the above example, notice that __init__() method was defined in both classes, Triangle as well Polygon. When this happens, the method in the derived class overrides that in the base class. This is to say, __init__() in Triangle gets preference over the __init__ in Polygon.

Generally when overriding a base method, we tend to extend the definition rather than simply replace it. The same is being done by calling the method in base class from the one in derived class (calling Polygon.__init__() from __init__() in Triangle).

A better option would be to use the built-in function super(). So, super().__init__(3) is equivalent to Polygon.__init__(self,3) and is preferred.

### Two built-in functions isinstance() and issubclass()

isinstance() and issubclass() are used to check inheritances.
>>> t = Triangle()
>>> isinstance(t,Triangle)
True

>>> isinstance(t,Polygon)
True

>>> isinstance(t,int)
False

>>> isinstance(t,object)
True

>>> issubclass(Polygon,Triangle)
False

>>> issubclass(Triangle,Polygon)
True

>>> issubclass(bool,int)
True
# Python Multiple Inheritance

## Multiple Inheritance

A class can be derived from more than one base class in Python, similar to C++. This is called multiple inheritance
In multiple inheritance, the features of all the base classes are inherited into the derived class. The syntax for multiple inheritance is similar to single inheritance.

Example


```python
class Base1:
    pass

class Base2:
    pass

class MultiDerived(Base1, Base2):
    pass
```

## Multilevel Inheritance

We can also inherit from a derived class. This is called multilevel inheritance. It can be of any depth in Python.

In multilevel inheritance, features of the base class and the derived class are inherited into the new derived class.


```python
class Base:
    pass

class Derived1(Base):
    pass

class Derived2(Derived1):
    pass

```

## The Diamond Problem

It refers to an ambiguity that arises when two classes Class2 and Class3 inherit from a superclass Class1 and class Class4 inherits from both Class2 and Class3. If there is a method “m” which is an overridden method in one of Class2 and Class3 or both then the ambiguity arises which of the method “m” Class4 should inherit.

![title](https://media.geeksforgeeks.org/wp-content/uploads/20191222084637/Diamond1.png)


```python
class Class1: 
    def m(self): 
        print("In Class1")  
        
class Class2(Class1): 
    def m(self): 
        print("In Class2") 
  
class Class3(Class1): 
    def m(self): 
        print("In Class3")   
         
class Class4(Class2, Class3): 
    pass   
      
obj = Class4() 
obj.m() 
```

    In Class2
    

Note: When you call obj.m() (m on the instance of Class4) the output is In Class2. If Class4 is declared as Class4(Class3, Class2) then the output of obj.m() will be In Class3.

way to solve the use case is depends on the requirement

### Solution 1 using super function


```python
# Python program to demonstrate 
# super() 
  
class Class1: 
    def m(self): 
        print("In Class1") 
  
class Class2(Class1): 
    def m(self): 
        print("In Class2") 
        super().m() 
  
class Class3(Class1): 
    def m(self): 
        print("In Class3") 
        super().m() 
  
class Class4(Class2, Class3): 
    def m(self): 
        print("In Class4")    
        super().m() 
       
obj = Class4() 
obj.m() 
```

    In Class4
    In Class2
    In Class3
    In Class1
    

for more solution check in https://www.geeksforgeeks.org/multiple-inheritance-in-python/


```python

```
