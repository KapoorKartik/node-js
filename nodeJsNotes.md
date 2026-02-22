### Node js 
---
- Node js is a runtime environment that allows to build server side application with java script
#### Even Loop
- Simple Defination
   - The Event Loop is the mechanism that allows Node.js to handle multiple operations using a single thread.
   - Node js is a single threaded, non blocking and asyn in nature
   - what this means if i've to run 1000 api calls, dnb query a single thread won't works without frezing 
   - That where even loop comes
   - It has three core pieces
      - Call Stack
      - Web api/ Libuv (Node js c++ backend)
      - Callback queues
#### 1. Call Stack
- This is where js executes synchronously
- And i can understand stack works as a lifo 
- Example given below

```
function A() {
   console.log("A")
  B();
}

function B() {
   console.log("B")
  C();
}

function C() {
  console.log("C");
}

A();
```
- In this example output would be because callback stack look like below 
 ```
first A()->then console inside A -> then go inside B() -> console inside b -> go inside C() -> then console C 
 
A
B
C
```
- But what if I first call the funcion and then console will the output
differs or still be the same?

```
function A() {
  console.log("A");
  B();
}

function B() {
  console.log("B");
  C();
}

function C() {
  console.log("C");
}

A();

In this case execution order would be A() -> B() -> C() -> console log c -> came out of c and execute the 
console log b -> came out of b -> console log a

C
A
B
```