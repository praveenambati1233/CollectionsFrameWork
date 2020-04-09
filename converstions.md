Convert immutable to mutable ( changeable)

```java
private List<Topic> topics = Arrays.asList(new Topic("Spring", "spring Fw", "new course"),new Topic("java", "Java 1.8", "basic course");

topics.add(topic); // Throws unsupportedOperationException - As Array.asList is having immutable objects. 
```

to convert immutable to mutable , we can do as follows

```java
private List<Topic> topics = new ArrayList<>(Arrays.asList(new Topic("Spring", "spring Fw", "new course"),new Topic("java", "Java 1.8", "basic course"));
```

Another Example:
```java
final List<someDTO> mutableList = new ArrayList<>(someDTO.getImmutableList());
```


