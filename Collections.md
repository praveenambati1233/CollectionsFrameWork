# CollectionsFrameWork
Theoretical and Practical explanation of all the topics in CFW.





**HashMap**

- A HashMap cannot contain duplicate keys.
- Java HashMap allows null values and the null key.
- HashMap is an unordered collection. It does not guarantee any specific order of the elements.
- Java HashMap is not thread-safe. You must explicitly synchronize         concurrent modifications to the HashMap.
- They are designed for easy retrieval


**Accessing keys and modifying their associated value in a HashMap
The example below shows:**

- How to check if a HashMap is empty | isEmpty()
- How to find the size of a HashMap | size()
- How to check if a given key exists in a HashMap | containsKey()
- How to check if a given value exists in a HashMap | containsValue()
- How to get the value associated with a given key in the HashMap | get()
- How to modify the value associated with a given key in the HashMap | put()
- Remove a key from a HashMap | remove(Object key)
- Remove a key from a HashMap only if it is associated with a given value | remove(Object key, Object value)
- entrySet  (prints k, v ) , entryKey (prints only keys ),  values ( print only key values)

**Iterating over a HashMap**





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


------------

**-  Get new records from two list**

> list 1 = [1234,1235]
list 1 = [1234,1236,1237]
output = [1236,1237]


```java
public class NewRecords {

	public static void main(String[] args) {

		// Setting DB records
		List<TelePhoneNumbers> lnpRecordsFromDB = new ArrayList<>();
		TelePhoneNumbers tn1= new TelePhoneNumbers();
		TelePhoneNumbers tn2= new TelePhoneNumbers();
		tn1.setTn(1234);
		tn2.setTn(1235);
		lnpRecordsFromDB.add(tn1);
		lnpRecordsFromDB.add(tn2);
		
		List<TelePhoneNumbers> lnpRecordsFromRequest = new ArrayList<>();
		TelePhoneNumbers tn3= new TelePhoneNumbers();
		TelePhoneNumbers tn4= new TelePhoneNumbers();
		TelePhoneNumbers tn5= new TelePhoneNumbers();
		tn3.setTn(1234);
		tn4.setTn(1237);
		tn5.setTn(1236);
		lnpRecordsFromRequest.add(tn3);
		lnpRecordsFromRequest.add(tn4);
		lnpRecordsFromRequest.add(tn5);

		List<TelePhoneNumbers> newTns= getNewTns(lnpRecordsFromDB , lnpRecordsFromRequest);
		newTns.forEach(Tns -> System.out.println(Tns));
	}

	private static List<TelePhoneNumbers> getNewTns(List<TelePhoneNumbers> lnpRecordsFromDB,
			List<TelePhoneNumbers> lnpRecordsFromRequest) {
		
		List<TelePhoneNumbers> newTNs = new ArrayList<>();	
		Map<Integer, TelePhoneNumbers> dbMap = buildTelePhoneMapByTn(lnpRecordsFromDB);
		Map<Integer, TelePhoneNumbers> requestMap = buildTelePhoneMapByTn(lnpRecordsFromRequest);
		
		for (Entry<Integer, TelePhoneNumbers>  entrySet : requestMap.entrySet()) {
			if(!dbMap.containsKey(entrySet.getKey())){
					newTNs.add(entrySet.getValue());
				}
			}
			return newTNs;
	}

	private static Map<Integer, TelePhoneNumbers> buildTelePhoneMapByTn(List<TelePhoneNumbers> lnpRecordsFromDB) {
		
		Map<Integer, TelePhoneNumbers>  map = new HashMap<>();
		for (TelePhoneNumbers telePhoneNumbers : lnpRecordsFromDB) {
			map.put(telePhoneNumbers.getTn(), telePhoneNumbers);
		}
		return map;
	}
}
```





