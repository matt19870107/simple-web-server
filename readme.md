# Simple Web Server
![Coverage](.github/badges/jacoco.svg)

![Branches](.github/badges/branches.svg)

A simplex HTTP 1.0 Server implemented in Java for educational
purposes based on W3C specifications (http://www.w3.org/Protocols/):

* [W3](https://www.w3.org/Protocols/HTTP/AsImplemented.html) Hypertext Transfer Protocol -- HTTP/0.9
* [RFC 1945](http://www.ietf.org/rfc/rfc1945.txt) Hypertext Transfer Protocol -- HTTP/1.0
* [RFC 2616](http://www.ietf.org/rfc/rfc2616.txt) Hypertext Transfer Protocol -- HTTP/1.1
* [RFC 2617](http://www.ietf.org/rfc/rfc2617.txt) HTTP Authentication: Basic and Digest Access Authentication
* [RFC 6265](http://tools.ietf.org/html/rfc6265) HTTP State Management Mechanism (Cookies)

## Build
```
./gradlew jar 
```

## Run
```
java -cp build/libs/simple-web-server-1.0.jar liteweb.Server
```

## Performance test
```
bzt performance.yml
```

```
The provided code snippet appears to handle an incoming client request in a server application. While it looks generally correct, there are a few potential performance issues you could consider:

1. BufferedReader Performance: Creating a new BufferedReader instance for every client request might be inefficient. Consider creating a single BufferedReader instance outside the `handle` method and reusing it for multiple requests, as long as it doesn't introduce thread-safety issues.

2. ArrayList Resizing: The `requestContent` ArrayList is used to store the lines of the incoming request. However, ArrayList resizing can be costly if the number of lines is large. If you have an estimate of the request size, you can initialize the ArrayList with an initial capacity to avoid frequent resizing.

3. String Concatenation: Instead of concatenating strings using the `+` operator, which creates new string objects, consider using StringBuilder or StringBuffer for more efficient string concatenation, especially if there are many lines in the request.

4. Error Logging: The current code logs an error when an IOException occurs. While this is important for error handling, logging can impact performance. Consider using a logging framework that allows you to control the log level and choose an appropriate level for error logging.

These are just a few potential areas for performance improvement based on the provided code snippet. It's important to profile and benchmark your application to identify the actual performance bottlenecks and focus on optimizing the critical parts.
```


