<center>
  <img src="https://i.imgur.com/No1RPUf.png" width="80%"/>
</center>

## What is Manifold?
[Manifold](http://manifold.systems) is a new breed of Java tooling. It provides powerful features to make 
Java development more appealing and productive. Simply add the Manifold jar to your project and begin taking advantage 
of it.

## What can you do with Manifold?

### [Meta-programming](http://manifold.systems/docs.html#manifold-in-a-nutshell)
Gain direct, type-safe access to <i>any</i> type of data, such as JSON Schema and YAML. Remove the code gen step in your build process.
```java 
// Access your User.json file directly as a type, no code gen!
User user = User.load().fromJsonUrl("http://api.example.com/users/$userId");
user.setName("Scott");
user.post().toJsonUrl("http://api.example.com/post/user");
```

### [Extensions](http://manifold.systems/docs.html#the-extension-manifold)
Add extension methods to existing Java classes, even String, List, and File. Eliminate boilerplate code. [Check it out!](http://manifold.systems/images/ExtensionMethod.mp4)
```java
String greeting = "hello";
greeting.myMethod(); // Add your own methods to String!
```  

### [Structural Typing](http://manifold.systems/docs.html#structural-interfaces)
Unify disparate APIs. Bridge software components you do not control. Access maps through type-safe interfaces.
```java
Map<String, Object> map = new HashMap<>();
MyThingInterface thing = (MyThingInterface) map; // O_o
thing.setFoo(new Foo());
Foo foo = thing.getFoo();
out.println(thing.getClass()); // prints "java.util.HashMap"
```
 
### [Type-safe Reflection](http://manifold.systems/docs.html#type-safe-reflection)
Access private features with <b>@Jailbreak</b> to avoid the drudgery and vulnerability of Java reflection.
```java
@Jailbreak Foo foo = new Foo();
// Direct, *type-safe* access to *all* foo's members
foo.privateMethod(x, y, z); 
foo.privateField = value;
```

### [String Templates](http://manifold.systems/docs.html#templating) (aka String Interpolation)
Embed variables and expressions in String literals, no more clunky string concat!
```java
int hour = 15;
// Simple variable access with '$'
String result = "The hour is $hour"; // Yes!!!
// Use expressions with '${}'
result = "It is ${hour > 12 ? hour-12 : hour} o'clock";
``` 
       
### [Template Files with *ManTL*](http://manifold.systems/manifold-templates.html)
Author template files with the full expressive power of Java, use your templates directly in your code as types.
```java
List<User> users = ...;
String content = abc.example.UserSample.render(users);
```
A tempate file `abc/example/UserSample.html.mtl`
```html
<%@ import java.util.List %>
<%@ import com.example.User %>
<%@ params(List<User> users) %>
<html lang="en">
<body>
<% users.stream()
   .filter(user -> user.getDateOfBirth() != null)
   .forEach(user -> { %>
    User: ${user.getName()} <br>
    DOB: ${user.getDateOfBirth()} <br>
<% }); %>
</body>
</html>
```

### [Libraries](http://manifold.systems/docs.html#extension-libraries)
Leverage stock Manifold extension libraries for standard Java classes. Save time and reduce boilerplate code.
```java
File file = new File(path);
// Use refreshing extensions to File
String content = file.readText();
```  

### [IntelliJ](http://manifold.systems/docs.html#working-with-intellij)
Use the Manifold IntelliJ IDEA plugin to fully leverage Manifold in your development cycle. The plugin provides 
comprehensive support for IntelliJ features including code completion, navigation, usage searching, refactoring, 
incremental compilation, hotswap debugging, full-featured template editing, and more.

### [Learn More](http://manifold.systems/docs.html)
