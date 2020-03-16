### Comparable 

- Belongs to java.lang package.
- compareTo(Object o) has to be implemented.
- Should provide object storting based on ordering such as ascending / decending. 
- Logical Difference - Comparable Interface compares "this" reference 
- Comparable in Java is used to implement natural ordering of object. In Java API **String, Date** and **wrapper classes** implements Comparable interface.Its always good practice to override compareTo() for value objects. As below 

```java
List<Integer> intList = new ArrayList<>();
intList.add(12);
intList.add(13);
intList.add(1);
intList.add(2);
intList.add(9);
//compareTo is implemented in Integer
Collections.sort(intList);		
intList.forEach(e -> System.out.println(e));


// code in Interger class

public int compareTo(Integer anotherInteger) {
        return compare(this.value, anotherInteger.value);
 }

public static int compare(int x, int y) {
        return (x < y) ? -1 : ((x == y) ? 0 : 1);
    }


```

####  e1.compareTo(e2)

- should return Negative integer (if e1 < e2), 0 (if e1 = e2), Positive integer (if e1 > e2)
- It should throw ClassCastException if object types of e1 and e2 are not comparable
- It should throw NullPointerException if e2 passed is null

Key points :

>-  If any class implement Comparable interface in Java then collection of that object either List or Array can be sorted automatically by using  Collections.sort() or Arrays.sort() method and object will be sorted based on there natural order defined by CompareTo method.
- for use defined object we need to implement CompareTo based on the order that user required. ( example below )


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

*You may be wondering why I didn't write that logic? Because getNameis  string, I have called the compareTo() method of string class, which does exactly the same.

However if the things we are comparing are of other type such as int then you can write the logic like this:
Lets say object of Employee class is (empId, empName, empAge) and we want to sort the objects by empAge.

*

```java
public int compareTo(Employee e){  
   if(this.empAge==e.empAge)  
      return 0;  
   else if(this.empAge>e.empAge)  
      return 1;  
   else  
      return -1;  
}
or

public int compareTo(Employee e){  
return this.empAge > e.empAge ? 1 : this.empAge < e.empAge ? -1 : 0;
}
```






