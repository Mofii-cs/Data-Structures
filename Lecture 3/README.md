## COMS3134 - Lecture 3
### Implementation of ArrayList
```
MyArratList.java
```
* theItems = (AnyType []) new Object[ newCapacity ]; // we can't constuct a new Array with generics typeholder
```
public java.util.Iterator<AnyType> iterator( ){
    return new ArrayListIterator( );
}
```
* StringBuilder: the use of "+" to compound strings is not a good idea; using StringBuilder is much more efficient (making it possible to 'append' a string after the original one)
### nested class: static and non-static(inner)
```
1	class A{
2		class B{
3			...
4		}
5	}
```
* inner classes actually have access to instance variables of the 'outer' class
* while static nested classes don't
* nested classes can only be instantiated within non-static methods
* ++a: increment the variable by 1, then use the new value
* a++: use the old value first, then increment the variable by 1
### Linked Lists
* Garbage Collection: for every object, when the reference count reaches 0
### Stack - ADT
* 'Adding' or 'removing' elements only allowing at one side
```
core methods:
* push - adding - a[theSize ++] = x
* pop - removing - return a[-- theSize]
* peek/top - look at the 'peak' element and remove(?)
* isEmpty
* size - return the size
```
* last-in-first-out (LIFO) structure
* [ ][ ][ ][ ][ ][ ] => [2][ ][ ][ ][ ][ ] => [2][4][ ][ ][ ][ ]
* For doubly linked lists, pick on side to push or pop.
* Application of Stack: check parenthesis
```
* Scan thru the characters in the input codes one by one
* We use Stack because syntax like "( [ ) ]" is not valid in Java.
```
* Application of Stack: keep track of function calls
```
* call a function and return to where it is invoked
```
* Application of Stack: "racecar"
```
* check if a word if parellel(?)
```
