## Data Structures and Algorithm Analysis - Chapter 2
### Mathematical Background
* Definition 2.1
```
T(N) = O(f(N))
if there are positive constants c and n<sub>0</sub> such that T(N) ≤ cf(N) when N ≥ n<sub>0</sub>
e.g. 1000*N = O(N<sup>2</sup>)
```
* Definition 2.2
```
T(N) = Omega(g(N))
if there are positive constants c and n<sub>0</sub> such that T(N) ≥ cg(N) when N ≥ n<sub>0</sub>
```
* Definition 2.3
```
T(N) = Theta(h(N))
if and only if T(N) = O(h(N)) and T(N) = Omega(h(N))
```
* Definition 2.4
```
T(N) = o(p(N))
if for all positive constants c there exists an n<sub>0</sub> such that T(N) < cp(N) when N > n<sub>0</sub>
Less formally, T(N) = o(p(N)) if T(N) = O(p(N)) and T(N) != Theta(p(N))
```
* upper bound and lower bound
upper bound: f(N) is an upper bound on T(N) if T(N) = O(f(N))
lower bound: f(N) is a lower bound on f(N) is f(N) = Omega(T(N))
* Important rules:
```
Rule 1:
if T<sub>1</sub>(N) = O(F(N)) and T<sub>2</sub>(N) = O(g(N)), then
	(a) T<sub>1</sub>(N) + T<sub>2</sub>(N) = O(f(N) + g(N))
		(intuitively and less formally it is O(max(F(N), g(N)))))
	(b) T<sub>1</sub>(N) * T<sub>2</sub>(N) = O(f(N) * g(N))
```
```
Rule 2:
if T(N) is a polynomial of degree k, then T(N) = Theta(N<sup>k</sup>)
```
```
Rule 3:
log<sup>k</sup>N = O(N) for any constant k, which means that logarithms grow very slowly
```
```
Using L’Hôpital’s Rule:
we can always determine the relative growth rates of two functions f(N) and g(N) by computing
lim<sub>N->∞</sub>f(N)/g(N)
1. The limit is 0: This means that f(N) = o(g(N))
2. The limit is c &ne; 0: This means that f(N) = Theta(g(N))
3. The limit is ∞: This means that g(N) = o(f(N))
4. The limit does not exist: There is no relation
```
### Model
* A model of computation, in which instructions are executed sequentially
* standard repertoire of simple instructions, such as addtion, multiplication, comparison, and assignment
### What to Analyze
* the Running Time - the algorithm rather that the programs
### Maximum Subsequence Sum Problem
```
Given (possibly negative) integers A<sub>1</sub>, A<sub>2</sub>, ..., A<sub>N</sub>, find the maximum value of (A<sub>i</sub> + A<sub>i+1</sub> + ... + A<sub>j</sub>). For convenience, the maximum subsequence sum is 0 if all the integers are negative.
```
### Running Time Calculations
```
To calculate 1<sup>3</sup> + 2<sup>3</sup> + 3<sup>3</sup> + ... + N<sup>3</sup>:
1	public static int sum(int n){
2		int partialSum;
3		partialSum = 0;
4		for (int i = 1; i <= n; i++){
5			partialSum += i * i * i;
6		}
7		return partialSum;
8	}
```
1. Declarations count for no time.
2. Lines 3 and 7 count for one unit each.
3. Line 5 counts for four units per time executed.
4. Line 4 has the hidden costs of initializing i, testing i &le; N, and incrementing i, which add up to 2N+2.
Add each steps up => 6N + 4 => O(N)
### General Rules
* Rule 1 - for loops
```
The running time of a for loop is at most the running time of the statements inside the for loop (including tests) times the number of iterations.
```
* Rule 2 - Nested loops
```
The total running time of a statement inside a group of nested loops is the running time of the statements multiplied by the product of the sizes of all the loops.
```
* Rule 3 - Consecutive Statements
```
These just add. O(N) + O(N<sup>2</sup>) = O(N<sup>2</sup>)
```
* Rule 4 - if/else
```
The running time of an if/else statement is never more than the running time of the test plus the larger of the running times of S1 and S2.
```
### Solutions for the Maximum Subsequence Sum Problem
* Algorithm 1
```
1	public static int maxSubSum1(int[] a){
2		int maxSum = 0;
3		for (int i = 0; i < a.length; i++){
4			for (int j = i; j < a.length; j ++){
5				int thisSum = 0;
6				for(int k = 1; k <= j; k++){
7					thisSum += a[k];
8				}
9				if (thisSum > maxSum){
10					maxSum = thisSum;
11				}
12			}
13		}
14		return maxSum;
15	}
```
	==> (N<sup>3</sup> + 3 * N<sup>2</sup> + 2 * N) / 6
	==> O(N<sup>3</sup>)
