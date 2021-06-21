 

Working with files will make your programs fast when analyzing masses of data. Exceptions are special objects that Python uses to manage errors that occur when a program is running. In this tutorial, we’ll learn working with files and handling some exception errors.

### Prerequisites

Have some basic knowledge of Python language.

### Reading from a file

Working with data in a text file, you need to read the file into memory first. To read a file, you must have a file with some data.

Let’s create a text file containing a list of years from 2020 to 2022 using an editor and save it in the same folder that stores our Python files as **years.txt**. The **years.txt** file should have:

```

2022

2021

2020

```

Below is a program that opens the above file, reads it and prints the data in the file:

```python

with open(‘years.txt’) as file_object:

    contents = file_object.read()

 print(contents)

```

The `open()` function takes one argument which is the name of the file to be opened. Python looks for the **years.txt** file in the folder where our Python file is stored. The `open()` function returns an object representing the file (years.txt) which is then stored in  variable file_object.

The keyword `with` closes the file when access to it is no longer need.

The `read()` method is used to read the whole data in the file and store it in contents.

When we run the above code, we get the output as:

```python

#OUTPUT

2022

2021

2020

```

### Working with a file’s contents

Now you have learnt how to read a file into memory, let’s try doing something with that data. Let’s create a single line holding all the digits in the **years.txt** file without white spaces in it.

```python

with open(‘years.txt’) as file_object:

    lines = file_object.readlines()

yrs_string = ‘’ # create a variable yrs_string to hold the digits of years

for line in lines: # create a loop that adds each line of digits to yrs_string

     yrs_string += line.rstrip() #.rstrip() removes the newline character from each line

print(yrs_string) # print this string

print(len(yrs_string)) # print how long the string is 

 # OUTPUT

 # 209020702089

 # 12

```

>**NOTE:**When reading from a text file, Python interprets all the text as a string. If you read a number from a file and you want to carry out arithmetic operations, convert it to float using the `float()` function or integer using the `int()` function.

### Writing to a file

Writing to a file is one of the easiest ways to save data. The output will still be even after we close the terminal having our program’s outputs.

 

When writing text to a file, we use the `open()` function with two arguments. First argument is the filename while the second argument is the mode in which you want to open the file. 

There are 4 modes in which you can open a file:

 1.Read mode (‘r’) 

 2.Write mode (‘w’) 

 3.Append mode (‘a’)

 4.read and write (‘r+’)

#### Writing to an empty file

If the file you are writing does not exist at all, the `open()` function auto-generates the file.

Example:

```python

 with open(‘student.txt’, ‘w’) as file_object:

      file_object.write(“My name is Felix.”)

```

The above code doesn’t print the output on the terminal, but when you open the **student.txt** file you will see one line:

```

My name is Felix.

```

>**NOTE:**When opening a file in ‘w’ mode and the file exists, Python will delete the file before returning the file object.

#### Appending to a file

To add data into a file, open the file in *append mode*. Any data you write will be placed at the end of the file.

Let’s add some lines in the **student.txt** file

```python

with open(‘student.txt’, ‘a’) as file_object: #’a’ argument to open the file for appending

      file_object.write(“I am 6 years old\n”)

      file_object.write(“I love playing games\n”)

```

The new **student.txt** file looks like this:

```

My name is Felix.

I am 6 years old

I love playing games

```

### Exceptions

Exceptions are unique objects that Python uses to control errors that occur when a program is running. Exceptions errors arise when correct syntactically Python programs produce an error. When these errors arise, Python creates an exception object. When we write codes that deal with the exception, our programs will continue running. If we don’t our programs will stop executing and show a trace-back, which is very hard for a user to understand.

Python uses the *try-except* block to control exceptions. A try-except block informs Python how to act when an exception emerges. Our programs will continue to execute even if things go wrong.

### Handling the ZeroDivisionError exception

Let’s run a program that divides a number by zero. We absolutely know it is impractical, but let’s see what Python will do.

```python

print(6/0)

```

When we run the above code Python gives the following trace-back:

```python

Traceback (most recent call last):

  File “C:\Users\ADMIN\PycharmProject\pythonProject\main.py”, line 1, in <module>

 print(6/0)

ZeroDivisionError: division by zero

```

Since Python cannot divide a number by zero, it reports an error in the trace-back, *ZeroDivisionError*, which is an exception object. This kind of object responds to a scenario where Python can’t do what we asked it to.

If you think of an error occurring use the *try-except* block to control the exception that may be raised.

To handle the ZeroDivisionError exception use a try-except block like this:

```python

try:

 print(6/0)

except ZeroDivisionError:

 print(“You can’t divide by zero!”) # You can’t divide by zero!

```

### Handling the FileNotFoundError exception

Errors will always arise when working with files that are missing. Python may fail to get file if you have written the wrong spelling of filename, or the file never exists. We handle this situation by applying the try-except block. For example, the program below tries to read a file that doesn’t exist on my computer.

```python

filename = ‘John.txt’

with open(filename) as f_obj:

 contents = f_obj.read()

 ```

Since Python can not read a file that does not exist, it raises an exception:

```python

Traceback (most recent call last):

  File “C:\Users\ADMIN\PycharmProject\pythonProject\main.py”, line 2, in <module>

 with open(filename) as f_obj:

FileNotFoundError: [Errno 2] No such file or directory: ‘john.txt’

```

Since Python can not find the file, we are opening it creates an exception that is the *FileNotFoundError* exception. In this example, the **open()** function creates the error. To solve this error, use the try block just before the line, which involves the **open()** function:

```python

filename = ‘John.txt’

try:

 with open(filename) as f_obj:

       contents = f_obj.read()

except FileNotFoundError:

 msg = “Sorry, the file “+ filename + “does not exist.”

 print(msg) # Sorry, the file John.txt does not exist.

```

### Conclusion

In this article, we have learnt how to:

 - Read from a file

 - Work with a File’s Contents

 - Write to a File

 - Handle the ZeroDivisionError Exception

 - Handle the FileNotFoundError Exception

