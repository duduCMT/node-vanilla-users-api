# NodeJS Fundamentals

## Description

Repository for learning and practicing NodeJS from the Rockeatseat Course.

## Setup

Install Dependencies With

```bash
npm install
```

To run the project, use:

```bash
npm start
```

To run the project in developer mode, use:

```bash
npm run dev
```

## Notations

I'm recording here some important lessons learned during the project implementation.

### About Javascript Imports

Using CommonJS

```javascript
const http = require("http");
```

To use ESModules like the exemple:

```javascript
import http from "http";
```

Set in your packege.json file this line:

```json
"type": "module",
```

In the latest versions of NodeJS, it is recommended to use `node:` in internal imports of node modules. That is:

```javascript
// ⚠️ Not recommended
import http from "http";

// ✅ Recommended
import http from "node:http";
```

### How To test Endpoints

Is this course, we use [HTTPie](https://httpie.io/) in terminal to test the API.

It is an alternative solution to the well-known curl.

Exemple:

```bash
http localhost:3333
```

Response:

```bash
HTTP/1.1 200 OK
Connection: keep-alive
Content-Length: 11
Date: Sun, 22 Feb 2026 15:33:11 GMT
Keep-Alive: timeout=5

Hello World
```

### Private Attributes in NodeJS Classes

To make a attriubute private using nodeJS, it is conventional to use `#` at the beginning of declaration. Exemple:

This is a public attribute

```javascript
export class Database {
  data = {};
}

const database = new Database();
console.log(database.data);
```

This is a private attribute

```javascript
export class Database {
  #data = {};
}

const database = new Database();
console.log(database.#data); // This doesn't work
```

If you try to run the code, Node will return the following error:

```bash
SyntaxError: Private field '#data' must be declared in an enclosing class
```
