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

That first line, `def greeting():`, is called the function signature. The function signature defines the basic elements of the function including the name of the function (identifier), `greeting`. After the function identifier, you need to tell it what parameters the function expects. We'll be covering parameters in an upcoming lesson, so don't worry too much about that for now. After the  parameters, you need to tell it that what follows is the function's code block, and you do this by using a colon character `:`.

So to recap, a function definition in Python has 5 parts, with the first 4 used as the function's signature:

1. The `def` keyword
2. The function's name, also known as it's identifier
3. The function's parameters (more on this in upcoming lessons)
4. The colon character `:` that tells it to start the function's code block
5. The function's code block (the code that will execute when your function is called)

What are code blocks? Once you've provided your function's signature, Python will use indentation (also known as whitespace) to figure out which of the following lines of code you want to be part of the function. This concept of what makes up a function is called a code block. Various other mechanisms in Python rely on code blocks, so you'll see this pattern again later in this course.

How does it use indentation (whitespace) to identify my function's code block? After your function signature's `:` character, it will look for all lines with a deeper indentation depth than your function's signature definition, and deem those lines to be part of your function. The first subsequent line of code which is at the same or less indentation than your function's signature definition, will be deemed as the end of the function's block.


You must terminate every opening `def` of a method with a corresponding `end` in order to close the method body. If you don't correctly `end` a method, your program will have unexpected results or break entirely because of a syntax error. A good practice is to define the method and then immediately close it before programming anything into the method.

```ruby
def greeting
  # Leave a line break for the method body
end # Immediately close the method.
```

Here we set up the method's structure first, ensuring a proper termination before adding any other complexity. It's also a great practice to indent methods correctly. The body of a method should be indented two (2) spaces, placing it visually within the method. When you `end` the method, go back to the same indentation of the `def`, aligning the opening and closing of the method visually.

Then you can easily define the body of the method and never worry about forgetting to `end` the method.

```ruby
def greeting
  puts "Hello World" # Now code the body of the method.
end
```

### Invoking a Method

Once you define a method, you can execute the method whenever you want by using the method name in your code.

```ruby
def greeting
  puts "Hello World"
end

greeting # Executing the method by name
#> "Hello World"

greeting # Executing the method again
#> "Hello World"
```

Try it out. Make a new file called `greeting.rb` (you can use: `touch greeting.rb` from your terminal). Put the following code in it:

File: `greeting.rb`

```ruby
def greeting
  puts "Hello World"
end
```

Save your file and run it with `ruby greeting.rb`. You'll see:

```bash
$ ruby greeting.rb
$
```

You'll notice that when you run your program, nothing happens. Your program successfully defined the method but it never executed it. Just because you built a machine doesn't mean that you turned it on. Update your `greeting.rb` to entirely read:

File: `greeting.rb`

```ruby
def greeting
  puts "Hello World"
end

greeting
```

Save your file and run it with `ruby greeting.rb`. You'll see:

```bash
$ ruby greeting.rb
Hello World
$
```

Now your program actually executed the program. Update the code again to entirely read:

File: `greeting.rb`

```ruby
def greeting
  puts "Hello World"
end

greeting
greeting
greeting
greeting
greeting
```

Save your file and run it with `ruby greeting.rb`. You'll see:

```bash
$ ruby greeting.rb
Hello World
Hello World
Hello World
Hello World
Hello World
$
```

The bareword `greeting` will execute the body of the defined method.

> Note: Programmers love conventions, or agreed upon rules that help them talk to each other about code. A common convention for Ruby methods is to preface them with a #, and in subsequent lessons, you might see methods written with a `#` in front of the method name. This is so that other rubyists can instantly recognize it as a method, as opposed to a variable or a bareword or a class. For example, if a method is named 'greeting', rubyists will often refer to it as '#greeting'. But remember that when you write it in your code, it should be `greeting` and not `#greeting`.

<a href='https://learn.co/lessons/ruby-methods-readme' data-visibility='hidden'>View this lesson on Learn.co</a>
