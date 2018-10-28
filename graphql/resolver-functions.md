# Resolver Functions

As mentioned  before, resolver functions work similarly to a route handler. It is invoked once a Query/Mutation is made for that particular Schema. 

Here is the definition of a resolver function:  A function on a GraphQL server that's responsible for fetching the data for a single field. 



```javascript
resolve: xml => {
        const ids = xml.GoodreadsResponse.author[0].books[0].book.map(elem => elem.id[0]._)
        console.log('fetching bookkks!')
        return Promise.all(ids.map(id =>
          fetch(`https://www.goodreads.com/book/show/${id}.xml?key=42tmzmwXfJJzHcbXlBRg`)
            .then(response => response.text())
            .then(parseXML)
        ))
      }
```

It is extremely important for GraphQL to include this feature as it enables the Queries and Mutation to pass through a layer that aggregates different types of APIs. \(In short - you can wrap GraphQL around an already existing API\)

![GraphQL as a wrapper for multiple APIs](../.gitbook/assets/graphql-wrapper.png)

Using GraphQL as a wrapper, it treats the other API servers as a black box. For programmers on the front-end and the back-end, once they have set up the proper Schema, they only need to interact with GraphQL.



Not only limited to API servers, the resolve function can directly connect to the Database as well. This allows GraphQL to stand on it's own as a replacement for REST. 

![An image depicting how GraphQL can combine Databases with APIs](../.gitbook/assets/graphql-wrapper-database.png)



