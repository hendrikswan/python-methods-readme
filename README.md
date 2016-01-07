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

That does work, but it's very repetitive. You made use of a variable to encapsulate the data you wanted to print and then the next ten lines literally print the phrase.

Now imagine later in your program you again want to say "Hello World!" ten times. The entire program would look something like this:

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

We have to repeat the code for printing the value of `phrase` ten times. Remember, variables store data, functions store behavior. Instead of repeating `print phrase` ten times, we should build a function for it. Think of this function as a little mini program that you can execute as many times as you want, but by calling it with code.

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
Now, when we add code to call it by using it's name followed by two parentheses `say_hello_world_ten_times()` in our program, it will invoke the function, running the code within the function. Now that we know about functions, let's revisit the script above that says hello 10 times, then does something else before saying hello 10 times yet again.

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

That's way cleaner. We define the abstraction, or the mini program, `say_hello_world_ten_times` once, but can "call" or "invoke" it (make it run) as many times as we want. Let's look at functions in a bit more detail.

### Defining a Function

You can define a function in Python with the `def` keyword. A method's name can begin with any lowercase letter. Here's a quick example:

```python
def greeting(): # Method Signature
  print "Hello World" # Method Body
```

That first line, `def greeting`, is called the method signature, it defines the basic properties of the method including the name of the method, `greeting`.

Once you open a method definition with the `def` keyword, all subsequent lines in your program are considered the method's body, the actual procedure or code that your method will run every time it's called.

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
