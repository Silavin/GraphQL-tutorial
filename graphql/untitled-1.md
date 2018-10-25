# Getting Started

To get started, we are going to run an npm command:

```text
npm install express graphql  express-graphql
```

After installation, you can make a folder structure like so:

```text
- app.js
- src/
   |__ graphql/
          |__ product/
          |       |__ schema.graphql
          |       |__ resolver.js
          |
          |__ variant/
                  |__ schema.graphql
                  |__ resolver.js

- index.js
- package.json
```

This folder structure is for you to have a root file to directly access GraphQL when necessary. 

The Product and Variant are folders that store their respective Schema and Resolvers. The determinant of the creation of these folders are based off the name of the top level Schema. \(More information can be found in Schema\)

