# Functions in Python

##Overview

In this lesson you'll learn one of the most important concepts in the Python language, or any other programming language for that matter, so pay attention!
This lesson shows you how to create and execute functions in Python.

## Objectives

1. Learn how to use functions to create reusable code that can be called multiple times
2. See how functions are used to encapsulate a piece of code's logic and make your code expressive
2. Learn how to define functions with the `def` keyword
3. Learn how to call a function

### Why Use Functions

When you want to store data in a Python program so that you can refer to it again, you use variables; when you want to store behavior in a Python program so that you can execute it again, you use functions. Variables are like nouns, functions are like verbs.

For example, imagine needing to say "Hello World!" ten times. You might do something like this:

```python
phrase = "Hello World!"
print phrase
print phrase
print phrase
print phrase
print phrase
print phrase
print phrase
print phrase
print phrase
print phrase
```

That does work, but it's very repetitive. You made use of a variable to encapsulate the data you wanted to print and then the next ten lines print the phrase.

Now imagine later in your program you want to say "Hello World!" ten times again. The program would look something like this:

```python
phrase = "Hello World!"
print phrase
print phrase
print phrase
print phrase
print phrase
print phrase
print phrase
print phrase
print phrase
print phrase

# ... The rest of the program

print phrase
print phrase
print phrase
print phrase
print phrase
print phrase
print phrase
print phrase
print phrase
print phrase
```

Using this approach, we have to repeat the code for printing the value of `phrase` ten times. Remember: variables store data, functions store behavior. Instead of repeating `print phrase` ten times, we should build a function for it. Think of this function as a little mini program that you can execute as many times as you want, but by calling it with code.

The function looks like this:

```python
def say_hello_world_ten_times():
  phrase = "Hello World!"
  print phrase
  print phrase
  print phrase
  print phrase
  print phrase
  print phrase
  print phrase
  print phrase
  print phrase
  print phrase
```
Now we can add code to 'call' the function. We do this by using the function name followed by two parentheses `say_hello_world_ten_times()`. This will 'invoke' the function, which means that  code within the function will execute. Now that we know about functions, let's see if we can't do something better with the script above that says hello 10 times, then does something else before saying hello 10 times yet again.

```python
def say_hello_world_ten_times():
  phrase = "Hello World!"
  print phrase
  print phrase
  print phrase
  print phrase
  print phrase
  print phrase
  print phrase
  print phrase
  print phrase
  print phrase

say_hello_world_ten_times()

# ... The rest of the program

say_hello_world_ten_times()
```

That's way cleaner, don't you think? We define the abstraction, the mini program, `say_hello_world_ten_times` once, but can "call" or "invoke" it (make it run) as many times as we want. Let's look at functions in a bit more detail.

### Defining a Function

To define a function in Python, you need to use the `def` keyword. A function's name can begin with any alphabetical letter. Most Python programmers use only lowercase letters for their functions. Here's a quick example:

```python
def greeting(): # Method Signature
  print "Hello World" # Method Body
```

That first line, `def greeting():`, is called the function signature. The function signature defines the basic elements of the function including the name of the function (identifier), `greeting`. After the function identifier, you need to tell it what parameters the function expects `()`. We'll be covering parameters in an upcoming lesson, so don't worry too much about that for now. After the parameters, you need to tell it that what follows is the function's code block, and you do this by using a colon character `:`.

So to recap, a function definition in Python has 5 parts, with the first 4 making up the function's signature:

1. The `def` keyword
2. The function's name, also known as it's identifier
3. The function's parameters `()` (more on this in upcoming lessons)
4. The colon character `:` that tells it to start the function's code block
5. The function's code block (the code that will execute when your function is called)

What are code blocks? Once you've provided your function's signature, Python will use indentation (also known as whitespace) to figure out which of the following lines of code you want to be part of the function. This concept of what makes up a function is called a code block. Various other mechanisms in Python rely on code blocks, so you'll see a similar pattern repeated throughout in this course.

How does Python use indentation (whitespace) to identify my function's code block? After your function signature's `:` character, it will look for all lines with a deeper indentation depth than your function's signature definition, and deem those lines to be part of your function. The first subsequent line of code which it finds with same or less indentation than your function's signature definition, is deemed as the end of the function's block.

You might feel that the concept of *significant whitespace* seems a bit quirky. But it's also this exact same concept which lends Python it's expressiveness as a language, it makes it much easier to read and understand.


Let's look at an example again:

```python
def greeting(): # this is the function's signature
    print 'hello' # included in the function's block
    print 'bye'   # included in the function's block

print 'hi there' # not included in the function's block
```

Because both `print 'hello'`, and `print 'bye'` are nested on a deeper level than the function signature, both lines are deemed as part of the function definition. Because `print 'hi there'` is on the same level as the function signature, it's deemed as a sibling code block, and therefore not part of the function.


There's a gotcha here! The indentation also needs to be consistent. This means that the first line in the block can't be 4 spaces indented from the start of the signature, with the second line indented 3 spaces from the start of the signature. The first line of code that you provide after the function signature sets the shallowest indentation allowed for the block.

Here's an example of using illegal indentation for a function definition. Because the `print 'bye'` line is not on the same level of indentation as the function signature, nor the same level as the first line, but shallower, this results in an error.

```python
def greeting(): # this is the function's signature
    print 'hello' # included in the function's block
  print 'bye'   # causes a syntax error
```

Don't worry if this sounds awfully technical and difficult, you'll get used to it very quickly.
It's a few simple rules to be aware of, and we've handled most of the tricky syntax already.


### Invoking a Function

Once you define a function, you can execute the function whenever you want by using the function name in your code, followed by parameters.

```python
def greeting():
    print 'hello'



greeting() # Executing the function
#> "hello"

greeting() # Executing the function again
#> "hello"
```

Try it out. Make a new file called `greeting.py` (you can use: `touch greeting.py` from your terminal). Put the following code in it:

File: `greeting.py`

```python
def greeting():
  print "hello"
```

Save your file and run it with `python greeting.py`. You'll see:

```bash
$ python greeting.py
$
```

You'll notice that when you run your program, nothing happens. Your program successfully defined the function but it never executed it.
Just because you built a function, it doesn't execute without being 'called'. Update your `greeting.py` to read:

File: `greeting.py`

```python
def greeting():
  print "hello"

greeting()
```

Save your file and run it with `python greeting.py`. You'll see:

```bash
$ python greeting.py
hello
$
```

Now your program actually executed the program. Update the code again to read:

File: `greeting.py`

```python
def greeting():
  print "hello"

greeting()
greeting()
greeting()
```

Save your file and run it with `python greeting.py`. You'll see:

```bash
$ python greeting.py
Hello World
Hello World
Hello World
$
```

Every time you add a call to a function, in this case `greeting`, it'll execute the body of the defined function.

<a href='https://learn.co/lessons/python-methods-readme' data-visibility='hidden'>View this lesson on Learn.co</a>
