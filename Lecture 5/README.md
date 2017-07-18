## Data Structures and Algorithm Analysis - Lecture 5
### Implementation of Expression Tree
	```
	// ExpressionTree class

	public class ExpressionTree{

		public ExpressionTree(String expression){

			// here we write our stack based method
			// for building an expression tree
			// when we pop off the final node after
			// processing all tokens, set root equal
			// to that node

		}

		public int eval(){
			return eval(root);
		}

		private int eval(Node t){

		}

		private static class Node{
			Node left;
			Node right;

			char operator;
			int operand;

			boolean isOperator;
		}

		Node root = null;

	}
	```
	```
	// ExpressionTester class

	public class ExpressionTester{
		public static final void main(String[] args){

			Expressiontree tree = new ExpressionTree("35 6 2 + -");

			System.out.println(tree.eval());

		}
	}
	```

### BinarySearchTree

* Binary tree of height h, the number of leaves is at most 2<sup>h</sup>
	1. base case: h = 0, 1 = 2<sup>0</sup>
	2. assume all perfect binary trees of height **n**, where 0 < n < h have 2<sup>n</sup> nodes
	3. by adding a 'root' node at the top of two height h trees, we know that the number of leaves of a height h+1 tree is at most 2<sup>h</sup> + 2<sup>h</sup> = 2<sup>h+1</sup>

* Total nodes in perfect binary tree of height h is 2<sup>h+1</sup> - 1
	1. base case: h = 0, 1 = 2<sup>0+1</sup> - 1
	2. assume true for heights 0 to h
	3. by adding a 'root' node at the top of two heigth h trees, we know that the number of nodes of a height h tree is 2<sup>h+1</sup> - 1 + 2<sup>h+1</sup> - 1 + 1 = 2<sup>h+2</sup>

* Binary Search Trees (BSTs)
	1. BST constraints: Any node in the left sub-tree must be smaller, while any mode in the right sub-tree must be larger. (implement Comparable) No duplicates.
	2. insert(): define the method in a recursive way
	3. search(): define the method in a recursive way
	4. remove(): search for the node and remove the node:
		if no children: just remove
		if only one child: remove the node and fix the reference
		if two children: substitute the 'sub-root' with the largest of the right sub-tree (or the smallest of the left sub-tree)
	5. findMin()
	6. findMax()

	```
	BinarySearchTree.java
	```
	'height = -1'

* Lazy Deletion: we don't actually delete an item, instean we add an attribute to the item: 'active', such that element with 'false' in 'active' is regarded as deleted. However, this way makes findMax() and findMin() really hard

* Self-balancing binary search trees (AVL trees)
	1. AVL congition / balance condition: for every node, the height of the left sub-tree cannot differ from the right sub-tree by more than 1 (or smaller than -1)
	2. store the height of a node
	3. When there is an inbalance, there are four situations:
		Zig-zig (left-left): single rotation
		Zig-zag (left-right): double rotation, rotate to zig-zig situation
		Zag-zig (right-left): double rotation, rotate to zag-zag situation
		Zag-zag (right-right): single rotation
	4. triangles of height n and triangles of height n+1 used to describe the general scenario
