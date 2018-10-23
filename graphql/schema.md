# Schema

GraphQL Schema defines how the clients can request data from the servers. It is often seen as a contract between the server and client, generally used as a reference on both ends. Therefore, it is an important concept to understand.

There are two main types of Schema definitions, which follow the usual CRUD \(Create, Read, Update, Delete\). There are three types in total but we will go through Subscription later.

```javascript
type Query { ... } //For Read
type Mutation { ... } //For Create, Update and Delete
type Subscription { ... } //For notification if a mutation takes place
```

## Structure

The structure shares a huge level of similarities with JSON. GraphQL created it's own Schema Definition Language \(SDL\) and here is how it looks:

```text
type Query {
  allPersons(last: Int): [Person!]!
}

type Mutation {
  createPerson(name: String!, age: Int!): Person!
}

type Subscription {
  newPerson: Person!
}

type Person {
  name: String!
  age: Int!
  posts: [Post!]!
}

type Post {
  title: String!
  author: Person!
}
```

Notice that there are some difference to your usual JSON format? let's go over them in detail.

> type - a declarative statement

> !  - to state that the field is required.

> \[ XXX \] - to state that this field contains another data structure.

> \(XXX: Type\) - parameters to input data into the payload \(body\)







