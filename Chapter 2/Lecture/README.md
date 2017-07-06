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
n*(n+1)/2 = O(n<sup>2</sup>)
```
if (condition){
	alg 1;
} else {
	alg 2;
}
```
### Abstract Data Type(ADT)
list -> get(i), set(i), add(), remove()
```
public interface Collection<AnyType> extends Iterable<AnyType>{
	int size();
	...
	java.util.Iterator<AnyType> iterator(); // return some class that implements iterator, show existence
}
```
Iterator in Java: hasNext(), next(), remove()
```
public interfact Iterator<AnyType>{
	boolean hasNext();
	AnyType next();
	void remove();
}
```
```
public interface List<AnyType> extends Collection<AnyType>{
	AnyType get(int idx);
	AnyType set(int idx, AnyType newVal);
	void add(int idx, AnyType x);
	void remove(int idx);

	ListIterator<AnyType> listIterator(int pos);
}
```
### ArrayList
* to wrap an array
### Linked List
* the concept, not only in Java
* singly-linked lists and doubly-linked lists
* Nodes have 2 instance variables: data and 'next'(points to next node)
```
Node<AnyType>{
	AnyType data;
	Node<AnyType> next;
}
```
* don't need to store nodes in continuous memory
* to add a node to the end of the linked list: O(n), iterate thru each node to the end of the list
* to add a node to the beginning of the linked list: O(1)
```
t = new LLNode();
t.next = k.next;
k.next = t;
```
* doubly linked list
* sentinal nodes: the first and last of doubly linked lists don't store data
* (null) <- [head] <->[7] <-> [5] <-> [tail] -> (null)
```
addAfter(Node k){
	t = new Node(30);
	t.prev = k;
	t.next = k.next;
	k.next = t;
	t.next.prev = t;
}
```
