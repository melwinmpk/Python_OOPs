# Python OOPs Introduction

## Class Creation


```python
class Employee:
    pass
```

## Creating a instance of a class


```python
emp_1 = Employee()
emp_2 = Employee()
print(emp_1)
print(emp_2)
```

    <__main__.Employee object at 0x0000026C2D18A888>
    <__main__.Employee object at 0x0000026C2D18A848>
    

In Python we can create the variables to the respective instances  example any way this is not advisiable to create variables like this


```python
emp_1 = Employee()
emp_1.first = 'Corey'
emp_1.last = 'Schafer'
emp_1.email = 'Corey.Schafer@company.com'
emp_1.pay = 50000  
print(emp_1.__dict__)
```

    {'first': 'Corey', 'last': 'Schafer', 'email': 'Corey.Schafer@company.com', 'pay': 50000}
    

We need to createthe variables in the class itself


```python
class Employee:
    def __init__(self, first, last, pay):
        self.first = first
        self.last  = last
        self.pay   = pay

emp_1 = Employee('Melwin', 'Varghese', 900000)
print(emp_1.__dict__)
```

    {'first': 'Melwin', 'last': 'Varghese', 'pay': 900000}
    

Or Another Way is by Class Variables


```python
class Employee:
    first = '' # these are class variable 
    last  = ''
    pay   = 0
    def __init__(self, first, last, pay):
        self.first = first
        self.last  = last
        self.pay   = pay 

emp_1 = Employee('Melwin', 'Varghese', 900000)
print(emp_1.__dict__)
```

    {'first': 'Melwin', 'last': 'Varghese', 'pay': 900000}
    

## Methods in the class


```python
class Employee:
    def __init__(self, first, last, pay):
        self.first = first
        self.last  = last
        self.pay   = pay
    def fullname(self):
        return '{} {}'.format(self.first, self.last)
emp_1 = Employee('Melwin', 'Varghese', 900000)
print(emp_1.__dict__)
print(emp_1.fullname())
print(Employee.fullname(emp_1)) #both are same
```

    {'first': 'Melwin', 'last': 'Varghese', 'pay': 900000}
    Melwin Varghese
    Melwin Varghese
    

## Class Variables 
### Accessing the class variables there are two ways 


 #### 1) Directly formt the Class name we can access/modify and overide the value for entire instances 


```python
class Employee:
    hike_percent = .10
    def __init__(self, first, last, pay):
        self.first = first
        self.last  = last
        self.pay   = pay
    def fullname(self):
        return '{} {}'.format(self.first, self.last)
    def hike_the_pay(self):
        self.pay = self.pay*(1+self.hike_percent)
emp_1 = Employee('Melwin', 'Varghese', 900000)
emp_2 = Employee('Alwin', 'Varghese', 1000000)
emp_1.hike_the_pay()
emp_2.hike_the_pay()
print(Employee.__dict__)
print(emp_1.__dict__)
print(emp_2.__dict__)
Employee.hike_percent = .20 #Directly formt the Class name
emp_1.hike_the_pay()
emp_2.hike_the_pay()
print(Employee.__dict__)
print(emp_1.__dict__)
print(emp_2.__dict__)
```

    {'__module__': '__main__', 'hike_percent': 0.1, '__init__': <function Employee.__init__ at 0x00000211DC452C10>, 'fullname': <function Employee.fullname at 0x00000211DC452F70>, 'hike_the_pay': <function Employee.hike_the_pay at 0x00000211DC494040>, '__dict__': <attribute '__dict__' of 'Employee' objects>, '__weakref__': <attribute '__weakref__' of 'Employee' objects>, '__doc__': None}
    {'first': 'Melwin', 'last': 'Varghese', 'pay': 990000.0000000001}
    {'first': 'Alwin', 'last': 'Varghese', 'pay': 1100000.0}
    {'__module__': '__main__', 'hike_percent': 0.2, '__init__': <function Employee.__init__ at 0x00000211DC452C10>, 'fullname': <function Employee.fullname at 0x00000211DC452F70>, 'hike_the_pay': <function Employee.hike_the_pay at 0x00000211DC494040>, '__dict__': <attribute '__dict__' of 'Employee' objects>, '__weakref__': <attribute '__weakref__' of 'Employee' objects>, '__doc__': None}
    {'first': 'Melwin', 'last': 'Varghese', 'pay': 1188000.0}
    {'first': 'Alwin', 'last': 'Varghese', 'pay': 1320000.0}
    

#### 2) Accessing the the Class variables as instance variables


```python
class Employee:
    hike_percent = .10
    def __init__(self, first, last, pay):
        self.first = first
        self.last  = last
        self.pay   = pay
    def fullname(self):
        return '{} {}'.format(self.first, self.last)
    def hike_the_pay(self):
        self.pay = self.pay*(1+self.hike_percent)
emp_1 = Employee('Melwin', 'Varghese',1000000)
emp_2 = Employee('Alwin', 'Varghese', 1000000)
emp_1.hike_percent  = .20
emp_1.hike_the_pay() # only for the emp_1 instance the hike percent will be 20% 
emp_2.hike_the_pay()
print(Employee.__dict__)
print(emp_1.__dict__)
print(emp_2.__dict__)
```

    {'__module__': '__main__', 'hike_percent': 0.1, '__init__': <function Employee.__init__ at 0x0000026C2D235678>, 'fullname': <function Employee.fullname at 0x0000026C2D2354C8>, 'hike_the_pay': <function Employee.hike_the_pay at 0x0000026C2D235558>, '__dict__': <attribute '__dict__' of 'Employee' objects>, '__weakref__': <attribute '__weakref__' of 'Employee' objects>, '__doc__': None}
    {'first': 'Melwin', 'last': 'Varghese', 'pay': 1200000.0, 'hike_percent': 0.2}
    {'first': 'Alwin', 'last': 'Varghese', 'pay': 1100000.0}
    

#### 3) we can use as a static variables 


```python
class Employee:
    hike_percent = .10
    no_of_employees = 0
    def __init__(self, first, last, pay):
        self.first = first
        self.last  = last
        self.pay   = pay
        Employee.no_of_employees += 1
    def fullname(self):
        return '{} {}'.format(self.first, self.last)
    def hike_the_pay(self):
        self.pay = self.pay*(1+self.hike_percent)
print(Employee.no_of_employees)        
emp_1 = Employee('Melwin', 'Varghese',900000)
emp_2 = Employee('Alwin', 'Varghese', 1000000)
print(Employee.no_of_employees) 
```

    0
    2
    


```python

```
