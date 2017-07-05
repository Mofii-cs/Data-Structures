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
L’Hôpital’s Rule:
```
