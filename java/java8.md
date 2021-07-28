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

## Difference between ZonedDateTime and LocalDateTime:
Basically, ZonedDateTime allows the user to set the Zone that he wants via ZoneId or default just calling ZonedDateTime, instead LocalDateTime 
gets the time without timezone information.

```java
/* ====ZonedDateTime====
ZonedDateTime - Represents the date/time with its time zone.
ZoneOffset->-03:00 //Difference from Greenwich/UTC. This is usually a fixed number of hours and minutes.
ZoneId-> America/Sao_Paulo */

//Example 1 (ZonedDateTime):
2018-07-18T08:04:14.541-03:00[America/Sao_Paulo]

//Example 2 (Setting a specific zone):
ZonedDateTime zonedDateTime = ZonedDateTime.now(ZoneId.of("America/New_York"));

/* ====LocalDateTime====
According to the Java 8 Documentation, LocalDateTime is an immutable date-time objetct that represents a date-time, without time-zone
in the ISO-8601 calenday system. */

//Example 3 (LocalDateTime):
2018-07-18T08:04:14.

// ====How to convert====

//Example 4 (LocalDateTime to ZonedDateTime)
    
public static void main(String[] args) {
  LocalDateTime localDateTime = LocalDateTime.now();
  ZonedDateTime zonedDateTime = localDateTime.atZone(ZoneId.of("America/Sao_Paulo"));
  System.out.println("zonedDateTime: " + zonedDateTime);
		
    //or
		
  ZonedDateTime zonedDateTime2 = Instant.now().atZone(ZoneId.of("America/Sao_Paulo));
	System.out.println("zonedDateTime2: " + zonedDateTime2);
  }
  ```
