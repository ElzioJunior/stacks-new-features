# Java 11 NEW Features

##  Local-Variable Syntax for Lambda Parameters
```java
list.stream()
    .map((@Notnull var s) -> s.toLowerCase())
    .collect(Collectors.toList());
```

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