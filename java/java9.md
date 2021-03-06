# Java 9 NEW Features

## The Clean Up Starts
Since Java 1.1 **A LOT OF** features were being **@Deprecated**, BUT, none of them were **removed**!
<br>This is the main cause of simples applications, writed in Java, are so heavy.
<br>So, Clean Up is a new strategy for remove @Deprecated and non-used things, for each release of Java, starting in 9...

##  Modules - Project JigSaw 

```java
/* 
Create a module-info into your project home directory

src
|_ com.elziojr.myproject 
    |_ module-info.java    -> declare module file here
    |_ com
        |_elziojr
            |_ myproject
                |_ HelloWorld.java
target
*/
```
module-info.java
```java
module com.elziojr.myproject {
    requires java.base;
}
```

## Linking
Link module dependencies with another modules to create a minimal runtime /environment 
<br>

## Collection factory methods 
```java
Set<Integer> ints = Set.of(1, 2, 3);
List<String> strings = List.of("first", "second");
```


## Stream API improvements
- takeWhile
```java
Stream.of(2, 4, 6, 8, 9, 10, 12)
    .takeWhile(n -> n % 2 == 0)
    .forEach(System.out::print);

// prints out:
// 2 4 6 8
```

- dropWhile (the oposite function)
```java
Stream.of(2, 4, 6, 8, 9, 10, 12)
    .dropWhile(n -> n % 2 == 0)
    .forEach(System.out::print);

// prints out:
// 9 10 12
```

Take care with **takeWhile** and **dropWhile** methods, it only get and ordered list if the original set is ordered.<br>
My tip is **always order the set before**, this give some **performace improvement** too <3 

- ofNullable

```java
// This is very usefull if you have a stream that can have nullables,
// and if you need to make something that can throw NullPointer
// - This list then skip nullable values
Stream.ofNullable([1, 2, null, 3, 4])
    .forEach(System.out::print);

// prints out:
// 1 2 3 4
```


## JShell 
```java
// this feature is a shell executor for java
1
2
➜  ~ jshell
|  Welcome to JShell -- Version 9
|  For an introduction type: /help intro
 
jshell>System.out.println(“foo bar”);
-> “foo bar”
```

# ...
