Level:2=>> Assignment 1

What is in this repo

There are 3 files in this repo.

solutions.ts — this has all the problem solutions
blog-1.md — this is a blog about any vs unknown in typescript
blog-2.md — this is a blog about generics in typescript


About the solutions
Problem 1
I made a function that takes a number array and returns only the even numbers from it.


Problem 2
I made a function that takes a string and returns it reversed.


Problem 3
I made a function that checks if a value is a string or a number and returns which one it is.


Problem 4
I made a generic function that takes an object and a key and returns the value of that key from the object.


Problem 5
I made a function that takes a book object and adds a isRead property to it and returns it.


Problem 6
I made a Person class and a Student class. Student extends Person and has a getDetails method that returns the student info as a string.


Problem 7
I made a function that takes two number arrays and returns only the numbers that exist in both arrays.


About the blogs
blog-1.md
This blog is about why using any in typescript is bad. When you use any, typescript stops checking types and that causes errors at runtime. unknown is a safer option because it forces you to check the type before using it. The blog also shows how to do type narrowing using typeof, instanceof and the in operator.


blog-2.md
This blog is about generics in typescript. Generics let you write one function or class that works for any type without losing type safety. The blog shows how to use generics in functions, interfaces and classes. It also shows how to add constraints using extends.



How to run the solutions file
first install typescript if you dont have it


npm install -g typescript

then compile and run

tsc solutions.ts

node solutions.js

or just use ts-node

npm install -g ts-node

ts-node solutions.ts

