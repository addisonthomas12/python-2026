# python-2026
portfolio for python

### multiple files
```python
import glob
```

```python
print(glob.glob('inflammation*.csv'))
```
    ['inflammation-10.csv', 'inflammation-09.csv', 'inflammation-11.csv', 'inflammation-06.csv', 'inflammation-05.csv', 'inflammation-08.csv', 'inflammation-01.csv', 'inflammation-07.csv', 'inflammation-04.csv', 'inflammation-03.csv', 'inflammation-02.csv', 'inflammation-12.csv']




```python
import glob
import numpy
import matplotlib.pyplot

filenames = sorted(glob.glob('inflammation*.csv'))
filenames = filenames[0:3]
                      
for filename in filenames:
    print(filename)
                      
    data = numpy.load(fname = filename, dilimiter = ',')
                        
    fig = matplotlib.pyplot.figure(figsize = (10.0, 3.0))
                      
    axes1 = fig.add_subplot(1,3,1)
    axes2 = fig.add_subplot(1,3,2)
    axes3 = fig.add_subplot(1,3,3)
                      
    axes1.set_ylabel('average')
    axes1.plot(numpy.mean(data, axis =0))
                      
    axes2.set_ylabel('max')
    axes2.plot(numpy.amax(data, axis =0))
                      
    axes3.set_ylabel('min')
    axes3.plot(numpy.amin(data, axis =0))
                      
    fig.tight_layout()
    matplotlib.pyplot.show()
            
``

## jupytor notes
```python
import glob
import numpy
import matplotlib.pyplot

filenames = sorted(glob.glob('inflammation*.csv'))
filenames = filenames[0:3]
                      
for filename in filenames:
    print(filename)
                      
    data = numpy.load(fname = filename, dilimiter = ',')
                        
    fig = matplotlib.pyplot.figure(figsize = (10.0, 3.0))
                      
    axes1 = fig.add_subplot(1,3,1)
    axes2 = fig.add_subplot(1,3,2)
    axes3 = fig.add_subplot(1,3,3)
                      
    axes1.set_ylabel('average')
    axes1.plot(numpy.mean(data, axis =0))
                      
    axes2.set_ylabel('max')
    axes2.plot(numpy.amax(data, axis =0))
                      
    axes3.set_ylabel('min')
    axes3.plot(numpy.amin(data, axis =0))
                      
    fig.tight_layout()
    matplotlib.pyplot.show()
            



### functions 1
```python
fahrenheit_val = 99
celsius_val = ((fahrenheit_val - 32) *(5/9))
             
print(celsius_val)
```
    37.22222222222222




```python
fahrenheit_val2 = 43
celsius_val2 = ((fahrenheit_val2 -32) * (5/9))

print(celsius_val2)
```
    6.111111111111112




```python
def explicit_fahr_to_celsius(temp):
    # Assign the converted value to a variable
    converted = ((temp - 32) * (5/9))
    # Return the values of the new variables
    return converted
```

```python
def fahr_to_celsius(temp):
    # Return converted values more effeciently using the return function without creating 
    # a new variable. This code does the same thing as the previous function but it is more
    # explicit in explaining how the return command works
    return ((temp - 32) * (5/9))
```

```python
fahr_to_celsius(32)
```


    0.0






```python
explicit_fahr_to_celsius(32)
```


    0.0






```python
print('Freezing point of water:' , fahr_to_celsius(32), 'C')
print('Boiling point of water:' , fahr_to_celsius(212), 'C')
```
    Freezing point of water: 0.0 C
    Boiling point of water: 100.0 C




```python
def celsius_to_kelvin(temp_c):
    return temp_c + 273.15
print('freezing point of water in Kelvin:' , celsius_to_kelvin(0.))
```
    freezing point of water in Kelvin: 273.15




```python
def fahr_to_kelvin(temp_f):
    temp_c = fahr_to_celsius(temp_f)
    temp_k = celsius_to_kelvin(temp_c)
    return temp_k
print('boiling point of water in kelvin:' , fahr_to_kelvin(212.0))
```
    boiling point of water in kelvin: 373.15




```python
print('Again, temperature in kelvin was:' , temp_k)
```


    <ipython-input-17-53334891ec22> in <module>
    ----> 1 print('Again, temperature in kelvin was:' , temp_k)
    

    NameError: name 'temp_k' is not defined




```python
temp_kelving = fahr_to_kelvin(212.0)
print('Temperatire in kelvin was:' , temp_kelving)
```
    Temperatire in kelvin was: 373.15




