---
layout: post
published: True
title: Post 3 With Ipython
---


# Fangohr, Hans. Introduction to Python for Computational Science and Engineering, 2015.
Embleton | 20160910 | Notes


### General Notes
* Use `help()` with a command for details
* Use `dir()` with a command for a list of available methods


## Chapter 2, A Powerful Calculator


```python
import math
```


```python
dir(math)

help(math.exp)

math.pi

math.e
```

    Help on built-in function exp in module math:
    
    exp(...)
        exp(x)
        
        Return e raised to the power of x.
    
    




    2.718281828459045



## Chapter 3, Data Types and Structures

* use cmath library to calculate complex results
* Strings are immutable, lists are mutable
* `dir("")` outputs a list of available methods
* Sequences
    * `a[i]` returns the ith element of a
    * `a[i:j]` returns elements i up to j-1
    * `len(a)` returns number of elements in a sequence
    * `min(a)` returns the smallest value in a seq.
    * `max(a)` 
    * `x in a` returns True if x is an element in a
    * `a + b` concatenates seq. a and seq. b
    * `n * a` creates n copies of seq. a
* The `split()` method seperates the string where it finds white space or at a seperator character.
* The join method is the opposite of split
* Lists
    * Empty list given by `x = []`
    * You can mix objects within a list
    * You can add lists within lists
        * ? Is this the proper method for making tables? Hopefully not.
    * `append()` to add an object to the end of a list, opposite is `remove()`
    * `range()` command common in for loops. Use: range(start, stop, step size)
        * Range is a type! 
* Tuple
    * Immutable
    * Empty tuple given by `t = ()`
    * Tuple containing one object `t = (x,)`. The comma is required.
* Indexing
    * Use negative numbers to retrieve values from the back of the list
* Slicing
    * Slicing is different from indicing as it corresponds to the point between two indicies.
* Dictionaries
    * empty dictionary: `d = {}`
    * look for matches with: `d.has_key()` or `d.has_item()`
    * method `get(key, default)` to retrieve values or default if key not found
    * Keyword can be any immutable object
    * Dictionaries are very fast when retreiving values (when given the key)
* Passing arguments to functions
    * Modifications to values of an arguement in a function can affect the value of the original object
* Copying
    * `b = a` does not pass a copy of a to b and create two seperate objects.  Instead b and a refer to the same object.  Only the lable is copied. To create a copy of a with a differnt label, use something like `c = a[:]`
    * use `id(a)` to determine if objects are the same or different
* Equality Operators
    * <, >, ==, >=, <=, !=
    * Does not depend on type
    * To compare the id use, `a is b`.  Objects with different types will not have the same id
    






```python
import cmath

cmath.sqrt(-1)
```




    1j




```python
a = 'This is a test sentence

print(a)

print(a.upper())

print(a.split())
```

    This is a test sentance
    THIS IS A TEST SENTANCE
    ['This', 'is', 'a', 'test', 'sentance']
    


```python
b = "The dog is hungry. The cat is bored. The snake is awake."
print(b)

s=b.split(".")

print(s)

print(".".join(s))

print(" STOP".join(s))
```

    The dog is hungry. The cat is bored. The snake is awake.
    ['The dog is hungry', ' The cat is bored', ' The snake is awake', '']
    The dog is hungry. The cat is bored. The snake is awake.
    The dog is hungry STOP The cat is bored STOP The snake is awake STOP
    


```python
a = [1, 2, 3]

print(a)

a.append(45)

print(a)

a.remove(2)

print(a)
```

    [1, 2, 3]
    [1, 2, 3, 45]
    [1, 3, 45]
    


```python
print(range(3, 10))

for i in range(3,11):
    print(i**2)
```

    range(3, 10)
    9
    16
    25
    36
    49
    64
    81
    100
    


