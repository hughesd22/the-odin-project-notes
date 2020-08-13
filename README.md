# Ruby
A collection of notes documenting important information about the Ruby programming language

## Basic Data Types
Ruby is strongly object-oriented. Even the most basic data types are objects.

### Some Basic Data Types
* numbers (integers and floats)
* strings
* symbols
* booleans (true, false, nil)

### Arithmetic Operators
Ruby has the typical math operators you'd expect.

* Addition ( + )
* Subtraction ( - )
* Multiplication ( * )
* Division ( / )
* Exponentiation ( ** )
* Modulus/Remainder ( % )

### Numbers
Two main types are **Integers** and **Floats**. When doing arithmetic operations with two integers, *the result will always be an integer*.

```ruby
17 / 5 #=> 3, not 3.4
```

If you want a more accurate answer, change one of the integers in the expression to a float.

```ruby
17 / 5.0 #=> 3.4
```

Optionally, an underscore can be used as a thousands separator for readability.

```ruby
1862928571 # huh...what number is that exactly?

# vs

1_862_928_571 # Ah!


# still evaluates the number as if the underscore was not there

1_000 #=> 1000

```

#### Number Type Conversion

Easy to convert between floats and ints.

* <num\>**.to_f**
* <num\>**.to_i**

```ruby
# int => float

13.to_f #=> 13.0

# float => int

13.0.to_i #=> 13
13.9.to_i #=> 13

```

*Note*: When converting float => int, no rounding occurs. Simply cuts off decimal places.

#### Some Useful Number Methods

* <num\>**.even?**
* <num\>**.odd?**

```ruby
# Check if even
1.even? #=> false
2.even? #=> true

# Check if odd
1.odd? #=> true
2.odd? #=> false
```

