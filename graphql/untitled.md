# Single End Point

A major difference between REST and GraphQL is the endpoint. Think of the endpoint as the path of the URL.

```text
https://www.gitbook.io/graphql/single-end-point
```

Up above, the end point would be the final path called 'single-end-point'. For REST, this could branch out to have multiple end points, all with different path. However, in GraphQL, there is only one end point!

## Benefits

Having a single end point means that the all request are passing through one point. Here is a glimpse of the difference between REST and GraphQL

![](../.gitbook/assets/viwd5i5.png)

REST has prepares each of their endpoints to have a set/prepared/fixed return payload. This means that there will be cases where fetching data for a client will be more than necessary. Likewise, if there are any changes in the client and they require more data types, restructuring is necessary.

This issue is recognized as Overfetching and Underfetching.

![](../.gitbook/assets/uy50ghz.png)

However, this is not the case for GraphQL. With a single endpoint, all data is on 'standby'. To retrieve said data, one just needs to request through Query what they need - no more, no less.

> Do note that when a client changes its requirements, structural changes are vastly different from Query changes. Structural changes take place on the level of the Schema while Query changes takes place only at the level of the Action \(basically the get, post, put, delete\).



