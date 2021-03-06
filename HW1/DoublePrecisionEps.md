# Function Name: DoublePrecisionEps()

### Last Mod Date

September 10, 2017

### Author

Skyler Wiser

### Written For

Python 2.7.13

### Description

Calculates the machine epsilon for a double precision float.

### Inputs

* None

### Outputs

* Machine Epsilon

### Modules Used

* Numpy

### Code

```python
def DoublePrecisionEps():
    x_bar=np.float64(1.0)
    n=0
    while 1+x_bar/2.0>1:
        x_bar-=x_bar/2.0
        n+=1
    print 'Test: Binary Digits (Double):',n, 'Epsilon:', x_bar, bool(1+x_bar/2.0>1),bool(1+x_bar>1)
    return x_bar
```

### Code notes

The print statement first prints 'n', which is the number of binary digits or the number of times a number can be cut in half before it isn't recognizeable when added to 1.0. 'x_bar' is then printed, which is the epsilon itself. Two bools are then printed:

1. The first bool checks if 1.0 + (epsilon)/2.0 is recognized as greater than 1. This would show that cutting the machine epsilon is at least no further than the current x_bar.
2. The second bool checks if 1.0 + (epsilon) is recognized as greater than 1. If this is true and (1) is false, then the current x_bar is the correct machine epsilon.

### Examples
#### Prompt

```python
DoublePrecisionEps()
print '64',np.spacing(np.float64(1.0))
#validates using numpy's built in machine precision function
```

#### Output

```
Test: Binary Digits (Double): 52 Epsilon: 2.22044604925e-16 False True
64 2.22044604925e-16
```
