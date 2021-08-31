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

By convention, you write your custom functions after your `main` function. But C won't understand this since you'll be calling the function before you define it. To remedy this, place the prototype above the `main` function.

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

### Floating-point Imprecision

You can control how many decimal places printf will print `printf(%.10\n, x / y)` but you may run into floating-point imprecision.

Computers only have finite memory. If you only have a finite number of bits you can count pretty precisely but not infinitely high or low.

After a certain point the computer will have to approximate and you'll run into problems like 1 / 10 equaling 0.100000001490116119384........

### Integer Overflow

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

One final debugging technique is rubber duck debugging. Sometimes explaining out loud what your code is supposed to do can clarify things.

### Memory

On a typical computer each data type in C is defined as taking up a fixed amount of space. This varies, but for example:

- bool - 1 byte
- char - 1 byte
- double - 8 bytes
- float - 4 bytes
- int - 4 bytes
- long - 8 bytes
- string - ? bytes

It's in memory (RAM) that programmes are stored while running and files are stored while open.

RAM is much faster than solid state storage but it's also volatile, it requires electricity to maintain it.

Imagine your computer's memory as a grid of bytes. An int would take up 4 spaces. In those 4 spaces would be a pattern of 0s and 1s representing the int.

### Arrays

An array is a sequence of values stored in memory back to back.

In C you need to specify how many values you want to store in the array when you declare it. The exception is when you are passing an array to a custom function, because you don't know in advance.

```c
int scores[3];

scores[0] = 72;
scores[1] = 73;
scores[2] = 33;
```

A constant is a variable whose value cannot change.

```c
const int TOTAL = 3;
```

### Strings

If you cast a character to an int, you can access its ASCII value.

Each char is stored in a single byte.

By default, C does not have a string datatype.

A string is an array of characters.

So the string `"HI!"` is equivalent to the array `['H', 'I', '!']`.

You can access the individual characters of a string using [] notation.

The computer's memory knows when strings begin and end because, under the hood, the string uses one extra byte, `\0` or `NUL`, to represent the end of the string. For example, the string `HI!` uses 4 bytes, not 3.

```c
string s = "HI!"
printf("%i %i %i %i\n", s[0], s[1], s[2], s[3]);
// 72 73 33 0
```

One dangerous aspect of C is that you can access values from other parts of memory. If you accessed `s[4]` you would get whatever value is in this adjacent spot in memory.

If you want to loop to the end of a string and then stop, you could set your loop to break when it reaches `\0` or use the `strlen()` function from `<string.h>`.

```c
int main(void)
{
  string s = get_string("Input: ");
  printf("Output: ");
  for (int i = 0, n = strlen(s); i < n; i++)
  {
    printf("%c", s[i]);
  }
  printf("\n");
}

```

### Arrays of Strings

You can have an array of strings. And since a string is itself an array, this is an array of arrays.

```c
string words[2];
words[0] = "HI!";
words[1] = "BYE!";
```

You can use multiple [] to access values from nested arrays.

```c
words[0][0]
// 'H'
words[1][1]
// 'Y'
```

The ASCII values of uppercase and lowercase letters are always 32 apart. You could uppercase a lowercase letter by subtracting 32 from it. Or you could just use the `toupper()` function from `<ctype.h>`. `toupper()` expects a character as input; you cannot pass a word to it. To make a string uppercase you would need to loop over every character in the string.

### Command-line Arguments

Just as custom functions can take inputs, so can main.

```c
int main(int argc, string argv[])
{

}
```

This means that this `main` takes an int and an array of strings as its input.

`argc` stands for argument count, the number of words you expect your user to type at the prompt. This includes the name of your programme.

`argv` stands for argument vector, an array of the strings typed by the user.

### Exit Status

Programmes often return an int to show what has happened. 0 indicates that nothing as gone wrong. This is why in C you set up `main` to return an int.

```c
int main(int argc, string argv[])
{
  if (argc != 2)
  {
    printf("missing command-line argument\n");
    return 1;
  }
  printf("hello, %s\n", argv[1]);
  return 0;
}
```

### Cryptography

Cryptography is the art of scrambling information in order to hide it.

If that information is text, you can convert the plaintext to ciphertext.

A cipher is an algorithm that scrambles its input so as to produce an output that a third party can't understand. That algorithm is a reversible process so that you can decipher the text and read it.

Ciphers use a key to determine how to encrypt and decrypt the input.

## 3 - Algorithms

A computer can only look at one location in an array at any one time.

Designing a search algorithm well is a compelling problem to solve.

Running time is how long an algorithm takes to run. This is the basis of Big O notation.

An algorithm with a linear curve could be described as O(n), one twice as fast would be O(n/2), one that is logarithmic would be O(log2 n).

Computer scientists tend to ignore constant factors and focus on the dominant factor. So this would be simplififedto O(n) and O(log n).

You tend to see common formulas:

- O(n2)
- O(n log n)
- O(n)
- O(log n)
- O(1)

Just as Big O notation refers to an upper bound of how much time an algorithm will take, Ω notation refers to the lower bound.

### Linear Search