#### Docs
* [Integer](https://ruby-doc.org/core-2.5.0/Integer.html)
* [Float](https://ruby-doc.org/core-2.5.0/Float.html)

### Strings
Can be formed with either double ( " ) or single ( ' ) quotation marks.

Strings formed with single ( ' ) quotation marks are *string literals* (which don't allow string interpolation or escape characters).

#### Concatenation

```ruby
# plus operator

"Hello " + "World" #=> "Hello World"


# shovel operator

"Hello " << "World" #=> "Hello World"


# concat method

"Hello".concat(" ").concat("World") #=> "Hello World"
```

*Note*: The shovel operator ( ```<<``` ) and the concat method (<string\>```.concat```) alter the original string, rather than creating a new one (as ```+``` does). This makes them more efficient.

#### Substrings

```ruby
"hello"[0] #=> "h"

"hello"[0..1] #=> "he"

"hello"[0, 4] #=> "hell"

"hello"[-1] #=> "o"
```

#### Escape Characters
Allow you to type representations of whitespace characters and to include quotation marks as part of the string without ending it.

*Note*: Only works with double ( " ) quotation marks.

```ruby
" \\ " # backslash
" \b " # backspace
" \r " # carriage return
" \n " # newline
" \s " # space
" \t " # tab
" \" " # double quotation mark
" \' " # single quotation mark
```

#### Interpolation

Allows you to evaluate expressions within a string.

*Note*: Only works with double ( " ) quotation marks.

```ruby
name = "Robert"

puts "Hello, #{name}!" #=> "Hello, Robert!"

puts 'Hello, #{name}!' #=> "Hello, #{name}!"
```

#### Some Useful String Methods

* <string\>**.capitalize**
* <string\>**.include?**
* <string\>**.upcase**
* <string\>**.downcase**
* <string\>**.empty?**
* <string\>**.length**
* <string\>**.reverse**
* <string\>**.split**
* <string\>**.strip**

```ruby
# capitalize
"hello".capitalize #=> "Hello"

# include?
"hello".include?("lo") #=> true

"hello".include?("z") #=> false

# upcase
"hello".upcase #=> "HELLO"

# downcase
"Hello".downcase #=> "hello"

# empty?
"hello".empty? #=> false

"".empty? #=> true

# length
"hello".length #=> 5

# reverse
"hello".reverse #=> "olleh"

# split
"hello world".split #=> ["hello", "world"]

"hello".split("") #=> ["h", "e", "l", "l", "o"]

"hello world".split(" ") #=> ["hello", "world"]

# strip
"     hello, world   ".strip #=> "hello, world"
```

#### Converting other objects to string

* <object\>**.to_s**

```ruby
5.to_s #=> "5"

nil.to_s #=> ""

:symbol.to_s #=> "symbol"
```

#### Docs

* [String](https://ruby-doc.org/core-2.6/String.html)

### Symbols

Similar to strings, but whereas a string can be changed and has to be stored in memory every time it is used, even if an existing string with the same value already exists, symbols are stored in memory only once and then reused. This makes them faster in certain situations.

A common use case where a symbol is preferred over a string is the key in a hash.

#### Creating a Symbol
Simply put a colon in front of text.

```ruby
:a_symbol
```

#### Docs
* [Symbol](https://ruby-doc.org/core-2.5.0/Symbol.html)

### Booleans

* true
* false
* nil

Pretty self explanatory.

```true``` represents something that is true

```false``` represents something that is false

```nil``` represents "nothing"

*Note*: Everything in Ruby has a return value. If a piece of code doesn't return anything, it will return nil.

#### Docs
* [true](https://ruby-doc.com/core/TrueClass.html)
* [false](https://ruby-doc.com/core/FalseClass.html)
* [nil](https://ruby-doc.com/core/NilClass.html)

### Arrays

An ordered list of information. Can be made up of strings, integers, floats, booleans, or any other data type.

```ruby
arr = [1, 2, 3, 4, 5]

arr[0] #=> 1
arr[-2] #=> 4

colors = ["red", "orange", "green", "yellow", "purple"]

users = ["user1", "user2", "user3", "user4"]

bool_arr = [true, false, true, true, true, false]
```

#### Docs
* [Array](https://ruby-doc.org/core-2.7.0/Array.html)

### Hashes

A hash, also referred to as a *dictionary* or as an *associative array*, is a set of key-value pairs. Each key, usually represented by a symbol, is unique and points to a specific piece of data.

Data can be retrieved from the hash by referencing its corresponding key.

```ruby
animal_sounds = {:dog => "bark", :cat => "meow", :pig => "oink"}

animal_sounds[:dog] #=> "bark"

animal_sounds[:cat] #=> "meow"
```

## Variables

Are a named placeholder for data. Think of it like a box with a label on it.

```ruby
# Defining a variable
age = 26

puts age #=> 26

# Assigning the result of an expression to a var
age = 20 + 6

puts age #=> 26
```

*Note*: Variables are not *declared* (created without assigning a value) in Ruby. You must *define* (assign a value to) a variable when you create it.

```ruby
user_name = "Bob" #=> OK
```

```ruby
user_name #=> error
```

Variable names are reusable. You can assign a new value at any time, overriding the previous value.

```ruby
# define
age = 18

puts age #=> 18

# re-assign
age = 26

puts age #=> 26
```

### Assignment Operators

Shorthand way of performing an operation on the original value of a variable and then reassigning that value to the variable.

* +=
* -=
* *=
* /=

```ruby
age = 20
age += 6 #=> age = 26

acct_bal = 500
acct_bal -= 15 #=> acct_bal = 485

cash = 100
cash *= 2 #=> cash = 200

temp = 70
temp /= 10 #=> temp = 7
```

### Naming Variables
Ruby aims to be natural to read and easy to write. Variable names should mirror this. A variable name should, as best as it can, describe the value held by the variable.

Names should be lowercase and use snake_case when they contain multiple words.

```ruby
# NO
a = 19
string = "Bob"

# YES
age = 19
first_name = "Bob"
```

### Variables are References
The box analogy breaks down a little bit, because in practice variables point to data in memory. Altering a variable that points to the another variable will actually alter the value stored in memory, thus affecting both variables since they simply point to the value stored in memory.

```ruby
destination = "Tokyo"
current_location = destination

puts destination #=> "Tokyo"
puts current_location #=> "Tokyo"

current_location.upcase!

puts current_location #=> "TOKYO", as expected

puts destination #=> "TOKYO", this variable was changed too!
```

Looking at the object id's of the variables can help illustrate this point.

```ruby
a = "hi there"
b = a

puts a #=> "hi there"
puts b #=> "hi there"

puts a.object_id #=> 180
puts b.object_id #=> 180

a = "not here"

puts a #=> "not here"
puts b #=> "hi there"

puts a.object_id #=> 200
puts b.object_id #=> 180
```
---

```ruby
a = "hi there"
b = a

puts a #=> "hi there"
puts b #=> "hi there"

puts a.object_id #=> 180
puts b.object_id #=> 180

a << ", Bob"

puts a #=> "hi there, Bob"
puts b #=> "hi there, Bob"

puts a.object_id #=> 180
puts b.object_id #=> 180
```

It's not that variables are deeply linked to each other...

```ruby
a = 4
b = a

puts a #=> 4
puts b #=> 4

a = 7

puts a #=> 7
puts b #=> 4
```

...it's that when the underlying value that both variables point to is altered (not just reassignment of one of the variables, which creates a new object), both variables will be affected since they point to the same object in memory.

* [Visual Explanation](http://ruby.bastardsbook.com/chapters/variables/#visual-guide)

### Variable Scope

Variables in Ruby are scoped by block. A block is a piece of code following a method invocation, usually delimited by curly braces ```{}``` or ```do/end```.

*Note*: Inner scope can access variables defined in outer scope, but not vice versa.

```ruby
# outer scope
a = 5

1.times do
  # inner scope

  # can access the variable defined in outer scope and re-assign it
  a = 3
end

puts a #=> 3
```

```ruby
# outer scope
a = 5

1.times do
  # inner scope
  b = 3
end

puts a #=> 5
puts b #=> error, b not defined in outer scope since it was initialized in inner scope
```

### Variable Types

There are five types of variables in Ruby.

* Constants
  * Defined by capitalizing every letter in the variable name
* Global
  * Defined by starting the variable name with ```$```
* Class
  * Defined by starting the variable name with ```@@```
* Instance
  * Defined by starting the variable name with ```@```
* Local

```ruby
# Constants
A_CONSTANT = "A value that never changes, available through all scopes"


# Global
$var_name = "Also available through all scopes"

# global variables tend to lead to unexpected complications; best to avoid


# Class
@@class_var = 1

# accessible by instances of the class and by the class itself

# used when you need a variable that is related to the class, but each instance of the class does not need its own value for the variable


# Instance
@instance_var = 0

# accessible throughout the current instance of the parent class


# Local
local_var = "Hello World"

# most common and obeys all scope boundaries
```

## Input & Output

### Output

* ```puts```
  * outputs passed argument, appending a newline, and returns ```nil```
* ```p```
  * same as ```puts```, but outputs a more raw version of the object that was passed in as an argument
* ```print```
  * outputs passed argument only, no newline, and returns ```nil```

### Input

* ```gets```
  * stands for "get string"
  * prompts user for input and then returns that input, appending a newline
* ```chomp```
  * String class method commonly used to trim separators

#### Examples

```ruby
name = gets

## user input
Bob
##

# name = "Bob\n"
```

---

```ruby
name = gets.chomp

## user input
Bob
##

# name = "Bob"
```

## Conditional Logic

*Note*: The only false values in Ruby are ```nil``` and ```false```. Everything else evaluates to true, even ```0```, ```""```, and ```"false"```.

### ```if```

```ruby
if <statement_to_be_evaluated> == true
  puts "Hello, World!"
end
```

---

**single line variation**

```ruby
puts "Hello, World!" if <statement_to_be_evaluated> == true
```

```ruby
if x == 3 then puts "x is 3" end
```

### ```else``` & ```elsif```

```ruby
if 1 < 2
  puts "Something"
else
  puts "Something else"
end
```

---

```ruby
if 1 >= 2
  print "an option"
elsif num < max_num
  print "another one"
  # can have more than one elsif
else
  print "the final one"
end
```

### Comparison Operators

* ==
* !=
* \>
* <
* \>=
* <=
* <object\>**.eql?**(<object\>)
  * checks both the value type and the actual value
* <object\>**.equal?**(<object\>)
  * checks if both values are the exact same object in memory
* <object\> **<=>** <object\>
  * spaceship operator
  * returns ```-1``` if left is less than right
  * returns ```0``` if equal
  * returns ```1``` if left is greater than right
  * most commonly used in sorting functions

### Logical Operators

* &&
* ||
* !

*Note*: Expressions always evaluated from left to right. Using &&, if left expression returns false, right never checked. Using ||, if left expression returns true, right never checked.

### ```case```

```ruby
grade = "A"

class_result = case grade
  when "A" then "Exceeded"
  when "B" then "Pretty good"
  when "C" then "Average"
  when "D" then "Hey man, D's get degrees"
  else "Failed"
end
```

---

```ruby
grade = "F"

case grade
  when "A"
    puts "Genius!"
    acct_bal += 500
  when "D"
    puts "Try again. You'll get it next time!"
    stop_trying = false
  else
    puts "Better try a different field..."
    stop_trying = true
end
```

---

```ruby
grade_avg = 96
grade_letter = ""

case
  when grade_avg >=90
    grade_letter = "A"

  when grade_avg >= 80
    grade_letter = "B"

  when grade_avg >= 70
    grade_letter = "C"

  when grade_avg >= 60
    grade_letter = "D"

  else
    grade_letter = "F"
end
```

### ```unless```

Opposite of an ```if``` statement. Only processes code block if expression evaluates to false.

```ruby
age = 26

unless age < 21
  puts "Have a beer"
end
```

---

```ruby
height_ft = 6

unless height_ft < 4
  puts "Welcome aboard the coaster!"
end
```

---

```ruby
grade = 96

unless grade < 60
  puts "Hey, you passed!"
else
  puts "R.I.P."
end
```

---

```ruby
puts "x isn't 3" unless x == 3
```

### Ternary Operator

Is a single line if/else

```ruby
age = 26

response = age < 21 ? "You have your whole life ahead of you!" : "You're all grown up."

puts response #=> "You're all grown up."
```

## Loops

### While

Continues as long as a condition is true.

```ruby
i = 0

while i < 10 do
  puts "i: #{i}"
  i += 1
end
```

```ruby
while gets.chomp != "yes" do
  puts "Are you ready?"
end
```

### Until

Opposite of ```while``` loops. Continues as long as a condition is false.

```ruby
i = 0

until i > 10 do
  puts "i: #{i}"
  i += 1
end
```

```ruby
until gets.chomp = "yes" do
  puts "Ready?"
end
```

*Note*: Notice how much more readable it is to use an ```until``` loop here instead of a ```while``` loop. Instead of using negated logic (```while gets.chomp != "yes"```) the code is much cleaner and easier to parse (```until gets.chomp = "yes"```).

### For

Iterates through a collection of information, such as an array or range.

```ruby
for i in 0..5
  puts "i: #{i}"
end
```

*Note*: While the other loops mentioned here return ```nil```, the For loop returns the range it is iterating over.

### Times

Iterations a specified number of times. Actually a method of the ```Integer``` class.

```ruby
5.times do
  puts "Hello, World!"
end
```

```ruby
5.times do |i|
  puts "i: #{i}"
end
```

### Upto / Downto

Iterates from one number ```upto``` another or from one number ```downto``` another. Actually methods of the ```Integer``` class.

```ruby
# upto
5.upto(10) { |i| puts "i: #{i}" }


# downto
10.downto(5) { |i| puts "i: #{i}" }
```

### Do/While

Similar to while loop, but ensures that the code inside the loop is executed at least once.

```ruby
loop do
  puts "Do you want to do that again?"
  answer = gets.chomp

  # conditional will break out of loop once the correct answer is received
  if answer != "y"
    break
  end
end
```

### Reserved Loop Keywords

```next``` will jump from the line it is on to the next loop iteration, without executing the code beneath it for the current loop iteration

```break``` will exit the loop immediately, without executing any more code within the loop


### Iterators

Methods that loop over a given set of data and allow you to operate on each element in the collection.

Preferred over loops, where possible.

```ruby
dog_names = ["Astro", "Bella", "Kaine", "Jesse", "Lucky", "Pip", "Kronos", "Terra", "Shadow"]

# Iterator
dog_names.each {|dog_name| puts dog_name}

# prints each name in the array to the screen, each on its own line
```