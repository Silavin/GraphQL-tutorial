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

```javascript
const AuthorType = new GraphQLObjectType({
  name: 'Author',
  fields: () => ({
    name: {
      type: GraphQLString,
      resolve: xml =>
        xml.GoodreadsResponse.author[0].name[0]
    },
    books: {
      type: new GraphQLList(BookType),
      resolve: xml => {
        const ids = xml.GoodreadsResponse.author[0].books[0].book.map(elem => elem.id[0]._)
        console.log('fetching bookkks!')
        return Promise.all(ids.map(id =>
          fetch(`https://www.goodreads.com/book/show/${id}.xml?key=42tmzmwXfJJzHcbXlBRg`)
            .then(response => response.text())
            .then(parseXML)
        ))
      }

    }
  })
})

```

Notice that there are some difference to your usual JSON format? let's go over them in detail.

> type - a declarative statement

> !  - to state that the field is required.

> \[ XXX \] - to state that this field contains another data structure.

> \(XXX: Type\) - parameters to input data into the payload \(body\)







