# Classmethods and Staticmethods

## Class Methods

For the classmethods we need to add decoratore
@classmethod just above the methods then in those methods insted of self the class object will be taken 


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
    @classmethod
    def set_rais_amt(cls, amount):
        cls.hike_percent = amount
        
emp_1 = Employee('Melwin', 'Varghese',900000)
emp_2 = Employee('Alwin', 'Varghese', 1000000)
print(Employee.hike_percent)
emp_1.set_rais_amt(.30)
emp_2.set_rais_amt(.40)
print(emp_1.hike_percent) 
print(emp_2.hike_percent)
Employee.set_rais_amt(.20)
print(Employee.hike_percent)
print(emp_1.hike_percent) 
print(emp_2.hike_percent)
```

    0.1
    0.4
    0.4
    0.2
    0.2
    0.2
    

whith this we can create alternate constructor


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
    @classmethod
    def set_rais_amt(cls, amount):
        cls.hike_percent = amount
    @classmethod
    def from_string(cls, emp_str):
        first, last, pay = emp_str.split('-')
        return cls(first, last, pay)
emp_1 = Employee.from_string('Melwin-Varghese-900000')
emp_2 = Employee.from_string('Alwin-Varghese-1000000') 
print(emp_1.__dict__)
print(emp_2.__dict__)
```

    {'first': 'Melwin', 'last': 'Varghese', 'pay': '900000'}
    {'first': 'Alwin', 'last': 'Varghese', 'pay': '1000000'}
    

## Static Method

For the static method its similer to the class method the difference is the decorator name will be @staticmethod and we will not be passing self or class object only the paramete that needed to pass will be there


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
    @classmethod
    def set_rais_amt(cls, amount):
        cls.hike_percent = amount
    @classmethod
    def from_string(cls, emp_str):
        first, last, pay = emp_str.split('-')
        return cls(first, last, pay)
    @staticmethod
    def is_workday(day):
        if day.weekday() == 5 or day.weekday() == 6:
            return False
        return True
    
import datetime
my_data = datetime.date(2016, 7, 11)
print(Employee.is_workday(my_data))
```

    True
    


```python

```
