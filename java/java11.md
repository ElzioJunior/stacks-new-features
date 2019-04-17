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