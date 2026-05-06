Blog Topic : 3

How Generics Allow You to Build Reusable, Strictly Typed Functions and Components in TypeScript


Introduction

One of the main challenges in software development is writing code that is both reusable and type-safe. Often, developers face a trade-off: either write strict, type-safe code that only works for one data type, or use any to make it flexible and lose type safety.

TypeScript solves this problem with Generics. Generics allow you to write code that works with any data type while still maintaining strict type checking. This means no need for any, no loss of safety, and no unexpected runtime errors.


The Problem Without Generics

Suppose you want a function that returns the first element of an array. Without generics, you have two approaches:

Rigid and repetitive approach:

function getFirstNumber(arr: number[]): number {
  return arr[0];
}

function getFirstString(arr: string[]): string {
  return arr[0];
}


This works but is not reusable because you must write separate functions for each type.

Flexible but unsafe approach:

function getFirst(arr: any[]): any {
  return arr[0];
}

const first = getFirst([1, 2, 3]);
first.toUpperCase(); // it will create untime error

Here, flexibility is achieved using any, but type safety is completely lost.

The Solution: Generics

Generics introduce a type placeholder, usually written as <T>, which represents the type that will be used when the function is called.

function getFirst<T>(arr: T[]): T {
  return arr[0];
}

const firstNumber = getFirst([1, 2, 3]); 
//it is inferred as number

const firstString = getFirst(["a", "b", "c"]); 
//it is inferred as string

firstNumber.toUpperCase(); 
// it creates ompile-time error

With generics, a single function works for all types while preserving full type safety. TypeScript automatically infers the correct type.

Generic Functions

Generics can use multiple type parameters. For example:

function pair<T, U>(first: T, second: U): [T, U] {
  return [first, second];
}

const result1 = pair("Alice", 30);
//it is [string, number]

const result2 = pair(true, ["x", "y"]);
//it is [boolean, string[]]

TypeScript tracks each type separately and ensures accuracy.

Generic Interfaces

Generics can also be used in interfaces to create reusable data structures:

interface ApiResponse<T> {
  data: T;
  status: number;
  message: string;
}

interface User {
  id: number;
  name: string;
}

interface Product {
  id: number;
  price: number;
}

const userResponse: ApiResponse<User> = {
  data: { id: 1, name: "Alice" },
  status: 200,
  message: "Success",
};

const productResponse: ApiResponse<Product> = {
  data: { id: 5, price: 99.99 },
  status: 200,
  message: "Success",
};

One interface works for multiple data types, reducing duplication.


Generic Classes

Generics also apply to classes, making reusable data structures:

class Stack<T> {
  private items: T[] = [];

  push(item: T): void {
    this.items.push(item);
  }

  pop(): T | undefined {
    return this.items.pop();
  }

  peek(): T | undefined {
    return this.items[this.items.length - 1];
  }
}

const numberStack = new Stack<number>();
numberStack.push(10);

const stringStack = new Stack<string>();
stringStack.push("hello");
stringStack.push(42); 
//it will create compile-time error

The type is fixed when the class is created and enforced throughout.


Generic Constraints

Sometimes you want flexibility with limits. You can restrict generics using extends:
interface HasId {
  id: number;
}

function findById<T extends HasId>(items: T[], id: number): T | undefined {
  return items.find(item => item.id === id);
}

This ensures that only types with an id property are allowed.

Real-World Example

A common use case is fetching API data:

async function fetchData<T>(url: string): Promise<T> {
  const response = await fetch(url);
  const data: unknown = await response.json();
  return data as T;
}

interface Post {
  id: number;
  title: string;
  body: string;
}

const post = await fetchData<Post>("/api/posts/1");
//here post is typed as Post

Generics allow the function to return correctly typed data without using any.



Conclusion

Generics make it possible to write reusable and type-safe code at the same time. They remove the need for any while keeping code flexible and maintainable.

Key points to remember:

<T> acts as a type placeholder
TypeScript usually infers the type automatically
Use extends to add constraints when needed
Generics work with functions, interfaces, and classes

Whenever you need flexibility without losing type safety, generics are the best solution.
