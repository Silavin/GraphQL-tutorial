# Setup

To get started, we are going to run an npm command:

```text
npm install express graphql  express-graphql
```

After installation, you can make a folder structure like so:

```text
- app.js
- graphql/
     |
     |__ index.js
     |
     |__ mutation/
     |       |__ index.js
     |       |__ post.js
     |       |__ user.js
     |
     |__ queries/
     |       |__ index.js
     |       |__ user.js
     |
     |__ types/      
             |__ index.js
             |__ post.js
             |__ user.js

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

const schema = require('./graphql')

app.use('/graphql', graphqlHTTP({
  schema,
  graphiql: true
}))

app.listen(3000, () => {
  console.log("GraphQL server running at port 3000...");
});
```



Under **graphql/index.js:**

Do note that this is an example of how a single source Schema is structured. There are more ways to structure your Schema but this is the method I prefer.

```javascript
import mutations from './mutations';
import queries from './queries';

export default new GraphQLSchema({
	query: new GraphQLObjectType({
		name: 'Query',
		fields: queries
	}),
	mutation: new GraphQLObjectType({
		name: 'Mutation',
		fields: mutations
	})
});
```



