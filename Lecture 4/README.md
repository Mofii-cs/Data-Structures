## COMS3134 - Lecture 4

### Web HP - 12C
```
1	3 5 + => 3+5
2	3 5 + 2 * => (3+5)*2
3	3 5 2 + * => 3 (5 2 +) * => 3*(5+2)
```
* it is actually a 'stack' algorithm; here we only use binary operators
* pop the answer out and check if the stack is empty

### Queue
* a FIFO data structure - first in first out
* ADT: size, isEmpty, isFull, enqueue (offer), dequeue (poll)
```
enqueue 54: [54][  ][  ][  ][  ]
enqueue 66: [54][66][  ][  ][  ]
enqueue 77: [54][66][77][  ][  ]
dequeue:    [  ][66][77][  ][  ]
```
* head / tail: mod length
* 'Queue' is a fixed length array
* Application of Queue:
```
n people standing in a circle, counting numbers from A in the clockwise order. Any guy who counts k gets kicked out. Who is the last guy standing?
```
```
import java.util.LinkedList;
import java.util.Queue;
public class Josephus{
	
	public static final void main(String[] args){

		int count = S;
		Queue<Integer> q = new LinkedList<Integer>();
		// for q, only methods from Queue interface can be invoked

		for (int i = 0; i < 10; i ++){
			q.offer(i);
		}

		int c = 0;

		while (q.size() != 1){
			int x = q.poll();
			c ++;

			if (c == 5){
				System.out.println("So long: " + x);
				c = 0;
			} else {
				q.offer(x);
			}
		}

		System.out.println("Winner is " + );

	}

}
```

### Tree
* Linked list is a tree, just a special case.
* There are no cycles within a tree.
* **Root**: top-level node
* **Child-node**: Child-parent relation
* **Sibling**: nodes of the same parent
* **Leaf-nodes**: nodes with no children
* **Interior-nodes**: nodes with child(ren)
* **Path**: only thru parent-to-child edges
* **Length of the path**: how many edges
* **Depth of a node**: length of the unique path back to the root
* **Height of a node**: length of the path from the given node to the furtherest leaf
```
class TreeNode<E>{
	
	E data;

	TreeNode<E> nextSibling;
	TreeNode<E> firstChild;

}
```
* Application of Tree: File system
* Pseudocode to list a directory in a hierarchincal file system
```
private void listAll(int depth){
	printName(depth); // print the name of the object
	if(isDirectory()){
		for each file c in this directory
			c.listAll(depth + 1);
	}
}
public void listAll(){
	listAll(0);
}
```
```
Print out:
/usr
	mark
		book
			ch1.r
			ch2.r
			ch3.r
		course
			cop3530
				fall
					sy1.r
				spr
					sy2.r
	tom
		...
```
### Binary Tree
* In which, each node only have 0, 1, or 2 children.
* **Left-child** and **Right-child**
```
class BTNode<E>{
	E data;
	BTNode<E> left;
	BTNode<E> right;
}
```
* Full: Every node has either 2 children or is a leaf
* Complete: Every level is filled from left to right
* Perfect: Every level is 'full'
### Expression Tree
* Assuming all the operators are binary
* **operator nodes**: 2 children or no children
* **operand nodes**
```
+-
	-4
	-3
```
```
+-
	-4
	-*-
		-2
		-5
```
```
int eval(ETNode t){
	if (t.isOperand()){
		return t.value;
	} else {
		int lval = eval(t.left);
		int rval = eval(t.right);
		return apply(t.operator, lval, rval);
	}
}
```
* post-order / pre-order
* recurse left - print - recurse right - recurse left - ...

### Build an Expression Tree (Constructor)
```
4 3 2 + *
```
* To build an Expression Tree:
	1. build a stack of Expression Nodes
	2. Add operands in
	3. When it comes an operator, pop the first node as its right node and second one as its left node
	4. Recursively
	5. The last node left in the stack is the root node
