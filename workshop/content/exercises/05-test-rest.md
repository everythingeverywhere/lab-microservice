Now that the service is up, try your service:

```execute-2
curl http://localhost:8080/greeting
```

You should see:

``` 
{"id":1,"content":"Hello, World!"}
```

Provide a name query string parameter by visiting 

```execute-2
curl http://localhost:8080/greeting?name=User
```
Notice how the value of the `content` attribute changes from `Hello, World!` to `Hello, User!`, as the following listing shows:

```
{"id":2,"content":"Hello, User!"}
```
This change demonstrates that the `@RequestParam` arrangement in `GreetingController` is working as expected. The `name` parameter has been given a default value of `World` but can be explicitly overridden through the query string.

Notice also how the `id` attribute has changed from `1` to `2`. This proves that you are working against the same `GreetingController` instance across multiple requests and that its counter field is being incremented on each call as expected.