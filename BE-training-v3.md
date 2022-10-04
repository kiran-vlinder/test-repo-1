# Vlinder BE Training

## Basics

duration: 3 days
covered: nodejs , npm , yarn, basic express, basic error handling,
source : Node.js Notes for professionals (PDF)

Chapter 1: Getting started with Node.js ............................................................................................................ 2
Section 1.1: Hello World HTTP server ........................................................................................................................... 4
Section 1.2: Hello World command line ....................................................................................................................... 5
Section 1.3: Hello World with Express .......................................................................................................................... 6
Section 1.4: Installing and Running Node.js ................................................................................................................. 6

Chapter 2: npm ............................................................................................................................................................ 19
Section 2.1: Installing packages ................................................................................................................................. 19
Section 2.2: Uninstalling packages ............................................................................................................................ 22
Section 2.3: Setting up a package configuration ..................................................................................................... 23
Section 2.4: Running scripts ....................................................................................................................................... 24
Section 2.5: Basic semantic versioning ..................................................................................................................... 24

Chapter 3: Web Apps With Express .................................................................................................................... 30
Section 3.1: Getting Started ......................................................................................................................................... 30
Section 3.2: Basic routing ........................................................................................................................................... 31
Section 3.3: Modular express application ................................................................................................................. 32

Section 3.5: JSON API with ExpressJS ....................................................................................................................... 34

Section 3.7: Adding Middleware ................................................................................................................................. 36
Section 3.8: Error Handling ......................................................................................................................................... 36
Section 3.9: Getting info from the request ................................................................................................................ 37
Section 3.10: Error handling in Express ...................................................................................................................... 38

Chapter 4: Filesystem I/O ...................................................................................................................................... 45
Section 4.1: Asynchronously Read from Files ........................................................................................................... 45

Chapter 6: Exporting and Importing Module in node.js .......................................................................... 58
Section 6.1: Exporting with ES6 syntax ...................................................................................................................... 58
Section 6.2: Using a simple module in node.js ......................................................................................................... 58

Chapter 7: How modules are loaded ................................................................................................................ 59
Section 7.1: Global Mode ............................................................................................................................................. 59
Section 7.2: Loading modules .................................................................................................................................... 59

Chapter 10: package.json ....................................................................................................................................... 63
Section 10.1: Exploring package.json ......................................................................................................................... 63
Section 10.2: Scripts ..................................................................................................................................................... 66
Section 10.3: Basic project definition ......................................................................................................................... 67
Section 10.4: Dependencies ........................................................................................................................................ 67
Section 10.5: Extended project definition .................................................................................................................. 68

Chapter 14: Callback to Promise ........................................................................................................................ 77

Section 14.2: Manually promisifying a callback ........................................................................................................ 77

Chapter 16: Exception handling ........................................................................................................................... 82
Section 16.1: Handling Exception In Node.Js ............................................................................................................. 82
Section 16.2: Unhanded Exception Management ..................................................................................................... 83
Section 16.3: Errors and Promises .............................................................................................................................. 84

Chapter 38: Creating API's with Node.js ........................................................................................................ 151
Section 38.1: GET api using Express ......................................................................................................................... 151
Section 38.2: POST api using Express ..................................................................................................................... 151

Chapter 60: Async/Await ...................................................................................................................................... 195
Section 60.1: Comparison between Promises and Async/Await .......................................................................... 195
Section 60.2: Async Functions with Try-Catch Error Handling ............................................................................. 195
Section 60.3: Stops execution at await ................................................................................................................... 196
Section 60.4: Progression from Callbacks .............................................................................................................. 196

Chapter 63: ECMAScript 2015 (ES6) with Node.js ...................................................................................... 200
Section 63.1: const/let declarations ......................................................................................................................... 200
Section 63.2: Arrow functions ................................................................................................................................... 200
Section 63.3: Arrow Function Example .................................................................................................................... 200
Section 63.4: destructuring ....................................................................................................................................... 201
Section 63.6: ES6 Class .............................................................................................................................................. 201

Chapter 80: Node.js Error Management ...................................................................................................... 242
Section 80.1: try...catch block .................................................................................................................................... 242
Section 80.2: Creating Error object ......................................................................................................................... 242
Section 80.3: Throwing Error .................................................................................................................................... 243
Chapter 81: Node.js v6 New Features and Improvement .................................................................... 244
Section 81.1: Default Function Parameters ............................................................................................................. 244
Section 81.2: Rest Parameters ................................................................................................................................. 244
Section 81.3: Arrow Functions ................................................................................................................................... 244
Section 81.4: "this" in Arrow Function ...................................................................................................................... 245
Section 81.5: Spread Operator ................................................................................................................................. 246

