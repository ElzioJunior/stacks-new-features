# Java 11 NEW Features

##  Local-Variable Syntax for Lambda Parameters
```java
list.stream()
    .map((@Notnull var s) -> s.toLowerCase())
    .collect(Collectors.toList());
```

## OracleJDK and OpenJDK is in the same level of features
Now oracle get some OracleJdk features and transform than into open-souce features. Then they put the openJdk at the same level of features.<br>
<img src="features%20openJdk%2011%20same%20level%20oracleJdk.png" />
<br>
Some of this closed-sources that are now open-sources features:
- Flight Recorder (https://openjdk.java.net/jeps/328)
- Mission Control (https://openjdk.java.net/projects/jmc/7/)

## HTTP Client (Standard)
Module: java.net.http

The main types defined are

- HttpClient
- HttpRequest
- HttpResponse
- WebSocket
The API can be used synchronously or asynchronously. Asynchronous mode makes use of CompletableFutures and CompletionStages.

## Predicate Not
Now you can convert this code:
```java
lines.stream()
    .filter(s -> !s.isBlank())
``` 

to

```java
lines.stream()
    .filter(Predicate.not(String::isBlank))
```

## String new methods
- **boolean isBlank()** <br>
    Returns true if the string is empty or contains only white space codepoints, otherwise false.
- **Stream lines()** <br>
    Returns a stream of lines extracted from this string, separated by line terminators: \n or \r or \r\n)
    ```java
        String s1 = "FirstLine\nSecondLine\rLastLine";;
        List lines = s1.lines().collect(Collectors.toList());
        // lines.size() -> 3
        System.out.println(lines); 
        // prints out:
        // [FirstLine, SecondLine, LastLine]
    ```
- **String repeat(int)** <br>
    Returns a string whose value is the concatenation of this string repeated count times.
- **String strip()** <br>
    Returns a string whose value is this string, with all leading and trailing whitespace removed.
- **String stripLeading()** <br>
    Returns a string whose value is this string, with all leading whitespace removed.
- **String stripTrailing()** <br>
    Returns a string whose value is this string, with all trailing whitespace removed.

##  Single-File Source-Code Launch
JEP 330 eliminates the **need to compile** a single-file application. So, imagine that you have a code like this:
```java
public class WriteLog {
    public static void main(String[] args) {
	    System.out.println(args[0]);
    }
}
```

Then with this feature now you can run your application without compiling, just typing:
> java -classpath /home/foo/java WriteLog.java ArgumentsTest
```java
// prints out:
// ArgumentsTest
```

# ...