```python
a = 100, 200, 'duck'
print(a)
print(type(a))

x, y = 10, 20
print(x)
print(y)

x, y = y, x
print(x)
print(y)
```

    (100, 200, 'duck')
    <class 'tuple'>
    10
    20
    20
    10
    


```python
a = 'dog cat mouse'
a = a.split()
print(a[0])
print(a[-1])
print(a[-2:])
```

    dog
    mouse
    ['cat', 'mouse']
    


```python
## Dictionaries
d = {}
d['today'] = [1, 2, 3]

d['yesterday'] = '19 deg C'

print(d.keys())
print(d.values())
print(d.items())

print(d)
print(d['today'])
print(d['today'][1])

# Other methods for creating dictionaries
d2 = {2:4, 3:9, 4:16}
print(d2)

d3 = dict(a=1, b=2, c=3)
print(d3)
print(d3['a'])

print(d.__contains__('today'))
d.get('today','unknown')
```

    dict_keys(['today', 'yesterday'])
    dict_values([[1, 2, 3], '19 deg C'])
    dict_items([('today', [1, 2, 3]), ('yesterday', '19 deg C')])
    {'today': [1, 2, 3], 'yesterday': '19 deg C'}
    [1, 2, 3]
    2
    {2: 4, 3: 9, 4: 16}
    {'c': 3, 'b': 2, 'a': 1}
    1
    True
    




    [1, 2, 3]




```python
# Dictionary Example

# create an empty directory
order = {}

# add orders as they come in
order['Peter'] = 'Pint of bitter'
order['Paul'] = 'Half pint of Hoegarden'
order['Mary'] = 'Gin Tonic'

# deliver order at bar
for person in order.keys():
    print(person, "requests", order[person])

```

    Peter requests Pint of bitter
    Paul requests Half pint of Hoegarden
    Mary requests Gin Tonic
    


```python
#Copying and Identity

a = [1, 2, 3, 4, 5]
b=a
b[0] = 42

print(a)

c = a[:]
c[1] = 99

print(a)
print(c)
print('id a: ', id(a))
print('id b: ', id(b))
print('id c: ', id(c))
```

    [42, 2, 3, 4, 5]
    [42, 2, 3, 4, 5]
    [42, 99, 3, 4, 5]
    id a:  118254856
    id b:  118254856
    id c:  119780616
    

## Chapter 4, Introspection

* Magic names start and end with a double underscore
* `isinstance(<unit>, <type space>)` Returns true if the given object is of the given type.
* `help(<object>)`
* `help()` Starts aand interactive help utility
* Provide a docstring for user defined functions



```python
# Example of documenting a user defined function and calling it.

def power2and3(x):
    """Returns the tuple (x**2, x**3)"""
    return x**2 ,x**3

print(power2and3(2))

print(power2and3.__doc__)

help(power2and3)
```

    (4, 8)
    Returns the tuple (x**2, x**3)
    Help on function power2and3 in module __main__:
    
    power2and3(x)
        Returns the tuple (x**2, x**3)
    
    

## Chapter 5, Input and Output

* String specifiers, reprinted table below
* Pg 54-55 for a more elegant method of string formatting used in Python 3
* `fileobject.readlines()` method returns a list of strings
   



```python
## Copied from pg 52.

AU = 149597870700  #Astronomical unit in [m]
"%g" %AU
```




    '1.49598e+11'



|Specifier|Style|Example Output for AU|
|:---:|:---:|:---|
|`%f`|Floating Point|149597870700.000000|
|`%e`|Exponential Notation|1.495979e+11|
|`%g`|Shorter of %e or %f|1.49598e+11|
|`%d`|Integer|149597870700|
|`%s`|String|149597870700|
|`%r`|repr|149597870700L|


```python
a = math.pi

print("Short pi = %.2f. longer pi = %.12f."  %(a, a))
```

    Short pi = 3.14. longer pi = 3.141592653590.
    


