# Operator Overloading

You can change the meaning of an operator in Python depending upon the operands used.

Python operators work for built-in classes. But the same operator behaves differently with different types. For example, the + operator will perform arithmetic addition on two numbers, merge two lists, or concatenate two strings.

This feature in Python that allows the same operator to have different meaning according to the context is called operator overloading.

So what happens when we use them with objects of a user-defined class? Let us consider the following class, which tries to simulate a point in 2-D coordinate system.

## Overloading the + Operator

To overload the + operator, we will need to implement __add__() function in the class. With great power comes great responsibility. We can do whatever we like, inside this function. But it is more sensible to return a Point object of the coordinate sum.


```python
class Point:
    def __init__(self, x=0, y=0):
        self.x = x
        self.y = y

    def __str__(self):
        return "({0},{1})".format(self.x, self.y)

    def __add__(self, other):
        x = self.x + other.x
        y = self.y + other.y
        return Point(x, y)
    
p1 = Point(1, 2)
p2 = Point(2, 3)
print("p1=", p1)
print("p2=", p2)
print("p1+ p2 =",p1+p2)    
```

    p1= (1,2)
    p2= (2,3)
    p1+ p2 = (3,5)
    

## Other Operational Operators

<table>
<tr>    
    <th>Operator</th>	        
    <th>Expression</th>	       
    <th>Internally</th>
</tr>    
<tr>    
<td>Addition</td>	        
<td>p1 + p2</td>
<td>p1.__add__(p2)</td>
</tr>
<tr>
    <td>Subtraction</td>
    <td>p1 - p2</td>
    <td>p1.__sub__(p2)</td>
</tr>
<tr>
    <td>Multiplication</td>
    <td>p1 * p2</td>
    <td>p1.__mul__(p2)</td>
</tr>
<tr>
    <td>Power</td>
    <td>p1 ** p2</td>
    <td>p1.__pow__(p2)</td>
</tr>
<tr>
    <td>Division</td>
    <td>p1 / p2</td>
    <td>p1.__truediv__(p2)</td>
</tr>
<tr>
    <td>Floor Division</td>
    <td>p1 // p2</td>
    <td>p1.__floordiv__(p2)</td>
</tr> 
<tr>
    <td>Remainder (modulo)</td>
    <td>p1 % p2</td>
    <td>p1.__mod__(p2)</td>
</tr>
<tr>
    <td>Bitwise Left Shift</td>
    <td>p1 << p2</td>
    <td> p1.__lshift__(p2)</td>
</tr>
<tr>
    <td>Bitwise Right Shift</td>
    <td>p1 >> p2</td>
    <td>p1.__rshift__(p2)</td>
</tr>
<tr>
    <td>Bitwise AND</td>
    <td>p1 & p2</td>
    <td>p1.__and__(p2)</td>
</tr>
<tr>
    <td>Bitwise OR</td>
    <td>p1 | p2</td>
    <td>p1.__or__(p2)</td>
</tr>
<tr>
    <td>Bitwise XOR</td>
    <td>p1 ^ p2</td>
    <td>p1.__xor__(p2)</td>
</tr>
<tr>
    <td>Bitwise NOT</td>
    <td>~p1</td>
    <td>p1.__invert__()</td>
</tr>  
</table>    

## Overloading Comparison Operators


```python
# overloading the less than operator
class Point:
    def __init__(self, x=0, y=0):
        self.x = x
        self.y = y

    def __str__(self):
        return "({0},{1})".format(self.x, self.y)

    def __lt__(self, other):
        self_mag = (self.x ** 2) + (self.y ** 2)
        other_mag = (other.x ** 2) + (other.y ** 2)
        return self_mag < other_mag

p1 = Point(1,1)
p2 = Point(-2,-3)
p3 = Point(1,-1)

# use less than
print(p1<p2)
print(p2<p3)
print(p1<p3)
```

    True
    False
    False
    

<table>
    <tr>
        <th>Operator</th>
        <th>Expression</th>
        <th>Internally</th>
    </tr> 
    <tr>
        <td>Less than</td>
        <td>p1 < p2</td>
        <td>p1.__lt__(p2)</td>
    </tr>
    <tr>
        <td>Less than or equal to</td>
        <td>p1 <= p2</td>
        <td>p1.__le__(p2)</td>
    </tr>
    <tr>
        <td>Equal to</td>
        <td>p1 == p2</td>
        <td>p1.__eq__(p2)</td>
    </tr>
    <tr>
        <td>Not equal to</td>
        <td>p1 != p2</td>
        <td>p1.__ne__(p2)</td>
    </tr>  
    <tr>
        <td>Greater than</td>
        <td>p1 > p2</td>
        <td>p1.__gt__(p2)</td>
    </tr>
    <tr>
        <td>Greater than or equal to</td>
        <td>p1 >= p2</td>
        <td>p1.__ge__(p2)</td>
    </tr>    
</table>    


```python

```