Linear search sequentially checks every item in a list.

This has a time complexity of O(n) and Ω(1).

```c
int main(void)
{
  int numbers[] = {4,6,8,2,7,5,0};

  for (int i = 0; i < 7; i++)
  {
    if (numbers[i] == 0)
    {
      printf("Found\n");
      return 0;
    }
  }
  printf("Not found\n");
  return 1;
}
```

### Binary Search

Binary search repeatedly divides in half the part of a list that could contain an item, until the possible locations is narrowed down to just one.

This has a time complexity of O(log n) and Ω(1).

### Structs

Using `typefed` and the `struct` keyword, C can create a datatype that is combination of other datatypes. This could be useful for storing key value pairs.

```c
typedef struct
{
  string name;
  string number;
}
person;
```

Phone numbers should be represented using strings not ints since they can have non-numeric characters in them.

```c
typedef struct
{
  string name;
  string number;
}
person;

int main(void)
{
  person people[2];

  people[0].name = "Brian";
  people[0].number = "+1-617-495-1000";

  people[1].name = "David";
  people[1].number = "+1-949-468-2750";

  for (int i = 0; i < 2; i++)
  {
    if (strcmp(names[i].name, "David") == 0)
    {
      printf("Found %s\n", people[i].number);
      return 0;
    }
  }
  printf("Not found\n");
  return 1;
}
```

### Selection Sort

Selection sort loops over a list, finding the smallest unsorted item and swapping it with the leftmost unsorted item until all items have been sorted. It is relatively inefficient.

It has a time complexity of O(n2) and Ω(n2).

### Bubble Sort

Bubble sort loops over a list, compares two adjacent elements and swaps them if they are in the wrong order. The loop is repeated until the list is sorted. The largest values bubble up to the end of the list.

It has a time complexity of O(n2) and Ω(n).

### Recursion

Recursion is the ability for a function to call itself.

You need to have a base case to quit execution.

### Merge Sort

Merge sort is a divide and conquer algorithm where you divide the unsorted list into n sublists, each containing one item, and then repeatedly merge the sublists to produce new sorted sublists until there is only one remaining.

Or in other terms: sort the left half, sort the right half, merge both halves.

It has a time complexity of O(n log n) and Ω(n).

Any time an algorithm has the same upper bound and lower bound, you can describe it with ϴ notation.

## 4 - Memory

Hexadecimal is a base-16 system using 0-9 and A-F.

So 0F = 16 and 10 = 17 and FF = 255.

Conveniently, one hexadecimal digit is equivalent to four binary digits.

By convention, hexademcial digits are represented with a `0x` prefix - `0x48` or `0x21` - to distinguish them from binary digits.

Hexadecimal is is the basis of RGB. That's why #000000 is black, the absence of colour and #FFFFFF is white, the complete saturation of colour.

### Addresses and Pointers

C has an `&` operator for looking up addresses in memory. The `*` operator is for looking inside a particular memory address.

```c
int n = 50;
printf("%p\n", &n);
// 0x7ffd80792f7c
```

A pointer is a variable that contains the address of some other value. A pointer takes up 8 bytes.

```c
int n = 50;
int *p = &n;
printf("%p\n", p);
// 0x7ffeeec8d03c
printf("%p\n", *p);
// 50
```

### Strings

Strings can be manipulated via their addresses. Since a string is an array of contiguous characters and ends in `\0`, you just need to know the address of the first character and you can find the rest of the string.

```c
string s = "HI!";
printf("%p\n", &s[0]);
printf("%p\n", &s[1]);
printf("%p\n", &s[2]);
// 0x4006b4
// 0x4006b5
// 0x4006b6
```

Just as you can think of strings as sequences of characters or as arrays, you can also think of them as pointers, the address of a character in memory.

Technically, string does not exist as a datatype in C. Instead it is `char *`, the address of a character.

For example, `<cs50.h>` uses `typedef char *string;` to create `string` as a synonym for `char *`.

### Pointer Arithmetic

You can do simple arithmetic on a pointer to access nearby addresses.

```c
char *s = "HI!";
printf("%c\n", *s);
printf("%c\n", *(s+1));
printf("%c\n", *(s+2));
```

When you touch memory you shouldn't, you may get a segmentation fault.

If you try to naively compare two strings, you'll be comparing the addresses of their first characters.

The `strcmp` function lets you compare the values of two strings.

```c
char *s = get_string("s: ")
char *t = get_string("t: ")

if(strcmp(s,t) == 0)
{
  printf("Same\n")
}
else
{
  printf("Different\n")
}
```

If you copy a string by simply assigning one string to another, they will both point to the same address in memory. This will later cause problems if you change one of the strings.

To safely copy a string, you need to assign a space in memory to copy its contents into. Use the `malloc` (memory allocation) function.

`malloc` takes a number specifying how many bytes of information to allocate. Remember to keep one for the null character.

`NULL` represents a null pointer, the absence of an address.

Any time you ask the computer for memory using `malloc`, the onus is on you to eventually give it back. Use `free` to free it up again.

### Valgrind

