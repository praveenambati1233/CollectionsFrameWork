# CollectionsFrameWork
Theoretical and Practical explanation of all the topics in CFW.





**HashMap**

- They are designed for easy retrieval


**Examples :**

1. sort by comparing values in the HashMap

```java
public class SortHashMapValues {

	public static void main(String[] args) {

		Map<String, Person > map = new HashMap<>();
		
		Person p1 = new Person("Jim", 23);
		Person p2 = new Person("Jimesh", 63);
		Person p3 = new Person("Zinhd", 53);
		Person p4 = new Person("Varun", 43);
		
		map.put(p1.getName(), p1);
		map.put(p2.getName(), p2);
		map.put(p3.getName(), p3);
		map.put(p4.getName(), p4);
		
		List<Person> list = new ArrayList<Person>(map.values());
		
		// Easy way to write 
//		Collections.sort(list, Comparator.comparing(Person::getAge));
		
		Collections.sort(list, new Comparator<Person>() {

			@Override
			public int compare(Person o1, Person o2) {
				
				int compare = o1.getAge() > o2.getAge() ? 1 :  o1.getAge() < o2.getAge() ? -1 : 0;
				return compare;
			}
		});
		
		list.forEach(e -> System.out.println(e));
		
	}

}

```

