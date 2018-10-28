# Setup

To get started, we are going to run an npm command:

```text
npm install express graphql  express-graphql
```

After installation, you can make a folder structure like so:

```text
- app.js
- src/
   |__ graphql/
          |
          |__ schema.js
          |
          |__ product/
          |       |__ schema.js
          |       |__ resolver.js
          |
          |__ variant/
                  |__ schema.js
                  |__ resolver.js

- index.js
- server.js
- package.json
```

This folder structure is for you to have a root file to directly access GraphQL when necessary. 

The Product and Variant are folders that store their respective Schema and Resolvers. The determinant of the creation of these folders are based off the name of the top level Schema. \(More information can be found in Schema\)



Next, under **server.js**, type out this code:

```javascript
const express = require('express')
const graphqlHTTP = require('express-graphql')
const app = express()

const schema = require('./src/graphql/schema')

app.use('/graphql', graphqlHTTP({
  schema,
  graphiql: true
}))

app.listen(4000)
console.log('Listening ...')
```



Under **src/graphql/schema.js:**

Do note that this is an example of how a single source Schema is structured. There are more ways to structure your Schema but this is the method I prefer.

```javascript
const { GraphQLSchema, GraphQLObjectType } = require("graphql");
const product = require("./product/schema.js")
const variant = require("./variant/schema.js")

module.exports = new GraphQLSchema({
    query: new GraphQLObjectType({
        name: "Query",
        fields: {
            product: product.graphql.query,
            variant: variant.graphql.query
        }
    }),
    
    mutation: new GraphQLObjectType({
        name: "Mutation",
        fields: {
            product: product.graphql.mutation,
            variant: variant.graphql.mutation
        }
    })
})
```



