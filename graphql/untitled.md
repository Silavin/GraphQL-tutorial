# Single End Point

A major difference between REST and GraphQL is the endpoint. Think of the endpoint as the path of the URL.

```text
https://www.gitbook.io/graphql/single-end-point
```

Up above, the end point would be the final path called 'single-end-point'. For REST, this could branch out to have multiple end points, all with different path. However, in GraphQL, there is only one end point!

## Benefits

### Efficient Data Fetching

![](../.gitbook/assets/viwd5i5.png)

REST has prepares each of their endpoints to have a set/prepared/fixed return payload. This means that there will be cases where fetching data for a client will be more than necessary. Likewise, if there are any changes in the client and they require more data types, restructuring is necessary.

This issue is recognized as Overfetching and Underfetching.

![](../.gitbook/assets/uy50ghz.png)

However, this is not the case for GraphQL. With a single endpoint, all data are on 'standby'. To retrieve said data, one just needs to request through Query what they need - no more, no less.

### Flexible to Iterations on Client Side

A common pattern with REST APIs is to structure the endpoints according to the views that you have inside your app. 

Now, imagine that you will need to change a certain request on the front-end. 

* **If the structure of this request is left unchanged**, it will face an issue of Overfetching or Underfetching. 
* **If the structure of this request was changed**,, you would most likely have to go into the server side to modify the request call. 

However, with GraphQL, you can change the request directly in the client side. \(Explained more in detail in **Actions**\)

### GraphiQL

GraphiQL is an interface to test your queries. Think of it as an inbuilt Insomnia or Postman but on the browser.

![GraphiQL testing a query](../.gitbook/assets/graphiql.png)

The greatest benefit of GraphiQL is the ability to test your Query and Mutation on the client side. This means that you do not need to go into the server and console.log out the values.

Better yet, the Query or Mutation that is being used in GraphiQL can be copy, pasted into your server and used. \(More information in **How to GraphiQL**\)

### GraphQL Schema Definition Language \(SDL\)

GraphQL uses a strong type system to define the capabilities of an API. All the types that are exposed in an API are written down in a _schema_ using the GraphQL Schema Definition Language \(SDL\). This schema serves as the contract between the client and the server to define how a client can access the data.

Once the schema is defined, the teams working on frontend and backends can do their work without further communication since they both are aware of the definite structure of the data that’s sent over the network.

Frontend teams can easily test their applications by mocking the required data structures. Once the server is ready, the switch can be flipped for the client apps to load the data from the actual API. \(More about this topic in **Schema**\)



### Insightful Analytics on the Backend

GraphQL allows you to have fine-grained insights about the data that’s requested on the backend. As each client specifies exactly what information it’s interested in, it is possible to gain a deep understanding of how the available data is being used. This can for example help in evolving an API and deprecating specific fields that are not requested by any clients any more.

With GraphQL, you can also do low-level performance monitoring of the requests that are processed by your server. GraphQL uses the concept of **resolver functions** to collect the data that’s requested by a client. Instrumenting and measuring performance of these resolvers provides crucial insights about bottlenecks in your system. \(More about this on **Resolver Functions**\)

> Do note that resolver functions acts in a similar way to a Route Handler. In case you are unaware of what is a Route handler, here is an example from express:

```text
app.get('/', function (req, res) {
  res.send('GET request to the homepage')
})
```

> The function up above is an example of a route handler.



