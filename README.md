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