```python
temp_kelvin
```



    <ipython-input-19-1684e2e47645> in <module>
    ----> 1 temp_kelvin
    

    NameError: name 'temp_kelvin' is not defined




```python
def print_temperatures():
    print('Temperature in fahrenheot was' , temp_fahr
    print('Temperature in kelvin was:' , temp_kelvin)
          
temp_fahr = 212.0

```



### Functions 2

import numpy
import matplotlib
import mtplotlib.pylot
import glob
  
```


          1 import numpy
          2 import matplotlib
    ----> 3 import mtplotlib.pylot
          4 import glob
          5 



```python
'freezing point of water in kelvin'
def visualize(filename):
    
    data = numpy.loadtxt(fname = filename, delimter = ',')
    
    fig = matplotlib.pyplot.figure(figsize=(10.0, 3.0))
    
    axes1 = fig.add_subplot(1, 3, 1)
    axes2 = fig.add_subplot(1, 3, 2)
    axes3 = fig.add_subplot(1, 3, 3)
    
    axes1.set_ylabel('average')
    axes1.plot(numpy.mean(data, axis = 0))
    
    axes2.set_ylabel('max')
    axes2.plot(numpy.amax(data, axis = 0))
    
    axes3.set_ylabel('min')
    axes3.plot(numpy.amin(data, axis = 0))
    
    fig.tight_layout()
    matplotlib.pyplot.show()
```

```python
def detect_problems(filename):
    
    data = numpy.loadtxt(fname = filename, delimeter = ',')
    
    if numpy.amax(data, axis = 0)[0] == 0 and numpy.amax(data, axis =0)[20] == 20:
        print("Supspicious looking maximal")
    elif numpy.sum(numpy.amin(data, axis=0)) == 0:
        print('Minima add up to zero!')
    else:
        print('Seems ok!')
```

```python
filenames = sorted(glob.glob('inflammation*.csv')) 

for filename in filenames[:3]:
    print(filename)
    visualize(filename)
    detect_problems(filename)
```
    inflammation-01.csv



          3 for filename in filenames[:3]:
          4     print(filename)
    ----> 5     visualize(filename)
          6     detect_problems(filename)


    <ipython-input-9-39168a26873f> in visualize(filename)
          2 def visualize(filename):
          3 
    ----> 4     data = numpy.loadtxt(fname = filename, delimter = ',')
          5 
          6     fig = matplotlib.pyplot.figure(figsize=(10.0, 3.0))


    TypeError: loadtxt() got an unexpected keyword argument 'delimter'




```python


### Functions 3

```python
def offset_mean(data, target_mean_value):
    return (data - numpy.mean(data)) + target_mean_value
```

```python
z = numpy.zeros((2,2))
print(offset_mean(z, 3))
```

    ---------------------------------------------------------------------------

    NameError                                 Traceback (most recent call last)

    <ipython-input-3-d85844a15494> in <module>
    ----> 1 z = numpy.zeros((2,2))
          2 print(offset_mean(z, 3))


    NameError: name 'numpy' is not defined




```python
data = numpy.loadtxt(fname = 'inflammation-0.1.csv' , delimeter = ',')

print(offset_mean(data, 0))
```

    ---------------------------------------------------------------------------

    NameError                                 Traceback (most recent call last)

    <ipython-input-6-bb5d076a4902> in <module>
    ----> 1 data = numpy.loadtxt(fname = 'inflammation-0.1.csv' , delimeter = ',')
          2 
          3 print(offset_mean(data, 0))


    NameError: name 'numpy' is not defined




```python
print('std dev before and after:' , numpy.std(data) , numpy.std(offset_data))
```

    ---------------------------------------------------------------------------

    NameError                                 Traceback (most recent call last)

    <ipython-input-7-7b0067eb16ce> in <module>
    ----> 1 print('std dev before and after:' , numpy.std(data) , numpy.std(offset_data))
    

    NameError: name 'numpy' is not defined




```python
print('difference in standard deviation before and after:' ,
     numpy.std(data) - numpy.std(offset_data))
```




```python
# offset_mean(data, target_mean_value):
# return a new array containing the original data with its mean offset to match
# This data should be imputed as a measurements in columns and samples in rows

def offset_mean(data, target_mean_value): 
    return (data - numpy.mean(data)) + target_mean_value
```

```python
def offset_mean(data, target_mean_value):
    """Return a new array containing the original datra with its mean offset to match the desired value"""
    return(data - numpy.mean(data)) + target_mean_value
```

```python
help(offset_mean)
```
    Help on function offset_mean in module __main__:
    
    offset_mean(data, target_mean_value)
        Return a new array containing the original datra with its mean offset to match the desired value
    