```python
## Reading and Writing Files

#1. Write a File
out_file = open("test.txt", "w")    # 'w' stands for Writing
out_file.write("Writing text to file. This is the first line.\n"
              "And the second lineasdfa.")
out_file.close()                    # close the file

#2. Read a File
in_file = open("test.txt", "r")       # 'r' stands for Reading
text = in_file.read()

in_file.close()

#3. Display Data
print (text)
```

    Writing text to file. This is the first line.
    And the second lineasdfa.
    


```python
## Readlines Example

myexp = open("myfile.txt", "w")    # 'w' stands for Writing
myexp.write("This is the first line.\n"
            "This is the second line.\n"
            "This is the third and last line.")
myexp.close()

f = open('myfile.txt', "r")
print(len(f.read()))
f.close()

f = open('myfile.txt', "r")
for line in f.readlines():
    print("%d characters" %len(line))
f.close()
```

    81
    24 characters
    25 characters
    32 characters
    

# Chapter 6, Control Flow

* If-then-else statements
* For loops
* use logical operators "`and`" and "`or`" to combine conditions
* Read chapter 8 for more on errors and exceptiosn, help('exceptions')


```python
a = 17

if a == 0:
    print("a is zero")
elif a < 0:
    print("a is negative")
else:
    print("a is positive")
```

    a is positive
    


```python
# for example
for animal in ['dog', 'cat', 'mouse']:
    print(animal, animal.upper())
    
for i in range(5,10):
    print(i)
```

    dog DOG
    cat CAT
    mouse MOUSE
    5
    6
    7
    8
    9
    

## Chapter 7, Functions and Modules

* A function takes an argument and returns a result or return value.
* Function parameter may have default values.
    * ie. `def print_multi_table(n, upto=10):`
* Common to have an `if __name__ == "__main__` to output results and capabilities only seen when program is runnin on its own.

Generic Function Format:

    def my_function(arg1, arg2, ..., argn):
        """Optional docstring."""
    
        #Implementation of the function
    
        return result #optional

    #this is not part of the function
    some_command
    



```python
help(__future__)
```


    

    NameErrorTraceback (most recent call last)

    <ipython-input-157-5013c2357ebb> in <module>()
    ----> 1 help(__future__)
    

    NameError: name '__future__' is not defined


## Chapter 8, Functional Tools

* Examples using the tools `filter`, `reduce`, and `lamda`.
* An anonymous function is only needed once or needs no name
    * `lambda x : x**2`
    * `(lambda x, y, z: (x + y) * z)(10, 20, 2)`
* The map function applies function f to all elements in sequence s, `lst2 = map(f,s)`
    * `map(lambda x:x**2, range(10))`
* The filter function applies the function f to all elements in a sequence s, `lst2 = filter(f, lst)`
    * The filet function should return a true or false.
    * `filter(lambda x:x>5,range(11))`
* List comprehension is an expression followed by a for clause, then zero or more for or if clauses.  More consise then the above methods.



```python
## Maps

def f(x):
    return x**2

# Two methods to print
print(list(map(f, range(10))))

for ch in map(f, range(10)):
    print(ch)

#Combining with Lambda
print(list(map(lambda x:x**2,range(10))))
    
```

    [0, 1, 4, 9, 16, 25, 36, 49, 64, 81]
    0
    1
    4
    9
    16
    25
    36
    49
    64
    81
    [0, 1, 4, 9, 16, 25, 36, 49, 64, 81]
    


```python
## List Comprehensions

vec = [2, 4, 6]
print(vec)
print([3 * x for x in vec])
print([3 * x for x in vec if x >3])
print([3 * x for x in vec if x <2])
print([[x, x**2] for x in vec])
```

    [2, 4, 6]
    [6, 12, 18]
    [12, 18]
    []
    [[2, 4], [4, 16], [6, 36]]
    

## Chapter 9, Common Tasks

