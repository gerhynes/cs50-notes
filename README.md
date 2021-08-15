# CS50 Notes

## 0 - Scratch

Computer science is not so much about programming as it is about problem solving.

### Representing Information

How do you represent the information being input into your problem solving - unary representation, base 10?

Computers use binary or base 2. These 0s and 1s are bits (binary digits).

Ultimately, a computer's input is electricity. By turning it on or off, you can represent information.

With three switches you could count from 0 to 7. (Computers start counting from 0).

Modern computers have millions of these switches (transistors).

Three bits can be permuted in 8 ways.

000 = 0
001 = 1
010 = 2
011 = 3
100 = 4
101 = 5
110 = 6
111 = 7

Early on, all computers could do was calculate. To represent letters, you could assign letters to numbers, like with ASCII (American Standard Code for Information Interchange).

01000001 or 65 = A

The first 64 codes represent control characters, symbols and punctuation.

01001000 01001001 00100001 = HI!

Computers now use 8 bits to represent each of these characters. Each pattern of 8 bits is a byte.

But ASCII is limited and US-centric. It has only 256 total possibilities.

Now, Unicode intends to support all human languages.

How is colour represented?

You can make every colour of the rainbow by mixing red, green and blue.

RGB represents quantities of red, green and blue using numbers from 0 to 255 for each of them.

Each pixel contains red, green and blue values stored in three bytes.

Video is just a stream of images where each pixel is being rapidly updated.

Music can similarly be represented numerically, with one number to represent a note, another the duration of that note.

File formats arise from groups of people agreeing on conventions to store information in patterns of 0s and 1s.

### Algorithms

Algorithms are step by step instructions for solving problems.

If you've every followed a recipe, you've executed an algorithm.

Computers will take you literally and so you need to be precise in your instructions.

Imagine you are looking for a name beginning with D in an old-school phone book.

To search page by page from the beginning is a correct but extremely slow algorithm.

With algorithms, efficiency matters as much as correctness.

You could search every second page but then you might miss the correct page.

If you opened the phone book to halfway, M, you now know the name isn't is the second half and you can discard that. You can then open to the middle of the remaining half and repeat. If you started with 1000 pages, it would only take 10 steps to get to the desired page.

The first algorithm could be graphed as a straight line. There is a one-to-one relationship between the size of the problem and the time to solve it. n

The second algorithm is twice as efficient but stil slow. n/2

With the third algorithm, the time taken barely rises as the size of the problem gets bigger and bigger. Doubling the size of the problem would just require one additional step. log2 n

Pseudocode is an algorithm implemented in human language:

1. Pick up phone book
2. Open to middle of phone book
3. Look at page
4. If person is on page
5. .....Call person
6. Else if person is earlier in book
7. .....Open to middle of left half of book
8. .....Go back to line 3
9. Else if person is later in book
10. ....Open to middle of right half of book
11. ....Go back to line 3
12. Else
13. ....Quit

In programming a function is a statement that gets the computer to do something.
Conditions are forks in the road of your algorithm.
Boolean expressions are questions whose answer is yes/no, true/false, 1/0.
Loops are cycles that repeat an action.
Variables represent values, like x,y,z in maths.
Threads allow a computer to do multiple things at once.

### Scratch

Scratch is a graphical programming language developed at MIT's Media Lab. It contains the same features as more complex programming languages: variables, functions, loops, events.

Abstraction is when you and others agree take a complicated idea and, while you can implement it the more complex way, you will think about it on a simpler level.

## 1 - C

There are a few guiding lights when writing code: correctness, design, style.

"hello, world" in C is:

```c
#include <stdio.h>

int main(void)
{
  printf("hello, world");
}
```

For a computer to understand this code, it needs to be converted from source code to machine code. A compiler is a programme designed to do this.

You need to type `make hello` to compile your code and `./hello` to run it.

A function is a programmed version of an algorithm. They take in arguments and can have side effects or return values.

```C
string answer = get_string("What's your name? ");
printf("hello, %s\n", answer);
```

Header files are programmes written in C with a .h file extension. `stdio.h` is the standard input output programme in C.

Comments should convey the purpose/intention of your code, not describe what it is literally doing.

### The Command Line

The command line lets you run commands without the need for a GUI.

For example:

ls - list files in current directory
rm - remove file
mv - move (rename) file
mkdir - make directory
cd - change directory
rmdir - remove directory

### Types

In C you have access to many data types: bool, char, double, float, int, long, string.