```python
def offset_mean(data, target_mean_value):
    """Return a new array containing the original data
    with its mean and offset to match its desired value.
    
    Examples
    ----------
    
    >>> Offset_mean[1, 2, 3], 0
    array([-1., 0., 1
    """
    
    return (data - numpy.mean(data)
```



### Functions 4
```python
numpy.loadtxt('inflammation-01.csv' , delimter = ',')
`
    ----> 1 numpy.loadtxt('inflammation-01.csv' , delimter = ',')
    

    NameError: name 'numpy' is not defined




```python
def offset_mean(data, target_mean_value = 0.0)
    """Return a new array containing the original data
    with its mean offset to match the desired value.
    
    Examples
    --------
    
    >>> Offset_mean[1,2,3] , 0)
    array([-1., 0., 1.,])
    """
    return (data - numpy.mean(data)) + target_mean_value1
```

      File "<ipython-input-2-db707dfe89bc>", line 1
        def offset_mean(data, target_mean_value = 0.0)
                                                      ^
    SyntaxError: invalid syntax






```python
print(offset_mean(test_data))
```



```python
print('only setting value of c')
display(c = 77)
```
    only setting value of c




```python
help.(numpy.loadtxt)
```

      File "<ipython-input-5-f56cfae289ae>", line 1
        help.(numpy.loadtxt)
             ^
    SyntaxError: invalid syntax






```python




```python

```
### making choices
```python
num = 37
if num > 100:
    print('greater')
else:
    print('not greater')
print('done')
```
    not greater
    done

```python
num = 53
print('before conditinal...')
if num > 100:
   print(num, 'is greater than 100')
print('...after conditional')
```
    before conditinal...
    ...after conditional



### storing values
    ```python
odds = [1, 3, 5, 7]
print('odds are:' , odds)
```
    odds are: [1, 3, 5, 7]




```python
print('first element:' , odds [0])
print('last element' , odds[3])
print('"-1" element' , odds[-1])
```
    first element: 1
    last element 7
    "-1" element 7




### using loops
```python
names = ['Curie' , 'Darwing' , 'Turing'] # Typon in Darwin's name

print('names is originally:' , names)

names[1] = 'Darwin' # Correct the name

print('final value of names:' , names)
```
    names is originally: ['Curie', 'Darwing', 'Turing']
    final value of names: ['Curie', 'Darwin', 'Turing']




```python
#name = 'Darwin'
#name[0] = 'd'
```

```python
odds.append(11)
print()
```


```python
odds = [1, 3, 5, 7]
```

```python
print(odds[0])
print(odds[1])
print(odds[2])
print(odds[3])
```
    1
    3
    5
    7




```python
odds = [1, 3, 5]
print(odds[0])
print(odds[1])
print(odds[2])
print(odds[3])
```
    1
    3
    5



    <ipython-input-3-b48c9fadc7bf> in <module>
          3 print(odds[1])
          4 print(odds[2])
    ----> 5 print(odds[3])
    

    IndexError: list index out of range




```python
odds = [1, 3, 5, 7, 9, 11, 13, 15, 17, 19]

for num in odds:
    print(num)
```
    1
    3
    5
    7
    9
    11
    13
    15
    17
    19




```python
length = 0
names = ['Curie' , 'Darwin' , 'Turing']
for value in names:
    length = length + 1
print('There are' , length, 'names in the list.')
```
    There are 3 names in the list.




```python
name = "Rosalind"
for name in ['Curie' , 'Darwin' , 'Turing']:
    print(name)
print('after the loop, name is' , name)
```
    Curie
    Darwin
    Turing
    after the loop, name is Turing




```python
print(len([0,1,2,3]))
```
    4




```python
name = ['Curie' , 'Darwin' , 'Turing']

print(len(name))
```
    3




```python

```
### translation
```python
# Prompt the user to enter the input RNA file name

input_file_name = input("Enter then name of the input RNA file:")
```
    Enter then name of the input RNA file: sequence.txt




```python
# Open the input RNA file and read the RNA sequence

with open(input_file_name, "r") as input_file:
     rna_sequence = input_file.read().strip()
```

```python
# Define the codon table

codon table = ("UUU")
```

### transcription
```python
# prompt the user to enter the input fasta file name

input_file_name = input('Enter the name of the input fasta file: ')
```
    Enter the name of the input fasta file:  sequence.txt




```python
# Open the input fasta file and read the DNA sequence

with open(input_file_name, "r") as input_file:
    dna_sequence = ""
    for line in input_file:
        if line.startswith(">"):
            continue
        dna_sequence += line.strip()
            
            