## Sample application and boilerplate introduction

Source: yet to create
Duratrion: yet to deceide

Chapter 1 Basics
1.1 repo, packages installation, db setup and running the program.
1.2 folder structure intro
1.3 application bootup intro
1.4 intro to common services, rest and graphql wrappers
1.5 writing business logic in common services
1.6 connecting to db and writing a model

Chapter 2 Rest
2.1 open api and loopback Rest Api intro
2.2 create a get api with openapi spec
2.3 create a post api with openapi spec

chapter 3 Mongodb , Mongoose
3.1 mongoose introduction, model creation
3.2 intro to findOne , create , findOneAndUpdate

Chapter 4 Graphql
4.1 graphql introduction
4.2 creation of graphql endpoints

chapter 5 Client Api's
5.1 intro to axios and Client api's (internal api calls)

chapter 6:
6.1 how to add a new env variable
6.2 accessing env variables

chapter 7:
7.1 error handling

chapter 6: Authentication
6.1 Authentication and role management
6.2 Authorization

chapter 7: User management
7.1 into to vlinder-login app
7.2 signup ,signin, reset password, change password

chapter 8: Email
8.1 Email templates and sending emails

## Chapter 1

### 1.1

- get repo access/credentials to application-boilerplate-code and npm login
- clone application boilerplate code
- do: npm login with provided credentials
- install mogodb in local machine or create an atlas account
- do: yarn to install dependencies
- create a .env file at the root folder and place the paste the env content

### 1.2

