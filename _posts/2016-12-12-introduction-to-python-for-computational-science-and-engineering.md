---
layout: post
published: true
title: Introduction To Python For Computational Science And Engineering
category: notes
tags:[book,notes,python]
---


`Fangohr, Hans. Introduction to Python for Computational Science and Engineering, 2015.`

Fangohr's book is an excellent introduction to python.  Coming from a Matlab background, the structure is easy to follow and very useful. The only negative about this book is that it was written for Python 2 and I am working in 3.  This generally didn't pose any problems, mainly just remembering that in 3 `print()` requires brackets.  I've uploaded my notes [here](stembl.github.io/public/ipy/Fangohr_2015/Fangohr_Python_Intro.ipynb) and below are some of the more interesting parts.

## General Notes
* Use `help()` with a command for details
* Use `dir()` with a command for a list of available methods


## Chapter 2, A Powerful Calculator


```python
import math
```


```python
import cmath

cmath.sqrt(-1)
```




    1j




## Chapter 4, Introspection

* Magic names start and end with a double underscore
* `isinstance(<unit>, <type space>)` Returns true if the given object is of the given type.
* `help(<object>)`
* `help()` Starts aand interactive help utility
* Provide a docstring for user defined functions



## Chapter 5, Input and Output

* String specifiers, reprinted table below
* Pg 54-55 for a more elegant method of string formatting used in Python 3
* `fileobject.readlines()` method returns a list of strings
   



```python
## Copied from Fangohr 2015, page 52.

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

## Chapter 12, Symbolic Computation

* SymPy is the Python Symbolic library, [SymPy Homepage](http://sympy.org) for full and up-to-date documentation
* Very slow compared to floating point opperation
* isympy an exexutable wrapper around python, convenient for figuring out new features or experementing interactively
* Rational type, Rational(1,2) represents 1/2.
    * Rational class works exactly as opposed to the standard float.
* If Sympy returns the result in an unfamiliar form, subtract it with the expected form to determine if they are equivalent.
* Calculate definite integrals with a tuple containing the variable of interest, lower, and upper bounds.
* Results from dsolve are an Equality class, function needs to be evaluated to a number to be plotted.
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
## Solving Non Linear Equations

import sympy

x, y, z = sympy.symbols('x,y,z')
eq = x - x**2
print(sympy.solve(eq,x))
```

    [0, 1]
    

## Chapter 15, Numerical Python (numpy): arrays

* The data structure, `array`, allows efficient matrix and vector operation
* An array can only keep elements of the same type, as opposed to lists which can hold a mix.
* Convert a matrix back tp a list or tuple using, `list(s)` or `tuple(s)`.
* Computing eiganvectors and eiganvalues
* Numpy examples at [SciPy.org](http://www.scipy.org/Numpy_Example_List)




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
#pylab.savefig('polyfit.pdf')
pylab.show()
```

    z =  [ 0.08703704 -0.81349206  1.69312169 -0.03968254]
    p =           3          2
    0.08704 x - 0.8135 x + 1.693 x - 0.03968
    


![png](/public/ipy/Fangohr_2015/output_29_1.png)


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


![png](/public/ipy/Fangohr_2015/output_31_0.png)



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
#plt.savefig('pylabhistogram.pdf')
#then display
plt.show()

```


![png](/public/ipy/Fangohr_2015/output_32_0.png)


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


![png](/public/ipy/Fangohr_2015/output_35_0.png)



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
#plt.savefig('fft1.pdf')
plt.show()
```


![png](/public/ipy/Fangohr_2015/output_36_0.png)