```

```python
# Transcribe the DNA to RNA
rna_sequence = ""
for nucleotide in dna_sequence:
    if nucleotide == "T":
        rna_sequence += "U"
    else:
        rna_sequence += nucleotide
```

```python
# Prompt the user to enter the output file name

output_file_name = input('Enter the name of the output file: ')
```

```python
# Save the RNA sequence to a text file

with open(output_file_name, "w") as output_file:
    output_file.write(rna_sequence)
    print("The RNA sequence has been saved to {output_file_name}")
```

```python
print(rna_sequence)
```

### defensive programming
```python
numbers = [1.5, 2.3, 0.7, 0.001, 4.4]
total = 0.0
for num in numbers:
    assert num > 0.0, 'Data should only contain positive valuse'
    total += num
print('total is:' , total)
```
    total is: 8.901



### analyzing 3
```python
def normalizing_rectangle(rect):
    """Normalizes a rectangle so tha tit is at the origin and 1.0 units long on its longest axis.
    input should be of the format (x0, y0, x1, y1).
    (x0, y0) and (x1, y1) define the lower left and upper right corners of the rectangle respectively."""
    assert len(rect) ==4, 'Rectangles must contain 4 coordinates'
    x0, y0, x1, y1 = rect
    assert x0 < x1, 'Invalid X coordinates'
    assert y0 < y1, 'Invalid Y coordinates'
    
    dx = x1 - x0
    dy = y1 - y0
    if dx > dy:
        scaled = dx/dy
        upper_x, upper_y = 1.0, scaled
    else:
        scaled = dx/dy
        upper_x, upper_y = scaled, 1.0
        
    assert 0 < upper_x <= 1.0, 'Calculated upper x coordinate invalid'
    assert 0 < upper_y <= 1.0, 'Calculated upper y coordinate invalid'
    
    return (0, 0, upper_x, upper_y)
```

```python
print(normalize_rectangle( (0.0, 1.0, 2.0) ))
```

    ---

    <ipython-input-10-f9d109085db1> in <module>
    ----> 1 print(normalize_rectangle( (0.0, 1.0, 2.0) ))
    

    NameError: name 'normalize_rectangle' is not defined




```python
print(normalize_rectangle( (0.0, 0.0, 1.0, 5.0)))
```


    <ipython-input-11-4757964e082c> in <module>
    ----> 1 print(normalize_rectangle( (0.0, 0.0, 1.0, 5.0)))
    

    NameError: name 'normalize_rectangle' is not defined




```python

```

```python
import numpy
data = numpy.loadtxt(fname= 'inflammation-0.1.csv', delimiter = ',')
```

    ---------------------------------------------------------------------------

    OSError                                   Traceback (most recent call last)

    <ipython-input-3-cec59f87bbe8> in <module>
          1 import numpy
    ----> 2 data = numpy.loadtxt(fname= 'inflammation-0.1.csv', delimiter = ',')
    

    ~/anaconda3/lib/python3.7/site-packages/numpy/lib/npyio.py in loadtxt(fname, dtype, comments, delimiter, converters, skiprows, usecols, unpack, ndmin, encoding, max_rows)
        966             fname = os_fspath(fname)
        967         if _is_string_like(fname):
    --> 968             fh = np.lib._datasource.open(fname, 'rt', encoding=encoding)
        969             fencoding = getattr(fh, 'encoding', 'latin1')
        970             fh = iter(fh)


    ~/anaconda3/lib/python3.7/site-packages/numpy/lib/_datasource.py in open(path, mode, destpath, encoding, newline)
        267 
        268     ds = DataSource(destpath)
    --> 269     return ds.open(path, mode, encoding=encoding, newline=newline)
        270 
        271 


    ~/anaconda3/lib/python3.7/site-packages/numpy/lib/_datasource.py in open(self, path, mode, encoding, newline)
        621                                       encoding=encoding, newline=newline)
        622         else:
    --> 623             raise IOError("%s not found." % path)
        624 
        625 


    OSError: inflammation-0.1.csv not found.




```python
import matplotlib.pyplot
image = matplotlib.pyplot.imshow(data)/
matplotlib.pyplot.show()
```

      File "<ipython-input-4-86b6d73d4fdd>", line 2
        image = matplotlib.pyplot.imshow(data)/
                                               ^
    SyntaxError: invalid syntax






```python

```

### analyzing 2
```python
# Let us a numpy function
print(numpy.mean(data))
```

    ---------------------------------------------------------------------------

    NameError                                 Traceback (most recent call last)

    <ipython-input-1-7c66b25740fe> in <module>
          1 # Let us a numpy function
    ----> 2 print(numpy.mean(data))
    

    NameError: name 'numpy' is not defined




```python
maxval, minvalm stdvat = numpy

