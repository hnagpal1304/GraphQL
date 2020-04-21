# Purpose
Intention is to self learn GraphQL from available resources on internet.

# What is GraphQL
GraphQL is a query language for APIs and a runtime for fulfilling those queries with your existing data. GraphQL provides a complete and understandable description of the data in your API, gives clients the power to ask for exactly what they need and nothing more, makes it easier to evolve APIs over time, and enables powerful developer tools.

## Example
GraphQL is a query language that lets you write queries using an object structure rather than a text string.

So rather than use an SQL query like:
`SELECT name, id, description FROM projects`
Simply describe the object and the fields you’d like from that object you like so:
`
{
  projects {
    id
    name
    description
  }
}
`

###### Resource
[A query language for your API](https://graphql.org/)
[A query language for your API](https://medium.com/@JeffLombardJr/when-and-why-to-use-graphql-24f6bce4839d)

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
