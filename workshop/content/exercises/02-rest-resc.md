Now that you have set up the project and build system, you can create your web service.

Begin the process by thinking about service interactions.

The service will handle `GET` requests for `/greeting`, optionally with a `name` parameter in the query string. The `GET` request should return a `200 OK` response with JSON in the body that represents a greeting. It should resemble the following output:

```
{
    "id": 1,
    "content": "Hello, World!"
}
```

The `id` field is a unique identifier for the greeting, and `content` is the textual representation of the greeting.

To model the greeting representation, create a **Resource Representation Class**. To do so, provide a plain old Java object with fields, constructors, and accessors for the `id` and `content` data, as the following listing (from `src/main/java/com/example/restservice/Greeting.java` ) shows:

```execute-1
touch ~/gs-rest-service/initial/src/main/java/com/example/restservice/Greeting.java
```

Open the file in the text editor:

```editor:open-file
file: ~/gs-rest-service/initial/src/main/java/com/example/restservice/Greeting.java
```


```editor:append-lines-to-file
file: ~/gs-rest-service/initial/src/main/java/com/example/restservice/Greeting.java
text: |
package com.example.restservice;

public class Greeting {

	private final long id;
	private final String content;

	public Greeting(long id, String content) {
		this.id = id;
		this.content = content;
	}

	public long getId() {
		return id;
	}

	public String getContent() {
		return content;
	}
}
```

> This application uses the [Jackson JSON](https://github.com/FasterXML/jackson) library to automatically marshal instances of type `Greeting` into JSON. Jackson is included by default by the web starter.