Each of these data types only have a finite number of bits.

Integers only use 32 bits. This can support 4 billion total values and lets you count from -2 billion to 2 billion. To work with larger numbers you'd need a long.

When working with formatted strings, you can use the following format codes:

%c - single character
%f - floating point value
%i - integer
%li - long
%s - string

C supports a number of mathmatical operators: +, -, \*, /, %.

### Typecasting

You need to keep track of which type you are using.

For example, if you divide an int by an int you'll get back an int, even if they don't divide evenly. You can store and print the result as a float but you'll lose everything after the decimal point. 4 / 3 would give you 1.000000.

```c
#include <cs50.h>
#include <stdio.h>

int main(void)
{
  int x = get_int("x: ");
  int y = get_int("y: ");

  float z = x / y;
  printf("%f\n", z);
}
```

You can get the computer to convert an int to a float by casting one data type to another: `float z = (float x) / (float) y`

Syntactic sugar is a different way of doing something syntactically that doesn't give you any new capabilities that you didn't already have.:`counter = counter + 1;` vs `counter += 1;` vs `counter++;`.

In C you use double quotes for strings but single quotes for individual characters.

### Abstraction

Abstraction is a computer programming principle where you can simplify otherwise more complicated detials.

A function lets you abstract its implementation details by just calling it by its name.

By convention, you write your custom functions after your main function. But C won't understand this since you'll be calling the function before you define it. To remedy this, place the prototype above the main function.

```c
#include <stdio.h>

// Prototype
void meow(void)

int main(void)
{
  for (int i = 0; i < 3; i++)
  {
    meow();
  }
}

void meow(void)
{
  printf("meow\n");
}
```

`void` refers the absence of input or output. If a function doesn't have a return value or arguments, mark it with `void`.

```c
void meow(int n)
{
  for (int i = 0; i < n; i++)
  {
    printf("meow\n");
  }
}
```

A do while loop is like a while loop but will do an action at least one time before checking a condition.

```c
#include <cs50.h>
#include <stdio.h>

// Prototype
int get_positive_int(void)

int main(void)
{
  int i = get_positive_int();
  printf("%i\n", i);
}

int get_positive_int(void)
{
  int n;
  do
  {
    n = get_int("Positive Integer: ");
  }
  while (n < 2);
  return n;
}
```

When you declare a variable inside curly braces you run into the issue of scope. The scope of a variable is the lines of code in which that variable exists and you can use it.

This is why you need to declare n outside the do while loop above.

### Floating-point imprecision

You can control how many decimal places printf will print `printf(%.10\n, x / y)` but you may run into floating-point imprecision.

Computers only have finite memory. If you only have a finite number of bits you can count pretty precisely but not infinitely high or low.

After a certain point the computer will have to approximate and you'll run into problems like 1 / 10 equaling 0.100000001490116119384........

### Integer overflow

Even integers have limitations. Integers are only 32 bit. If the calculation needs more than this then the result becomes inaccurate. If you need to carry a number but run out of space it gets dropped.

This is the same principle behind the Y2K scare. Any system storing years as two digits would go from 99 to 00 and interpret 2000 as 1900.

The Unix Epoch counds the seconds since 1 January 1970. Any programme that is keeping track of this using 32 bits will run into problems once it reaches 4 billion seconds, on 19 January 2038.

## 2 - Arrays

### Compiling

A compiler is a programme that converts source code to machine code. Clang is a popular compiler for C.

When all programmes had to be compiled, the default file produced was `a.out` for assembly output.

Clang can be configured with command line arguments but these can become long and verbose. Eventually you will want to automate the steps.

Sometimes when using a library it's not sufficient to include the header file at the top of your code, you need to explicitly tell the computer where to find the file.

When you comile your code there are a few steps involved:

- precompiling
- compiling
- assembling
- linking

First the computer preprocesses your code, looking for any lines starting with `#` and copying the contents of the referenced file into your own code.

To compile your code means to convert it from source code to another kind of source code, assembly code.

To assemble your code means to convert your code from assembly to machine code, 0s and 1s.

Finally the 0s and 1s of your code need to be linked to the 0s and 1s of any library you are using.

### Debugging

The most famous early bug is from Rear Admiral Grace Hopper's notebook.

Printing a value to the terminal is the easiest way to debug.

A debugger gives you more nuanced tools for debugging, letting you run your programme more slowly.

You can step through line by line, set breakpoints where you want to pause the execution of your code and see what is going on.
