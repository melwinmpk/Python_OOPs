# Property Decorators - Getters, Setters, and Deleters

# Getters

For the getters its pretty simple we need to add the decorator @property to the method so that we can call the method as a variable


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
    @property
    def email(self):
        return '{first}.{last}@gmail.com'.format(first=self.first,last=self.last)
emp_1 = Employee('Melwin','Varghese','900000')  
print(emp_1.email)

```

    Melwin.Varghese@gmail.com
    

## Setters

For the getters its pretty simple we need to add the decorator @{attributename}.setter to the method so that we can call the method as a variable


```python
class Employee:
    hike_percent = .10
    no_of_employees = 0
    def __init__(self, first, last, pay):
        self.first = first
        self.last  = last
        self.pay   = pay
        Employee.no_of_employees += 1     
    @property
    def fullname(self):
        return '{} {}'.format(self.first, self.last)
    def hike_the_pay(self):
        self.pay = self.pay*(1+self.hike_percent)
    @property
    def email(self):
        return '{first}.{last}@gmail.com'.format(first=self.first,last=self.last)
    @fullname.setter
    def fullname(self,name):
        self.first, self.last = name.split(' ')
emp_1 = Employee('Melwin','Varghese','900000')  
print(emp_1.email)
emp_1.fullname = "Alwin Varghese"
print(emp_1.fullname)
print(emp_1.email)

```

    Melwin.Varghese@gmail.com
    Alwin Varghese
    Alwin.Varghese@gmail.com
    

## Deleters

For the getters its pretty simple we need to add the decorator @{attributename}.deleter to the method so that we can call the method as a variable


```python
class Employee:
    hike_percent = .10
    no_of_employees = 0
    def __init__(self, first, last, pay):
        self.first = first
        self.last  = last
        self.pay   = pay
        Employee.no_of_employees += 1     
    @property
    def fullname(self):
        return '{} {}'.format(self.first, self.last)
    def hike_the_pay(self):
        self.pay = self.pay*(1+self.hike_percent)
    @property
    def email(self):
        return '{first}.{last}@gmail.com'.format(first=self.first,last=self.last)
    @fullname.setter
    def fullname(self,name):
        self.first, self.last = name.split(' ')
    @fullname.deleter
    def fullname(self):
        self.first = None
        self.last = None
        self.pay = None
        Employee.no_of_employees -= 1
        
emp_1 = Employee('Melwin','Varghese','900000')  
print(emp_1.email)
emp_1.fullname = "Alwin Varghese"
print(emp_1.fullname)
print(emp_1.email)
print(Employee.no_of_employees)
del emp_1.fullname
print(Employee.no_of_employees)



```

    Melwin.Varghese@gmail.com
    Alwin Varghese
    Alwin.Varghese@gmail.com
    1
    0
    


```python

```
