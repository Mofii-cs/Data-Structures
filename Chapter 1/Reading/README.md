## Data Structures and Algorithm Analysis - Chapter 1
### Selection Problem: determine the kth largest element
* sort the list in decreasing order, then return the kth element
* sort the first kth element in decreasing order, add the remaining element by comparing with the kth element, ignore it if it is smaller
* a better way?
### Optimization Efforts
### Series
* S = A^0 + A^1 + A^2 + ... + A^n + ... (0 < A < 1) <= 1 / (1 - A) [Geometric series]
* S = 1 / (2^1) + 2 / (2^2) + ... + n / (2^n) + ... = 2
* S = 1 + 2 + 3 + ... + n = n * (n + 1) / 2 => (n^2) / 2 [Arithmetic series]
* S = 1^2 + 2^2 + 3^2 + ... + n^2 = n * (n + 1) * (2n + 1) / 6 => (n^3) / 3
* S = 1^k + 2^k + 3^k + ... + n^k => (n^(k+1)) / |k + 1| (k != -1)
* Harmonic numbers: H<sub>N</sub> = 1 / 1 + 1 / 2 + 1 / 3 + ... + 1 / N => log<sub>e</sub>N tends to γ (Euler's constant: 0.57722)
###A is congruent to B modulo N, written A ≡ B(mod N)
*If N is a prime number, there are three theorems:
*ab ≡ 0 (mod N) is true if and only if a ≡ 0 (mod N) or b ≡ 0 (mod N)
*If N is a prime number, then the equation ax ≡ 1 (mod N) has a unique solution, for all 0 < a < N. The solution 0 < x < N, is the multiplicative inverse.
*If N is a prime number, then the equation x^2 ≡ a (mod N) has either two solutions, for all 0 < a < N, or no solutions.
###The P Word
*Induction, Contradiction, and Counterexample
*Induction: base case => inductive hypothesis => first k to (k + 1)
*Contradiction: Proof by contradiction proceeds by assuming that the theorem is false and showing that this assumption implies that some known property is false, and hence the original assumption was erroneous.

###Recursion
*Recursive: A function that is defined in terms of itself.
*Using recursion for numerical calculations is usually a bad idea.
*Example:
```
1   public static int f(int x){
2       if (x == 0){
3           return 0;
4       } else
5           return 2 * f(x - 1) + x * x;
6   }
```
*Recursive calls will keep on being made until a base case is reached.
*Fundamental rules of recursion:
```
1. Base cases. You must always have some bvase cases, which can be solved without recursion.
2. Making progress. For the cases that are to be solved recursively, the recursive call must always be to a case that makes progress toward a base case.
3. Design rule. Assume that all the recursive calls work.
4. Compound interest rule. Never duplicate work by solving the same instance of a problem in separate recursive rules.
```
###Printing numbers:
```
1   public static void printOut(int n){       // print nonnegative n
2       if (n >= 10)
3           printOut(n / 10);
4       printDigit(n % 10);
5   }
```
###Recursion and Induction
###Implementing Generic Components Pre-Java 5
###Implementing Generic Components Using Java 5 Generics
###Function Objects