print('maximum inflammation:' , maxval)
```

      File "<ipython-input-2-9b5da16cf40d>", line 1
        maxval, minvalm stdvat = numpy
                             ^
    SyntaxError: invalid syntax






```python
maxval = numpy.amax(data)
minval = numpy.amin(data)
stdval = nump.std(data)
```

    ---------------------------------------------------------------------------

    NameError                                 Traceback (most recent call last)

    <ipython-input-4-d950cf03eb8e> in <module>
    ----> 1 maxval = numpy.amax(data)
          2 minval = numpy.amin(data)
          3 stdval = nump.std(data)


    NameError: name 'numpy' is not defined




```python
# Sometimes we want to look at variation statistical values, such as maximum inflammation per patient,
# or average from day one
```

```python
print(numpy.mean(data, axis =1))
```

    ---------------------------------------------------------------------------

    NameError                                 Traceback (most recent call last)

    <ipython-input-6-5ab1c2d4e936> in <module>
    ----> 1 print(numpy.mean(data, axis =1))
    

    NameError: name 'numpy' is not defined




```python

```

### analyzing 1
```python
import numpy
```

```python
numpy.loadtxt(fname = 'inflammation-0.1.csv' , delimiter = ',')
```

    ---------------------------------------------------------------------------

    OSError                                   Traceback (most recent call last)

    <ipython-input-2-40264fcc8496> in <module>
    ----> 1 numpy.loadtxt(fname = 'inflammation-0.1.csv' , delimiter = ',')
    

    ~/anaconda3/lib/python3.7/site-packages/numpy/lib/npyio.py in loadtxt(fname, dtype, comments, delimiter, converters, skiprows, usecols, unpack, ndmin, encoding, max_rows)
        966             fname = os_fspath(fname)
        967         if _is_string_like(fname):
    --> 968             fh = np.lib._datasource.open(fname, 'rt', encoding=encoding)
        969             fencoding = getattr(fh, 'encoding', 'latin1')
        970             fh = iter(fh)


    ~/anaconda3/lib/python3.7/site-packages/numpy/lib/_datasource.py in open(path, mode, destpath, encoding, newline)
        267 
        268     ds = DataSource(destpath)
    --> 269     return ds.open(path, mode, encoding=encoding, newline=newline)
        270 
        271 


    ~/anaconda3/lib/python3.7/site-packages/numpy/lib/_datasource.py in open(self, path, mode, encoding, newline)
        621                                       encoding=encoding, newline=newline)
        622         else:
    --> 623             raise IOError("%s not found." % path)
        624 
        625 


    OSError: inflammation-0.1.csv not found.




```python
print(type(data))
```

    ---------------------------------------------------------------------------

    NameError                                 Traceback (most recent call last)

    <ipython-input-3-ea83332336b0> in <module>
    ----> 1 print(type(data))
    

    NameError: name 'data' is not defined




```python
print(data.shape)
```

    ---------------------------------------------------------------------------

    NameError                                 Traceback (most recent call last)

    <ipython-input-4-25a56bb3f532> in <module>
    ----> 1 print(data.shape)
    

    NameError: name 'data' is not defined




```python
print value in data: 0.0
```

      File "<ipython-input-5-203fc1b4726a>", line 1
        print value in data: 0.0
                  ^
    SyntaxError: Missing parentheses in call to 'print'. Did you mean print(value in data: 0.0)?






```python
print('middle value in data:' , data[29,19])
```

    ---------------------------------------------------------------------------

    NameError                                 Traceback (most recent call last)

    <ipython-input-6-74a0f03ad484> in <module>
    ----> 1 print('middle value in data:' , data[29,19])
    

    NameError: name 'data' is not defined




```python
print(data[5:10, 0:10])
```

    ---------------------------------------------------------------------------

    NameError                                 Traceback (most recent call last)

    <ipython-input-7-c6e5cb76298a> in <module>
    ----> 1 print(data[5:10, 0:10])
    

    NameError: name 'data' is not defined




```python
small = data[:3, 36:]
```

    ---------------------------------------------------------------------------

    NameError                                 Traceback (most recent call last)

    <ipython-input-8-ce939cdf3fa1> in <module>
    ----> 1 small = data[:3, 36:]
    

    NameError: name 'data' is not defined




```python
small ls:
    
```

      File "<ipython-input-9-73a678db3a48>", line 1
        small ls:
               ^
    SyntaxError: invalid syntax






```python
p
