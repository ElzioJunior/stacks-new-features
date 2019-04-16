# Java 8 NEW Features


## Lambda Functions <br>
```java
array.forEach(item -> Syso(item));
```


## Optional <br>
```java
// Bye bye repositories NullPointerExceptions ;)
> Optional<Foo> fooResponse = repository.findById(id);

if (!fooResponse.isPresent()) throw new NotFoundException(“Entidade não existe”);

Foo foo = fooResponse.get();
doSomething(foo);
```

## Method reference 
```java
array.forEach(System.out::println);
// note that :: calls println with the argument passed on forEach

Person p1 = new Person();
p1.name = "bar";

Person p2 = new Person();
p2.name = "foo";

List<Person> personList = Arrays.asList(p1, p2);
List<String> nameList = personList.stream().map(Person::getName).collect(Collectors.toList());
// nameList: [“bar”, “foo”];
```

## Streams API 
```java
List<String> list = Arrays.asList("bbb", "aaa", "xxx", "ccc");
List<String> sortedList = list.stream().sorted().collect(Collectors.toList());
// sortedList: [“aaa”, “bbb”, “ccc”, “xxx”];
```

## Date/Time API
```java
LocalDateTime dateTime = LocalDateTime.now();
```

## ...