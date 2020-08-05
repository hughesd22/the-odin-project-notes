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