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

[Latest spec](http://spec.graphql.org/)

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

```
query {
            images {
                        title
                        thumbnail: url(transformation: {width: 50, height: 50})
                        original: url,
                        low_quality: url(transformation: {quality: 50})
                        file_size
                        content_type
                   }
}
```

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
1. **Query:** are used by the client to request the data it needs from the server.
2. **Mutation:** is the key. In GraphQL, mutations are used to CUD
  * Create new data
  * Update existing data
  * Delete existing data
3. **Subscription:**  are a way to create and maintain real time connection to the server. This enables the client to get immediate information about related events. Basically, a client subscribes to an event in the server, and whenever that event is called, the server will send the corresponding data to the client.

## Types

### Scalar Types
GraphQL comes with a set of default scalar types out of the box:

1. **Int:** A signed 32‐bit integer.
2. **Float:** A signed double-precision floating-point value.
3. **String:** A UTF‐8 character sequence.
4. **Boolean:** true or false.
5. **ID:** The ID scalar type represents a unique identifier, often used to refetch an object or as the key for a cache. The ID type is serialized in the same way as a String; however, defining it as an ID signifies that it is not intended to be human‐readable.

### Enumeration types
Also called Enums, enumeration types are a special kind of scalar that is restricted to a particular set of allowed values. This allows you to:

Validate that any arguments of this type are one of the allowed values
Communicate through the type system that a field will always be one of a finite set of values
Here's what an enum definition might look like in the GraphQL schema language:

```
enum Episode {
  NEWHOPE
  EMPIRE
  JEDI
}
```
This means that wherever we use the type Episode in our schema, we expect it to be exactly one of NEWHOPE, EMPIRE, or JEDI.

### Object types and fields
The most basic components of a GraphQL schema are object types, which just represent a kind of object you can fetch from your service, and what fields it has. In the GraphQL schema language, we might represent it like this:

```
type Character {
  name: String!
  appearsIn: [Episode!]!
}
```

The language is pretty readable, but let's go over it so that we can have a shared vocabulary:

1. **Character** is a GraphQL Object Type, meaning it's a type with some fields. Most of the types in your schema will be object types.
2. **name** and appearsIn are fields on the Character type. That means that name and appearsIn are the only fields that can appear in any part of a GraphQL query that operates on the Character type.
3. **String** is one of the built-in scalar types - these are types that resolve to a single scalar object, and can't have sub-selections in the query. We'll go over scalar types more later.
4. **String!** means that the field is non-nullable, meaning that the GraphQL service promises to always give you a value when you query this field. In the type language, we'll represent those with an exclamation mark.
5. **[Episode!]!** represents an array of Episode objects. Since it is also non-nullable, you can always expect an array (with zero or more items) when you query the appearsIn field. And since Episode! is also non-nullable, you can always expect every item of the array to be an Episode object.

### Arguments
Every field on a GraphQL object type can have zero or more arguments, for example the length field below:
```
type Starship {
  id: ID!
  name: String!
  length(unit: LengthUnit = METER): Float
}
```

**NOTE:** All arguments are named. Unlike languages like JavaScript and Python where functions take a list of ordered arguments, **all arguments in GraphQL are passed by name specifically**. In this case, the length field has one defined argument, unit. 

### The Query and Mutation type
Every GraphQL service has a query type and may or may not have a mutation type. These types are the same as a regular object type, but they are special because they define the entry point of every GraphQL query.

```
type Query {
  author_details: [Author]
}

type Mutation {
 addAuthor(firstName: String, lastName: String) : Author
}

```

It's important to remember that other than the special status of being the "entry point" into the schema, the Query and Mutation types are the same as any other GraphQL object type, and their fields work exactly the same way.

### Variables
are used to factor dynamic values out of the query and pass them as a separate dictionary.

For example, if we have a search field where a user types in the title of documents he or she wants to view. To allow that, we’d use variables like this:

```
query Documents($title: String) {
  document(title: $title) {
    title
    
    content
  }
}
```

($title: String) is the variable definition. title is the variable name and it is prefixed by $, followed by the type in this case String.


###### Resource
[Schema Types](https://graphql.org/learn/schema/)
[Core Concept](https://medium.com/software-insight/graphql-queries-mutations-and-subscriptions-286522b263d9)

# Hands on section to write Queries
We will use **GraphiQL** an in-browser IDE for writing, validating and testing GraphQL queries.

## Prerequisite: 
GitHub account. 

**NOTE:** Github GraphQL Exploreres uses real, live, production data 

[GitHub Developer Explorer](https://developer.github.com/v4/explorer/)

### Fields
```
query { 
  viewer { 
    login
  }
}
```

```
query { 
  viewer { 
    login
    bio
    id
    avatarUrl
    name
    status {
      id
      emoji
      message
    }
  }
}
```
 


