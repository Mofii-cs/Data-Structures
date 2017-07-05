## COMS-3134 Lecture 1
### Prep:
* Mid-term: Monday of 4th Week
* TA Office Hour: Evening of Tuesday, Thursday, and Friday
* Instructor Office Hour: After Lecture
* Textbook: Data Structures and Algorithm Analysis in Java 3rd Edition by Mark Allen Weiss
* Reading: Chapter 1 and 2
### Data Structures:
* Array, ArrayList
* Binary Search: O( log N )
* Linked list
### Generic Class
* ArrayList<Integer> a = new ArrayList<>(); creating an arraylist of integers
* In arraylist, 'generic' is built-in
* generic identifier
* use wrapper class instead of primitive class
### Proof:
* Induction, Contradiction, and Counterexample
### Recursion:
* Fib(k) = Fib(k-1) + Fib(k-2) (k >= -1), Fib(0) = 1, Fib(1) = 1
* Using induction proof: F(i) < (5/3)<sup>i</sup> (i >= 1)
```
I. Show base cases: F(1) = 1 < 5/3
                    F(2) = 2 < 25/9
II. Assume true for up to k
    Such that:
    F(k+1) < (5/3)<sup>k</sup> + (5/3)<sup>k+1</sup>
           = (3/5 + 9/25) * (5/3)<sup>k+1</sup>
           < (5/3)<sup>k+1</sup>
```
### Factorial
### Tower of Hanoi
### Java Review: Generics