* Algorithm 2
```
1	public static int maxSubSum2(int[] a){
2		int maxSum = 0;
3		for (int i = 0; i < a.length; i++){
4			int thisSum = 0;
5			for(int j = 0; j < a.length; j++){
6				thisSum += a[j];
7				if (thisSum > maxSum){
8					maxSum = thisSum;
9				}
10			}
11		}
12		return maxSum;
13	}
```
	==> O(N<sup>2</sup>)
* Algorithm 3
```
1	private static in maxSumRec(int[] a, int left, int right){
2		if (left == right){
3			if(a[left] > 0){
4				return a[left];
5			} else {
6				return 0;
7			}
8		}
9	
10		int center = (left + right) / 2;
11		int maxLeftSum = maxSumRec(a, left, center);
12		int maxRightSum = maxSumRec(1, center + 1, right);
13	
14		int maxLeftBorder = 0, leftBorderSum = 0;
15		for (int i = center; i >= left; i --){
16			leftBorderSum += a[i];
17			if (leftBorderSum > maxLeftBorderSum)
18				maxLeftBorderSum = leftBorderSum;
19		}
20	
21		int maxRightBorderSum = 0, rightBorderSum = 0;
22		for (int i = center; i <= right; i++){
23			rightBorderSum += a[i];
24			if (rightBorderSum > maxRightBorderSum)
25				maxRightBorderSum = rightBorderSum;
26		}
27	
28		return max3(maxLeftSum, maxRightSum, maxLeftBorderSum + maxRightBorderSum);
29	
30		public static in maxSubSum3(int[] a){
31			return maxSumRec(a, 0, a.length-1);
32		}
33	}
```
	==> T(1) = 1; T(N) = 2T(N/2) + O(N)
	==> T(N) = O(NlogN)
* Algorithm 4
```
1	public static int maxSubSum4(int[] a){
2		int maxSum = 0, thisSum = 0;
3		for (int j = 0; j < a.length; j++){
4			thisSum += a[j];
5			if (thisSum > maxSum){
6				maxSum = thisSum;
7			}
8			else if (thisSum < 0){
9				thisSum = 0;
10			}
11		}
12		return maxSum;
13	}
```
==> This algorithm is actually much faster.
==> And it makes only one pass thru the data, called online algorithm.
* Online Algorithm: An algorithm that makes only one pass thru the data, and at any point in time, can correctly give an answer to the subsequence problem for the data it has already read. An online algorithm that requires only constant space and runs in linear time is just about as good as possible.
### Logarithms in the Running Time
* Binary Search
```
1	public static <AnyType extends Comparable<? super AnyType>> int binarySearch(AnyType[] a, AnyType x){
2		int low = 0, high = a.length - 1;
3	
4		while (low <= high){
5			int mid = (low + high) / 2;
6			if (a[mid].compareTo(x) < 0){
7				low = mid + 1;
8			} else if (a[mid].compareTo(x) > 0){
9				high = mid - 1;
10			} else {
11				return mid;
12			}
13		}
14		retunr NOT_FOUND; // NOT_FOUND is defined as -1
15	}
```
1. All the work done inside the loop takes O(1) per iteration, thus the number of times around the loop is at most [log(N-1)] + 2.
2. Binary search can be viewed as our first data structure implementation. It supports the <I>contains</I> opertaion in O(logN) time, but all other operations (in particular <I>insert</I>) require O(N) time.
* Euclid's Algorithm
```
1	public static long gcd(long m, long n){
2		while (n != 0){
3			long rem = m % n;
4			m = n;
5			n = rem;
6		}
7		return m;
8	}
```
1. The number of iterations is at most 2logN = O(logN).
2. Theorem 2.1: If M > N, then M mod N < M/2.
3. Actually the contant, 2, can be improved slightly, to roughly 1.44(logN).
* Exponentiation
```
1	public static long pow(long x, int n){
2		if (n == 0)
3			return 1;
4		if (n == 1)
5			return x;
6		if (isEven(n))
7			return pow(x * x, n/2);
8		else
9			return pow(x * x, n/2) * x;
10	}
```
1. The program will run in O(logN).
### A Grain of Salt
### Summary
