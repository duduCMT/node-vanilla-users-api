# Node Vanilla Users API

## Description

Repository for learning and practicing NodeJS from the Rockeatseat Course.

A user registration API built with pure Node.js, without external frameworks. Even the database layer is implemented using the native Node.js file system, storing and managing data directly within project files. This project demonstrates how to build a fully functional API from scratch using only core Node.js modules.

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

### NodeJS File System

Node has two modules for working with files.

- `node:fs`
- `node:fs/promises`

Here's the difference between them:

```javascript
import fs from "node:fs";
```

`node:fs` uses methods with callback functions, an older and less practical execution model compared to promise systems.

```javascript
import fs from "node:fs/promises";
```

`node:fs/promises` uses the same engines, and file manipulation strategies as `node:fs`, with the difference being that it uses JavaScript's promise system. It has a more practical and readable syntax.

Another difference is that methods related to Stream do not exist in `node:fs/promises`.

### NodeJS File Constants

In older versions of Node, it was common to use `__dirname` and other constants that referred to the project's file system. However, with the introduction of `"type": "module"`, these constants no longer work.

Now, you should use strategies like `import.meta.url`.

### Tip for Testing Regex

A quick and practical way to test regular expressions is by using the [Regex Previewer](https://marketplace.visualstudio.com/items?itemName=chrmarti.regex) extension, which allows you to type text and see if the result of the regular expression is as expected.
