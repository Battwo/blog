---
title: "The art of debugging"
date: 2025-12-5
---

<h1> Debugging Adventures: How I Learned to Tame Sneaky Bugs
</h1>

<br>
Imagine this: it’s Friday, you finally get home, the house is empty, and you’re ready to relax. You turn on the TV… but there’s no sound? You check the volume, check if it’s muted, and even make sure the speakers are plugged in. Nothing works. After a few minutes of panic, you discover the babysitter broke it right before you got home.

Believe it or not, that exact process is basically what debugging is. Debugging is all about finding and fixing problems. Programmers do the same thing with code, they figure out what’s supposed to happen, compare it with what’s actually happening, and then test different pieces until they find the bug.

That’s how I debug! I test things one at a time, pay attention to the results, and keep going until the problem is solved. It takes patience, but it’s also incredibly satisfying when the lightbulb finally clicks.

Below, I’m going to walk you through four code snippets I debugged recently. I’ll show you the original code, explain what it’s supposed to do, the problems I found, and how I fixed it. Whether you’re a coding pro or just starting out, I promise it’ll make sense, and maybe, just maybe even be a little fun.


<h1> Temperature Trouble 
</h1>

```python
temperature = 75

if temperature > 80:
    print("It's hot")
elif temperature > 50:
    print("It's temperate")
elif temperature < 0:
    print("It's cold")


```

This code is supposed to tell us whether the temperature is hot, temperate, or cold. Basically, we’re giving the computer a thermometer and asking it to explain the weather in words

<h2>
what's wrong?
</h2>

If the temperature is 25, what will this code print?

1. It prints “It’s hot”
2. It prints “It’s temperate”
3. It prints “It’s cold”
4. It prints nothing

Answer: D – Nothing!


If the temperature is 25, the program prints nothing. Why? Because there’s no instruction for temperatures between 0 and 50. The code has a 
“logic gap.”

<h2>
The solution
</h2>

```python
temperature = 25

if temperature > 80:
    print("It's hot")
elif temperature > 50:
    print("It's temperate")
elif temperature < 0:
    print("It's cold")
else:
    print("It's cool")

```


Now it prints “It’s cool” for temperatures in that range. Debugged and ready to go!

<br>

<h1>
Counting Spaces 
</h1>


```python
text = "Hello, world, my name is"
count = 0

for char in text:
    if char == "":
       count += 1

print(count)

```

This snippet is meant to count how many spaces are in a string. It loops through each character and increases a counter whenever it finds a space.


<h2>
What's wrong?
</h2>

what's the issue with this code?
2. The if condition char == "" will never be true, so spaces are not counted.
3. The count variable should start at 1 instead of 0.
4. The print statement is in the wrong place.

Answer: B

The condition char == "" will never be true. That’s because an empty string isn’t the same as a space " ".

<h2>
The solution
</h2>

```python
text = "Hello, world, my name is"
count = 0

for char in text:
    if char == " ":
       count += 1

print(count)

```

Now it correctly counts the spaces! This is a classic logic bug. the program runs, but doesn’t do what we expect.

<br>
<h1>
Even or Odd?
</h1>

```python
print("give me a number")

n = input()

for num in range(1, n):
    if num % 2 < 0:
        print(num, "is even.")
    else:
        print(num, "is odd.")

```

This code should tell us whether numbers from 1 to n are even or odd.

<h2>
What's wrong?
</h2>

what's the issue with this code? 


1. input() gives a string, not a number, so range(1, n) will cause an error.
2. num % 2 < 0 will never be true, so even numbers are not detected correctly.
3. Both A and B
4. Nothing is wrong; it works perfectly


Answer: C!


1. input() returns a string, but range() needs an integer.
2. num % 2 < 0 is wrong. % 2 gives 0 for even, 1 for odd, so this condition never works.

<h2>
The solution
</h2>

```python
print("Give me a number")
n = int(input())

for num in range(1, n):
    if num % 2 == 0:
        print(num, "is even.")
    else:
        print(num, "is odd.")

```
types matter and logic matters. Debugging step by step helps you catch both issues.
<h1>
Password Checker
</h1>

```python
attempts = 0
correct_password = "secret"

while True:
    password = input("Enter your password: ")
    attempts += 1

    if password == "incorrect_password":
        print("Correct password!")
    else:
        print("Incorrect password")

    if attempts > 3:
        print("Too many attempts")
        break
```

the purpose for this code is to ask the user for a password, check if it’s correct, and limit attempts to 3

<h2>
Quiz Time
</h2>

Take a close look at the code. What’s wrong here? 

1. The program will never end.
2. The line if password == "incorrect_password" is checking the wrong thing.
3. The attempts counter doesn’t increase.
4. Nothing is wrong; it works perfectly. 

Hint: Think about what the programmer meant versus what the code actually does.

If you picked Answer: B then you're right! The code is checking against the literal string "incorrect_password" instead of the variable correct_password. That means it always prints “Incorrect password,” even if the user enters "secret"!

<h2>
The solution
</h2>

```python
attempts = 0
correct_password = "secret"

while True:
    password = input("Enter your password: ")
    attempts += 1

    if password == correct_password:
        print("Correct password!")
        break
    else:
        print("Incorrect password")

    if attempts >= 3:
        print("Too many attempts")
        break

```

Always check variable names and loop logic when debugging, it’s amazing how one small mistake can make the program behave completely wrong.

<br>

Debugging is like detective work. You look at what should happen, compare it to what actually happens, and figure out the tiniest missteps that are causing problems.
Going through these snippets taught me a few big things

1. Check types: strings, numbers, and other data types matter.
2. Check logic: sometimes the code runs perfectly but doesn’t do what you want.
3. Step-by-step debugging works every time—you don’t need to know the answer at the start.


I feel like a code detective now, and I know that these debugging skills will help me in every project I tackle in the future.
