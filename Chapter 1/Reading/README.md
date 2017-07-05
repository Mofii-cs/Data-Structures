## Big Java - Chapeter 18 Generic Classes
### Generic Classes and Type Parameters
* Generic Programming can be archieved with inheritance or with type parameters.
* Type parameters can be instantiated with class or interface types.
* Cannot substitute any of the eight primitive types for a type parameter. Use wrapper classes instead.
### Implementing Generic Types
```
1   public class Pair<T, S>{
2     	private T first;
3   	private S second;
4   	public Pair(T firstElement, S secondElement){
5	        first = firstElement;
6	        second = secondElement;
7       }
8   	public T getFirst(){ return first; }
9       public S getSecond(){ return second; }
10  }
```
* Is is considered good form to use short uppercase names for type variables, such as those in the following table:
|Type Variable|Meaning|
| --- | --- |
|E|Element type in a collection|
|K|Key type in a map|
|V|Value type in a map|
|T|General type|
|S, U|Additional general types|
### Generic Methods
* A generic method is a method with a type parameter. Such a method can occur in a class that in itself is not generic.
```
1   public static <E> String toString(ArrayList<E> a){
2   	String result = "";
3   	for (E e : a){
4   	    result = result + e + " ";
5   	}
6   	return result;
7   }
```
* When calling a generic method, you need not instantiate the type parameters.
```
1   Rectangle[] rectangles = ...;
2   ArrayUtil.print(rectangles);
```
* Cannot replace type parameters with primitive types.
### Constructing Type Parameters
* Type parameters can be constrained with bounds.
```
1   public interface Measurable{
2   	double getMeasure();
3   }
4
5   public static <E extends Measureble> double average(ArrayList<E> objects){
6   	if (object.size() == 0){ return 0; }
7       double sum = 0;
8       for (E obj : objects){
9           sum = sum + obj.getMeasure();
10      }
11      return sum / object.size();
12  }
```
* This means "E or one of its superclasses extends or implements Measurable". In this situation, we say that E is a subtype of the Measurable type.
* If two or more bounds supplied, use '&': <E extends Comparable<E> & Measurable>
### Type Erasure
