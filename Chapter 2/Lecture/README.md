## Data Structures - Lecture 2
### Run-tim Analysis
* Analyze the 'cost' the algorithm
* By counting how many operations the computer perform, we can come up with an expression.
Example:
```
1   int sum = 0;
2   for (int i = 0; i < a.length; i ++){
3   	sum += a[i];
4   }
```
i ++ => 1 operation
2 + (2 + 3 + 1) * n = 2 + 6n (operations)
As n gets really large, (2 + 6n) ~ (2*10<sup>9</sup>)
Example:
```
1   for (i = 0; i < a.length; i++){
2   	for (j = 0; j < a.length; j++){
3   		// something constant (single operation)
4   	}
5   }
```
n<sup>2</sup> + n
* T(N) = O(f(N)), if there are positive constants c and n<sub>0</sub> such that T(N) ≤ cf(N) when N ≥ n<sub>0</sub>
* T(N) = Omega(g(N)), if there are positive constants c and n<sub>0</sub> such that T(N) ≥ cg(N) when N ≥ n<sub>0</sub>
* T(N) = Theta(h(N)), if and only if T(N) = O(h(N)) and T(N) = Omega(h(N))
* The Avg. scenario of linear search is not O(n/2) because when the target is not in the array, it is always necessary to make n comparisons.
* if T(N) is a polynomial of degree k, then T(N) = Theta(N<sup>k</sup>)
* log<sup>k</sup>N = O(N) for any constant k, which means that logarithms grow very slowly
```
1	for (i = 0; i < n; i ++){
2		for (j = i; j < n; j++){
3			x ++;
4		}
5	}
```