![neo folder stucture](https://neo.vlinder.io/be-folder-structure/)
![lucid fodler structure ]("https://https://lucid.app/publicSegments/view/dfc16245-6546-4512-8aff-a7819fb2115c/image.jpeg")

### 1.3

- build: "npm run build"
- start: "npm run start"
- first file to load is "index.js" which in turn loads Src/application.ts

application boilerplate code

```typescript
export class VApplication extends RepositoryMixin(Application) {
  constructor() {
    this.setupBindings();
  }
}
```

setupBindings contains all configuration and binding of services

### 1.4

![alt](<[https://link](https://lucid.app/lucidchart/fd0aa249-e102-443a-a705-39e57e11c2c9/edit?viewport_loc=89%2C-21%2C1304%2C1575%2CaAD7CiGbkNYn&invitationId=inv_fece8679-171c-4401-9e2b-639cc656f1cf)>)

- the core business logic is saved in src/common/modules/\*
- api logic is stored in either src/servers/rest or src/servers/graphql based on rest/gql

### 1.5

- The core business logic is stored in src/common/modules/
- Create a new folder ping in src/common/modules/
- create a new file pinger-common-service.ts in src/common/modules/ping

- create a class and its methods

```ts
export class PingCommonService {
  constructor() {}

  async ping(params: any) {
    return params;
  }
}
```

- Attach the service to Application context

in src/application

```ts
initCommonServices(){
this.service(PingCommonService);
}
```

### 1.8

- We use mongoose to npm package to create db models
- a db connection is established during the bootup of the program
- db connection code is at /src/common/services/mongoose.service.ts
- the db url must be supplied via vault or can be placed in local .env

### 1.7

The db model of any component is stored in src/common/modules/\*/\*.model.ts

- to create a new db model for user.

1. create a type script interface representing the model
2. create a mongoose schema
3. create a mongoose collection model from the above schema
4. check below link on how to query collections

![alt](https://mongoosejs.com/docs/queries.html)

```typescript
import mongoose, { Document, Schema } from "mongoose";

/**
 * The typescript interface of the User model
 */
export interface IUser extends Document {
  email: string;
  givenName?: string;
  familyName?: string;
  fullName?: string;
  emailVerified?: boolean;
}

export const UserSchema = new Schema(
  {
    telephone: { type: String },

    email: {
      type: String,
      unique: true,

      lowercase: true,
      trim: true,
      minLength: 5,
      maxLength: 50,
    },
    givenName: {
      type: String,
      sparse: true,
      lowercase: true,
      minLength: 3,
      maxLength: 50,
      trim: true,
      get: humaniseStringFunc,
    },
    familyName: {
      type: String,
      sparse: true,
      lowercase: true,
      minLength: 3,
      maxLength: 50,
      trim: true,
      get: humaniseStringFunc,
    },
    emailVerified: {
      type: Boolean,
      default: false,
    },
  },
  { timestamps: true }
);

export const User = mongoose.model<IUser>("user", UserSchema);
```

- the above created model must be imported to perform operations on that collection

## Chapter 3

### 3.1 Introduction

![download](https://www.mongodb.com/docs/manual/introduction/)

### 3.1.1 create atlas free tier and load test data

![alt](https://www.mongodb.com/docs/atlas/getting-started/)

### 3.1.2 install locally

- copy and install community version from below
  ![alt](https://www.mongodb.com/try/download/community?tck=docs_server)

### 3.1.3 Install Nosqlbooster

![alt](https://nosqlbooster.com/downloads)

- connect to local db or atlas db

### 3.2 MongoDB CRUD Operations

- for crud operations, select sample code to be displayed in mongodb shell format in the below links

  ![alt](https://www.mongodb.com/docs/manual/crud/)

### 3.2.1 Insert Documents

![alt](https://www.mongodb.com/docs/manual/tutorial/insert-documents/)

### 3.2.2 Query Documents

![alt](https://www.mongodb.com/docs/manual/tutorial/query-documents/)

### 3.2.3 Update Documents

![alt](https://www.mongodb.com/docs/manual/tutorial/update-documents/)

### 3.2.4 Delete Documents

![alt](https://www.mongodb.com/docs/manual/tutorial/remove-documents/)

### 3.3.1 mongoose schemas

![alt](https://mongoosejs.com/docs/guide.html)

### 3.3.2 mongoose schema Types

![alt](https://mongoosejs.com/docs/schematypes.html)

### 3.4 Aggregation

![alt](https://www.mongodb.com/docs/manual/aggregation/)

### 3.4.1 Aggregation Pipeline

![alt](https://www.mongodb.com/docs/manual/core/aggregation-pipeline/)

### 3.4.2 Aggregation stages

![alt](https://www.mongodb.com/docs/manual/reference/operator/aggregation-pipeline/#std-label-aggregation-pipeline-operator-reference)
Stages to cover

- $match, $count ,$group, $limit ,$lookup ,$project, $sort, $skip, $unwind, $facet

## Chapter 4

### 4.1

#### 4.1.1 Introduction

![alt](https://graphql.org/learn)

#### 4.1.2 Queries and mutations

![alt](https://graphql.org/learn/queries/)

#### 4.1.3 Schemas and Types

![alt](https://graphql.org/learn/schema/)
![alt](https://www.apollographql.com/docs/apollo-server/schema/schema/)

#### 4.1.4 Resolvers

Resolvers:
![alt](https://www.apollographql.com/docs/apollo-server/data/resolvers)

#### 4.1.5 Build-Run-Queries

![alt](https://www.apollographql.com/docs/studio/explorer/explorer/)
![alt](https://www.apollographql.com/docs/apollo-server/testing/build-run-queries)

### 4.2

#### 4.2.1 Creating new GQL Endpoints in Vlinder Boilerplate

create a new folder in src/servers/grqhql/module-name
create below files
src/servers/grqhql/module-name/module-name.module.ts
src/servers/grqhql/module-name/module-name.type.ts
src/servers/grqhql/module-name/module-name.resolver.ts

create types in type.ts

```typescript
import { gql } from "graphql-modules";

export const Hello = gql`
  type Query {
    hello: String!
  }
  type Mutation {
    hello: String!
  }
`;
```

create types in resolver.ts

```typescript
export const HelloResolver = {
  Query: {
    hello: () => "world",
  },
  Mutation: {
    hello: () => "world",
  },
};
```

create types in resolver.ts

```typescript
export const HelloResolver = {
  Query: {
    hello: () => "world",
  },
  Mutation: {
    hello: () => "world",
  },
};
```

create new gql module

```typescript
import { createModule } from "graphql-modules";
import { HelloResolver } from "./hello.resolver";
import { Hello } from "./hello.type";

export const HelloModule = createModule({
  id: "hello-module",
  dirname: __dirname,
  typeDefs: [Hello],
  resolvers: [HelloResolver],
});
```

add this module in graphql.component.ts

```typescript
const MODULES = [HelloModule];

const application: any = createApplication({
  modules: MODULES,
});
this.schema = application.createSchemaForApollo();
```
