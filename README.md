# Aloompa Coding Challenge: GraphQl API

### Description:

Create a GraphQL API to query apps, events, and stages using this [data set](https://assets.aloompa.com.s3.amazonaws.com/rappers/hiphopfest.json).

Your project must use Node (TypeScript or JavaScript) for the query resolvers. You may use any libraries or frameworks as dependencies, but the code inside the project must be your own.

### API Requirements:
- [x] You should be able to list all of the apps
- [x] You should be able to query a single app
- [x] You should be able to list all the stages
- [x] You should be able to query a single stage
- [x] You should be able to search the stages by name
- [x] You should be able to list all of the events
- [x] You should be able to query a single event
- [x] You should be able to search the events by name
- [x] You should be able to query the events that occur between two dates
- [x] You should be able to list all of the events in an app
- [x] You should be able to list all the stages in an app
- [x] You should be able to get the stage in an event
- [x] You should be able to list the events at a stage
- [x] You should be able to add, update and remove all entities

### Extra Credit:
- [ ] Your project is deployed to AWS ([JavaScript & AWS Solution Here](https://github.com/thejmdw/graphql-challenge))
- [x] Your repo has a README
- [x] You use TypeScript

---

# TypeScript Solution

### Technologies Used


![](https://img.shields.io/badge/Node.js-43853D?style=for-the-badge&logo=node.js&logoColor=white) ![TypeScript](https://img.shields.io/badge/TypeScript-323330?style=for-the-badge&logo=typescript) ![Apollo-GraphQL](https://img.shields.io/badge/-ApolloGraphQL-311C87?style=for-the-badge&logo=apollo-graphql)

### Running the API

### **Locally
#### Prerequisites

1. Install [Node.js](https://nodejs.org/en/)

#### Installation

1. Clone this repository and change to the directory in the  terminal.
    ```
    git clone git@github.com:thejmdw/graphql-challenge-typescript.git
    cd graphql-challenge-typescript
    ```
2. Install dependencies.
    ```
    npm install
    ```
3. Start server.
    ```
    node --loader ts-node/esm ./index.ts 
    ```
    or
    ```
     npm start
    ```
4. Point browser to [http://localhost:4000](http://localhost:4000) and click "Query your server" to explore with graph with Apollo Studio.

---

# Problem Encountered

Attempting to deploy to AWS using Serverless yields the following error: 

```
serverless deploy --stage prod

Running "serverless" from node_modules

Deploying aloompa-typescript-challenge to stage prod (us-east-1)
Bundling with Webpack...
asset index.js 33.4 KiB [emitted] (name: index)
./index.ts 11.8 KiB [built] [code generated]
external "apollo-server-lambda" 42 bytes [built] [code generated]
external "uuid" 42 bytes [built] [code generated]
external "graphql-type-long" 42 bytes [built] [code generated]
webpack compiled successfully in 1570 ms

✖ Stack aloompa-typescript-challenge-prod failed to deploy (2s)
Environment: darwin, node 16.14.0, framework 3.7.5 (local) 3.7.5v (global), plugin 6.1.5, SDK 4.3.2
Credentials: Local, "default" profile
Docs:        docs.serverless.com
Support:     forum.serverless.com
Bugs:        github.com/serverless/serverless/issues

Error:
Error: npm ls -prod -json -depth=1 failed with code 1
    at ChildProcess.<anonymous> (/Users/thejmdw/workspace/take-homes/aloompa-ts/node_modules/serverless-webpack/lib/utils.js:91:16)
    at ChildProcess.emit (node:events:520:28)
    at ChildProcess.emit (node:domain:475:12)
    at maybeClose (node:internal/child_process:1092:16)

```

###Steps to Recreate Problem
 1. ```git checkout thejmdw-aws```
 2. ```serverless deploy --stage prod```

###Google
Google lead me this [issue](https://github.com/serverless/serverless/issues/9187) on the Serverless Repo.

Which lead me down a rabbit hole of these [issues](https://github.com/serverless-heaven/serverless-webpack/issues?q=depth) on the Serverless-Webpack Repo.

###Solutions I tried:

1. removing ```package-lock.json``` & ```node_modules``` and using ```npm install`` to reinstall the dependencies
2. updating to latest ```serverless-webpack``` & ```webpack``` versions
3. changing the node.js ```provider.runtime``` in the ```serverless.yml``` from ```nodejs12.x``` to ```nodejs14.x```

 