Valgrind is a tool for memory debugging, helping you to figure out where you touched memroy you shouldn't have or putting in `free` when needed, preventing a memory leak.

You should never trust the contents of your computer's memory if you have not explicitly put the content there. Assume it's a "garbage value".

Always initialize values before thinking of touching or reading them.

### Memory Layout

By convention, a computer doesn't just put things in random locations in memory. It treats different portions of memory differently.

When you run a programme, all the 0s and 1s are stored in machine code, seperately you have your globals, then the heap (a chunk of memory that `malloc` uses to get you a spare chunk of memory).

When you call a function, it uses stack space rather than heap space.

The stack is a dynamic space where memory keeps getting used and reused.

| Memory       |      |
| ------------ | ---- |
| machine code |      |
| globals      |      |
| heap ↓       |      |
|              | swap |
| stack ↑      | main |

If you want a function to change the contents of a variable, you need to pass in the address of the variable.

```c
void swap(int *a, int *b)

int main(void)
{
  int x = 1;
  int y = 2;

  printf("x is %i, y is %i\n", x, y);
  swap(&x,&y);
  printf("x is %i, y is %i\n", x, y);
}

void swap(int *a, int *b)
{
  int temp = *a;
  *a = *b;
  *b = *tmp;
}
```

Having the heap and stack consume memory from each end sets up problems to occur.

A stack overflow is when you call a function so many times that it overflows the heap.

When using iteration you probably won't overflow the stack but with recursion there is an inherent danger of overflow.

A buffer overflow is when you allocate memory (for example, for an array) and then go over the limits of it.

### scanf

scanf reads input from the user.

If you manually assign space in memory for the input, you need to be aware that the user could enter more or less data, requiring more or less space in memory.

```c
int main(void)
{
  char s[4];
  printf("s: ");
  scanf("%s", s);
  printf("s: %s\n", s);
}
```

### File I/O

If you put a programme in memory, as soon as the programme ends it's contents are gone. Files allow for data to be saved long term.

You can open files in different ways: to read them, to (over)write them or to append to them.

You need to tell C when you are opening and closing a file and while mode you are working in.

```c
int main(void)
{
  FILE *file = fopen("phonebook.csv", "a");
  if (file == NULL)
  {
    return 1;
  }

  char *name = get_string("Name: ");
  char *number = get_string("Number: ");

  fprintf(file, "%s,%s\n", name, number);

  fclose(file);
}
```

You can often determine a file's type by looking at its first few bytes. These "magic numbers" at the beginning of the files are industry standards.

A jpeg will start with `0xff 0xd8 0xff`.

## 5 - Data Structures

### Arrays

Say you have an array with three elements and you want to add one more but the adjacent space in memory is already occupied by another value that's currently in use.

You could create a new, larger array and copy the values into it.

The running time of inserting into an array like this has an upper bound of O(n) and a lower bound of Ω(1).

`realloc` works like `malloc` but takes two arguments: the address of a chunk of memory you've already allocated and the size of the memory you want to allocate to the new value. It copies the old values into the new space in memory.

```c
int main(void)
{
  int *list = malloc(3 * sizeof(int));
  if (list == NULL)
  {
    return 1;
  }

  list[0] = 1;
  list[1] = 2;
  list[2] = 3;

  int *tmp = realloc(list, 4 * sizeof(int));
  if (tmp == NULL)
  {
    free(list);
    return 1;
  }

  tmp[3] = 4;

  free(list);

  list = tmp;

  for (int i = 0; i < 4; i++)
  {
    printf("%i\n", list[i]);
  }

  free(list);
}
```

### Linked Lists

A linked list is a data structure that solves some of the problems with arrays.

You can grow and shrink the data structure dynamically without having to touch all the data and move it to a new location, making inserting data more efficient.

You can put values wherever there is room in memory. For each value you also store metadata to keep track of location of the next value.

A linked list is a collection of node conected by pointers.

The trade-off is that is takes up more space in memory and you cannot rely on binary search.

The running time of searching a linked list is O(n).

If you don't care about sorted order, the running time of inserting into a linked list is O(1).

```c
typedef struct node
{
  int number;
  struct node *next;
}
node;

int main(void)
{
  node *list = NULL;

  node *n = malloc(sizeof(node));
  if(n == NULL)
  {
    return 1;
  }
  n->number = 1;
  n->next = NULL;
  list = n;

  n = malloc(sizeof(node))
  if(n == NULL)
  {
    free(list);
    return 1;
  }
  n->number = 2;
  n->next = NULL;
  list->next = n;

  n = malloc(sizeof(node))
  if(n == NULL)
  {
    free(list->next);
    free(list);
    return 1;
  }
  n->number = 3;
  n->next = NULL;
  list->next->next = n;

  for (node *tmp = list; tmp != NULL; tmp = tmp->next)
  {
    printf("%i\n", tmp->number);
  }

  while (list != NULL)
  {
    node *tmp = list->next;
    free(list);
    list = tmp;
  }
}
```

If you insert a new node without keeping track of the existing nodes, you have orphaned them, creating a memory leak.

You can stitch together data structures in memory using pointers as a thread.

### Trees