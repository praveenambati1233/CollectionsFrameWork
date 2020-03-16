### Comparable 

- Belongs to java.lang package.
- compareTo(Object o) has to be implemented.
- Should provide object storting based on ordering such as ascending / decending. 
- Logical Difference - Comparable Interface compares "this" reference 
- Comparable in Java is used to implement natural ordering of object. In Java API **String, Date** and **wrapper classes** implements Comparable interface.Its always good practice to override compareTo() for value objects.

####  e1.compareTo(e2)

- should return Negative integer (if e1 < e2), 0 (if e1 = e2), Positive integer (if e1 > e2)
- It should throw ClassCastException if object types of e1 and e2 are not comparable
- It should throw NullPointerException if e2 passed is null

Key points :

>-  If any class implement Comparable interface in Java then collection of that object either List or Array can be sorted automatically by using  Collections.sort() or Arrays.sort() method and object will be sorted based on there natural order defined by CompareTo method.


```java
public int compareTo(Employee o) {
  if(o == null){
   throw new NullPointerException("compareTo: Argument passed is null");
  }
  if(this.getClass().equals(o.getClass())){
   Employee e = (Employee) o;
   return this.getName().compareTo(e.getName());
  }else{
   throw new ClassCastException("compareTo: Objects are not comparable");
  }
 }
```
