## Data Structures and Algorithm Analysis - Chapter 3
### Abstract Data Types (ADTs)
* An abstract data type (ADT) is a set of objects together with a set of operations.
* Objects such as lists, sets, and graphs, along with their operaions, can be viewed as abstract data types, just as integers, reals, and booleans are data types.
### The List ADT
* For any list except the empty list, we say that A<sub>i</sub> follows (or succeeds) A<sub>i-1</sub> (i < N) and that A<sub>i-1</sub> precedes A<sub>i</sub> (i > 0). suuccessor / predecessor
### Simple Array Implementation of Lists
* Insertion: O(N), not efficient
### Simple Linked Lists
* The linked list consists of a series of nodes, which are not necessarily adjacent in memory.
* Each node contains the element and a link to a node containing its successor. We call this the <I>next</I> link. The last cell's <I>next</I> link references <I>null</I>.
* printList or find(x): O(N)
* findKth(i): O(N), less efficient
* In principle, if we know where a change is to be made, inserting or removing an item from a linked list does not require moving lots of items and instead involves only a constant number of changes to node links.
### Doubly Linked Lists
### Iterator s
* Collections that implement the Iterable interface must provide a method named iterator that returns an object of type iterator. The iterator is an interface defined in package java.util.
```
Iterator interface
1	package java.util;
2	public interface Iterator<E>{
3		boolean hasNext();
4		E next();
5		void remove();
6	}
```
```
Collection interface
	public interface Collection<AnyType> extends Iterable<AnyType>{
		int size();
		boolean isEmpty();
		void clear();
		boolean contains(AnyType x);
		boolean add(AnyType x);
		boolean remove(AnyType x);
		java.util.Iterator<AnyType> iterator();
	}
```
* When the compiler sees an enhanced for loop being used on an object that is Iterable, it mechanically replaces the enhanced for loop with calls to the iterator method to obtain an Iterator and then calls to next and hasNext. Thus the print routine is rewritten by the compiler.
```
print_1
1	public static <AnyType> void print(Collection<AnyType> coll){
2		for (AnyType item : coll){
3			System.out.println(item);
4		}
5	}
```
```
print_2
1	public static <AnyType> void print(Collection<AnyType> coll){
2		Iterator<AnyType> itr = coll.iterator();
3		while(itr.haxNext()){
4			AnyType item = itr.next();
5			System.out.println(item);
6		}
7	}
```
* If you make a stuctural change to the collection being iterated, then the iterator is no longer valid, and a ConcurrentModificationException is thrown. This is necessary to avoid ugly situations in which the iterator is prepared to give a certain item as the next item, and then that item is either removed, or perhaps a new item is inserted just prior to the need to use it. However, if the iterator invokes its remove method, then the iterator is still valid.
### Implementation of ArrayList

[MyArrayList.java](../Chapter 3/MyArrayList.java)