* Illustrates many ways to compute a series to illustrate the differnt methods possible and also illustrate the different methods we've previously discussed.  Includes a check method and doc file.
* `sorted` returns a copy of a sorted list while `sort` changes the list insto a sorted order of elements


## Chapter 10, Matlab to Python
* Common differences
* The extension library numpy provides matrix functionality similar to Matlab

## Chapter 11, Python Shells

* Useful features of different Python shells
* iPython, IPython Notebook, Spyder

## Chapter 12, Symbolic Computation

* SymPy is the Python Symbolic library, [SymPy Homepage](http://sympy.org) for full and up-to-date documentation
* Very slow compared to floating point opperation
* isympy an exexutable wrapper around python, convenient for figuring out new features or experementing interactively
* Rational type, Rational(1,2) represents 1/2.
    * Rational class works exactly as opposed to the standard float.
* If Sympy returns the result in an unfamiliar form, subtract it with the expected form to determine if they are equivalent.
* Calculate definite integrals with a tuple containing the variable of interest, lower, and upper bounds.
* Results from dsolve are an Equality class, function needs to be evaluated to a number to be plotted.
* Covers series expansion
* LaTeX and Pretty printing
* `preview()` allows you to display rendered output on the screen
* Automatic generation of C code via `codegen()`



```python
## Symbols

import sympy

x, y, z = sympy.symbols('x, y, z')

a = x + 2*y + 3*z - x

print(a)

print(sympy.sqrt(8))
```

    2*y + 3*z
    2*sqrt(2)
    


```python
x, y = sympy.symbols('x,y')
a = x + 2*y
print(a.subs(x, 10))
print(a.subs(x,10).subs(y,3))
print(a.subs({x:10, y:3}))

SS_77 =  -y + -23.625*x**3 - 5.3065*x**2 + 5.6633*x
SS_52 =  -y + -245.67*x**3 + 31.951*x**2 + 4.4341*x
SS_36 =  -y + -18.58*x**3 - 5.4025*x**2 + 2.1623*x



#print("t0 = 36, 0.5 Strain at %.2f MPa" % sympy.solve(SS_36.subs(y, 0.5),x)[0])
#print("t0 = 52, 0.5 Strain at %.2f MPa" % sympy.solve(SS_52.subs(y, 0.5),x)[0])
#print("t0 = 77, 0.5 Strain at %.2f MPa" % sympy.solve(SS_77.subs(y, 0.5),x)[0])

print("t0 = 36, 0.01 Stress at %.3f Strain" % sympy.solve(SS_36.subs(x, .01),y)[0])
print("t0 = 52, 0.01 Stress at %.3f Strain" % sympy.solve(SS_52.subs(x, .01),y)[0])
print("t0 = 77, 0.01 Stress at %.3f Strain" % sympy.solve(SS_77.subs(x, .01),y)[0])
```

    2*y + 10
    16
    16
    t0 = 36, 0.01 Stress at 0.021 Strain
    t0 = 52, 0.01 Stress at 0.047 Strain
    t0 = 77, 0.01 Stress at 0.056 Strain
    


```python
a = sympy.Rational(2,3)
print(a)
print(float(a))
print(a.evalf())
print(a.evalf(50))
```

    2/3
    0.6666666666666666
    0.666666666666667
    0.66666666666666666666666666666666666666666666666667
    


```python
# Differentiation

print(sympy.diff(3*x**4, x))
print(sympy.diff(3*x**4, x, x, x))
print(sympy.diff(3*x**4, x, 3))
```

    12*x**3
    72*x
    72*x
    


```python
## Integration

from sympy import integrate

print(integrate(sympy.sin(x), y))
print(integrate(sympy.sin(x), x))

# Definite Integrals
print(integrate(x*2, x))
print(integrate(x*2, (x, 0, 2)))
print(integrate(x**2, (x,0,2), (x, 0, 2), (y,0,1)))
```

    y*sin(x)
    -cos(x)
    x**2
    4
    16/3
    


```python
## Ordinary Differential Equations

from sympy import Symbol, dsolve, Function, Derivative, Eq

y = Function("y")
x = Symbol('x')
y_ = Derivative(y(x), x)
print(dsolve(y_ + 5*y(x), y(x)))
print(dsolve(Eq(y_ + 5*y(x), 0), y(x)))
print(dsolve(Eq(y_ + 5*y(x), 12), y(x)))
```

    Eq(y(x), C1*exp(-5*x))
    Eq(y(x), C1*exp(-5*x))
    Eq(y(x), C1*exp(-5*x)/5 + 12/5)
    


```python
## Linear Equations and Matrix Inversion

from sympy import symbols, Matrix

x, y, z = symbols('x,y,z')

A = Matrix(([3,7], [4,-2]))
print(A)

print(A.inv())
```

    Matrix([[3, 7], [4, -2]])
    Matrix([[1/17, 7/34], [2/17, -3/34]])
    


```python
## Solving Non Linear Equations

import sympy

x, y, z = sympy.symbols('x,y,z')
eq = x - x**2
print(sympy.solve(eq,x))
```

    [0, 1]
    

## Chapter 14, Numerical Calculation

* Limitations of the different number types: int, float, complex, and long.
* Comparing float and symbolic time to compute.

## Chapter 15, Numerical Python (numpy): arrays

* The data structure, `array`, allows efficient matrix and vector operation
* An array can only keep elements of the same type, as opposed to lists which can hold a mix.
* Convert a matrix back tp a list or tuple using, `list(s)` or `tuple(s)`.
* Computing eiganvectors and eiganvalues
* Numpy examples at [SciPy.org](http://www.scipy.org/Numpy_Example_List)




```python
## Vectors (1d-arrays)

import numpy as N

x = N.array([0, 0.5, 1, 1.5])

print(x)

print(N.zeros(4))
a = N.zeros((5,4))
print(a)
print(a.shape)

print(a[2,3])

random_matrix = N.random.rand(5,5)
print(random_matrix)

x = N.random.rand(5)

b = N.dot(random_matrix, x)
print("b= ", b)

```

    [ 0.   0.5  1.   1.5]
    [ 0.  0.  0.  0.]
    [[ 0.  0.  0.  0.]
     [ 0.  0.  0.  0.]
     [ 0.  0.  0.  0.]
     [ 0.  0.  0.  0.]
     [ 0.  0.  0.  0.]]
    (5, 4)
    0.0
    [[ 0.40586402  0.3751796   0.07520575  0.04377951  0.50251993]
     [ 0.15624137  0.98907939  0.28103249  0.0530061   0.44953567]
     [ 0.33179472  0.86670563  0.35891555  0.34783184  0.42391847]
     [ 0.79664181  0.86991121  0.88200181  0.72128736  0.466348  ]
     [ 0.69840165  0.16322735  0.95999346  0.96007779  0.27195858]]
    b=  [ 0.2963257   0.78371708  0.82267624  1.36913152  1.08810305]
    


```python
## Curve Fitting of Polynomial Example

import numpy

# demo curve fitting: xdata and ydata are input data
xdata = numpy.array([0.0, 1.0, 2.0, 3.0, 4.0, 5.0])
ydata = numpy.array([0.0, 0.8, 0.9, 0.1, -0.8, -1.0])

#now fit for cubic (order = 3) polynomial
z = numpy.polyfit(xdata, ydata, 3)

#z is an array of coefficients, highest first, i.e.
#          x^3         X^2      X       0
#z=array([0.08703704, -0.8134, 1.693, -0.0396])

print("z = ", z)

#It is convenient to use `poly1d` objects for dealing with polynomials
p = numpy.poly1d(z)    #Creates a polynomial function p from coefficients and p can be evaluated for all x then.

print("p = ",p)

#Create a plot
xs = [0.1 * i for i in range(50)]
ys = [p(x) for x in xs]    # evaluates p(x) for all x in list xs

%matplotlib inline
import pylab
pylab.plot(xdata, ydata, 'o', label = 'data')
pylab.plot(xs, ys, label = 'fitted curve')
pylab.ylabel('y')
pylab.xlabel('x')
pylab.savefig('polyfit.pdf')
pylab.show()
```

    z =  [ 0.08703704 -0.81349206  1.69312169 -0.03968254]
    p =           3          2
    0.08704 x - 0.8135 x + 1.693 x - 0.03968
    


![png](ipyim/Fangohr_Python_Intro_files/Fangohr_Python_Intro_46_1.png)


## Chapter 15, Visualizing Data

* Need to include all the useful links here
* IPython Inline mode via: `%matplotlib inline`, `%matplotlib qt`, or `%pylab`.
* `help(pylab.legend)` for legend placement information
* `help(pylab.plot)` for line style, color, thickness, etc calls
    * Colors can be called out in RGB, Hex, greyscale, etc.
* Subplot to call more than one plot in one figure, `pylab.subplot(numRows, numCols, plotNum)`.
* Multiple figures via: `pylab.figure(figNum)`.
* `pylab.close()` may be used to close one, some, or all figures.
* Use `pyplot.imshow()` to visualize matrix data (heat plot).
    * Use different color maps with the module `matplotlib.cm`
* Check out the contour_demo.py example for illustrating `z=f(x,y)`
* Visual Python is a module that allows you to create and animate 3D scenes.
    * Visual Python [Home Page](http://vpython.org)
    * Useful for illustrating time dependent data
* Visualising 2D and 3D fields as a function of time with the Visualization Toolkit, [VTK](http://vtk.org).
* Other modules: Mayavi, Paraview, and VisIt.




```python
## Plot details example

import pylab
import numpy as N

%matplotlib inline

x = N.arange(-3.14, 3.14, 0.01)
y1 = N.sin(x)
y2 = N.cos(x)

pylab.figure(figsize=(5,5))    #Sets figure size to 5 x 5 in.
pylab.plot(x, y1, label='sin(x)')
pylab.plot(x, y2, label='cos(x)')
pylab.legend()
pylab.grid()
pylab.xlabel('x')
pylab.title('This is the Title')
pylab.axis([-2,2,-1,1])
pylab.show()

```


![png](ipyim/Fangohr_Python_Intro_files/Fangohr_Python_Intro_48_0.png)



```python
## Histogram Example

import numpy as np
import matplotlib.mlab as mlab
import matplotlib.pylab as plt

# create data
mu, sigma = 100, 15
x = mu + sigma * np.random.randn(10000)

#histogram of the data
n, bins, patches = plt.hist(x, 50, normed=1, facecolor='green', alpha=0.75)

#fine tuning the plot
plt.xlabel('Smarts')
plt.ylabel('Probability')

#LaTeX strings for labels and titles
plt.title(r'$\mathrm{Histogram\ of\ IQ :}\ \mu=100,\ \sigma=15$')
plt.axis([40, 160, 0, 0.03])
plt.grid(True)

#add a best fit line curve
y = mlab.normpdf(bins, mu, sigma)
l = plt.plot(bins, y, 'r--', linewidth=1)
             
#Save to file
plt.savefig('pylabhistogram.pdf')
#then display
plt.show()

```


![png](ipyim/Fangohr_Python_Intro_files/Fangohr_Python_Intro_49_0.png)


## Chapter 16, Numerical Methods using Python (scipy)

* The `scipy` package privides numerous numerical algorithms
* All functionality from `numpy` may be available in `scipy`
* Using `help(scipy)` will detail the package structure.  You can call specific sections ie. `import scipy.integrate`.
* Use `scipy.quad()` to solve integrals of the form $\int_{a}^{b} f(x)dx$
    * Functions that approach +/- inf may be difficult to handle numerically.  Plot results with integand to check
* Use `scipy.odeint()` to solve differential equations of the type $\frac{\partial y}{\partial t}(t) = f(y,t)$
    * `help(scipy.integrate.odeint)` to explore differnet error tolerance options
* Using the `bisect()` method to find roots.  Requires arguments f(x), lower limit, and upper limit.  Optional xtol parameter.
* Using `fsolve()` to find roots is more efficient, but not garunteed to converge.  Input argument is a starting location suspected close to the root.
* The function `y0 = scipy.interpolate.interp1d(x, y, kind='nearest')` may be used to interpolate the data $(x_i, y_i)$ for all x.
* A generic curve fitting function is provided with `scipy.optimize.curve_fit()`
* FFT example below
* Optimization, using `scipy.optimize.fmin()` to find the minimum of a function. Arguments are the function and starting point.




```python
## Integral Example

from math import cos, exp, pi
from scipy.integrate import quad

#function  we want to integrate
def f(x):
    return exp(cos(-2 * x * pi)) + 3.2

#call quad to integrate f from -2 to 2
res, err = quad(f, -2, 2)

print("The numerical result is {:f} (+/-{:.2g})" .format(res, err))
```

    The numerical result is 17.864264 (+/-1.6e-11)
    


```python
## ODE Example

from scipy.integrate import odeint
import numpy as N

def f(y,t):
    """This returns the RHS of the ODE to integrate, i.e. dy/dt = f(y,t)"""
    return(-2 * y * t)

y0 = 1    # initial value
a = 0     # integration limits for t
b = 2

t = N.arange(a, b, 0.01)  # values of t for which we require the solution y(t)

y = odeint(f, y0, t)  # actual computation of y(t)

import pylab     # Plotting of results

%matplotlib inline
pylab.plot(t, y)
pylab.xlabel('t'); pylab.ylabel('y(t)')
pylab.show()
```


![png](ipyim/Fangohr_Python_Intro_files/Fangohr_Python_Intro_52_0.png)



```python
## FFT exmaple
# Create a superposition of 50 and 70 Hz and plot the fft.

import scipy
import matplotlib.pyplot as plt
%matplotlib inline
pi = scipy.pi

signal_length = 0.5 # [seconds]
sample_rate = 500   # sampling rate [Hz]
dt = 1./sample_rate # delta t [s]

df = 1/signal_length    # frequency between points in the freq. domain [Hz]

t = scipy.arange(0, signal_length, dt) # the time vector
n_t = len(t)                           # length of the time vector

# create signal
y = scipy.sin(2*pi*50*t) + scipy.sin(2*pi*70*t + pi/4)

# compute the fourier transport
f = scipy.fft(y)

# work out meaningful frequencies in fourier transform
freqs = df*scipy.arange(0,(n_t-1)/2.,dtype='d')    #d = double precision float
n_freq = len(freqs)

# plot input data y against time
plt.subplot(2,1,1)
plt.plot(t, y, label='input data')
plt.xlabel('time [s]')
plt.ylabel('signal')

# plot frequency spectrum
plt.subplot(2,1,2)
plt.plot(freqs, abs(f[0:n_freq]), label='abs(fourier transform)')
plt.xlabel('frequency [Hz]')
plt.ylabel('abs(DFT(signal))')

# save plot to disk
plt.savefig('fft1.pdf')
plt.show()
```


![png](ipyim/Fangohr_Python_Intro_files/Fangohr_Python_Intro_53_0.png)



```python
len(y)
```




    250



## Chapter 17, Where to go from here?

* A list of additional skills for computational science work.


```python

```


    

    NameErrorTraceback (most recent call last)

    <ipython-input-5-aba79f90e137> in <module>()
    ----> 1 help(nbconvert)
    

    NameError: name 'nbconvert' is not defined



```python

```
