# Purpose
Intention is to self learn GraphQL from available resources on internet.

# What is GraphQL
GraphQL is a query language for APIs and a runtime for fulfilling those queries with your existing data. GraphQL provides a complete and understandable description of the data in your API, gives clients the power to ask for exactly what they need and nothing more, makes it easier to evolve APIs over time, and enables powerful developer tools.

## Example
GraphQL is a query language that lets you write queries using an object structure rather than a text string.

So rather than use an SQL query like:
`SELECT name, id, description FROM projects`
Simply describe the object and the fields you’d like from that object you like so:

```
{
  projects {
    id
    name
    description
  }
}
```

###### Resource
[A query language for your API](https://graphql.org/)

[Medium article](https://medium.com/@JeffLombardJr/when-and-why-to-use-graphql-24f6bce4839d)

# Is GraphQL a programming language?
GraphQL is a specification. This means it is an abstract set of rules which can be implemented in any language. This means you can write a GraphQL API in any language, at least any language in which a GraphQL library has been writtern (which at this point is pretty much all of them).

###### Resource
[Detailed Explaination](https://www.quora.com/Is-GraphQL-a-programming-language)

# Why use GraphQL?

## Strongly-typed Schema
All the types (such as Boolean, String, Int, Float, ID, Scalar) supported by the API are specified in the schema in GraphQL Schema Definition Language (SDL), which helps determine the data that is available and the form it exists in. This, consequently, makes GraphQL less error-prone, and more validated, and provides auto-completion for supported IDE/editors.

## No Over-Fetching or Under-Fetching
With GraphQL, developers can fetch only what is required. Nothing less, nothing more. This solves the issues that arise due to over-fetching and under-fetching.

## Saves Time and Bandwidth
GraphQL allows making multiple resources request in a single query call, which saves a lot of time and bandwidth by reducing the number of network round trips to the server. It also helps to save waterfall network requests, where you need to resolve dependent resources on previous requests. For example, consider a blog’s homepage where you need to display multiple widgets, such as recent posts, the most popular posts, categories, and featured posts. With REST architecture, displaying these would take at least five requests, while a similar scenario using GraphQL requires a single GraphQL request.

## Schema Stitching for Combining Schemas
Schema stitching allows combining multiple, different schemas into a single schema. In a microservices architecture, where each microservice handles the business logic and data for a specific domain, this is very useful. Each microservice can define its own GraphQL schema, after which you’d use schema stitching to weave them into one that is accessed by the client.

## Versioning Is Not Required
In REST architecture, developers create new versions (e.g., api.domain.com/v1/, api.domain.com/v2/) due to changes in resources or the request/response structure of the resources over time. Hence, maintaining versions is a common practice. With GraphQL, there is no need to maintain versions. The resource URL or address remains the same. You can add new fields and deprecate older fields. This approach is intuitive as the client receives a deprecation warning when querying a deprecated field.

## Transform Fields and Resolve With Required Shape
A user can define an alias for fields, and each of the fields can be resolved into different values. Consider images transformation API, where a user wants to transform multiple types of images using GraphQL. The query looks like this:

`
query {
            images {
                        title
                        thumbnail: url(transformation: {width: 50, height: 50})
                        original: url,
                        low_quality: url(transformation: {quality: 50})
            file_size
content_type
  }
}`
###### Resource 
[Why GraphQl](https://dzone.com/articles/why-and-when-to-use-graphql-1)

# When to use GraphQl
GraphQL works best for the following scenarios:
1. Apps for devices such as mobile phones, smartwatches, and IoT devices, where bandwidth usage matters.
2. Applications where nested data needs to be fetched in a single call.
   * For example, a blog or social networking platform where posts need to be fetched along with nested comments and commenters details.
   
###### Resource 
[When to use GraphQl](https://dzone.com/articles/why-and-when-to-use-graphql-1)

# Design Pattern that can be implemented using GraphQl

## The Composite Pattern
### What is composite pattern?
Composite pattern is used where we need to treat a group of objects in similar way as a single object. Composite pattern composes objects in term of a tree structure to represent part as well as whole hierarchy. This type of design pattern comes under structural pattern as this pattern creates a tree structure of group of objects.

This pattern creates a class that contains group of its own objects. This class provides ways to modify its group of same objects.

### Usage of pattern with GraphQl
Use when you want to aggregate data from multiple places into one convenient api.

![](https://miro.medium.com/max/1400/1*Zv40o5M183Ejk6bhB25KGw.png "The Composite Pattern Usage")

###### Resource
[composite_pattern](https://www.tutorialspoint.com/design_pattern/composite_pattern.htm)
[Explaination of usage](https://medium.com/@JeffLombardJr/when-and-why-to-use-graphql-24f6bce4839d)
 
## Proxy Pattern
### What is proxy pattern?
The Proxy pattern allows us to create an intermediary that acts as an interface to another resource, while also hiding the underlying complexity of the component.

### Usage of pattern with GraphQl
Use when you want to add functionality to an old api.
![](https://miro.medium.com/max/1400/1*d9FYrp9aGIPTEu4GRqgspQ.png "Proxy pattern Usage")

###### Resource
[proxy pattern explaination](https://www.baeldung.com/java-proxy-pattern)
[Explaination of usage](https://medium.com/@JeffLombardJr/when-and-why-to-use-graphql-24f6bce4839d)

## Facade Pattern
### What is facade pattern?
Facade pattern hides the complexities of the system and provides an interface to the client using which the client can access the system. This type of design pattern comes under structural pattern as this pattern adds an interface to existing system to hide its complexities.

This pattern involves a single class which provides simplified methods required by client and delegates calls to methods of existing system classes.

### Usage of pattern with GraphQl
Use when you want to simplify a complex api.
The difference between a proxy and a facade is simple. Proxies — represents the original, perhaps add some functionality like authentication. Facade — simplifies the original.

![](https://miro.medium.com/max/1400/1*LsjlCJLOC1561MysSVJSTA.png "Facade pattern Usage")

###### Resource
[Facade Pattern explaination](https://www.tutorialspoint.com/design_pattern/facade_pattern.htm)
[Explaination of usage](https://medium.com/@JeffLombardJr/when-and-why-to-use-graphql-24f6bce4839d)

## Multi-Pattern: Combination
It is completely possible to mix and mash these patterns. For example in a composite pattern you might also need to add a facade to an older api.
###### Resource
[Explaination of usage](https://medium.com/@JeffLombardJr/when-and-why-to-use-graphql-24f6bce4839d)

## Anti-Pattern: Do Nothing Proxy
You should not just add GraphQL as a wrapper to your existing API for the sake of doing so. Most of these patterns that are server to server have performance considerations. Instead if you want to provide the exact same access with a different interface, consider developing a web sdk for your clients.
###### Resource
[Explaination of usage](https://medium.com/@JeffLombardJr/when-and-why-to-use-graphql-24f6bce4839d)

# Rest vs GraphQL

![](https://www.altexsoft.com/media/2019/03/word-image-5.png "Rest vs GraphQL")

### Rest Example
![](https://miro.medium.com/max/1400/1*oI0gd6_n6-E9K_NcHgMhUw.png "Rest Example")

### GraphQL Example
![](https://miro.medium.com/max/1400/1*-S7vILUNs2sABozisfBQVw.png "Rest Example")

###### Resource
[Dzone Article](https://dzone.com/articles/graphql-core-features-architecture-pros-and-cons)

[Explaination of usage](https://medium.com/@JeffLombardJr/when-and-why-to-use-graphql-24f6bce4839d)

# GraphQl Primary Concept
1. Query: Read data.
2. Mutation: Write data.
3. Subscription: Observe Event and automatically send data.

