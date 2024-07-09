
### Name  : M S I Hussain
### Index : UKI STU 836
### Node.js Basics Assignment

#### 1. What is Node.js and what is it used for?
Node.js is a runtime environment that allows the execution of JavaScript code on the server side. It is used for building scalable network applications, particularly web servers.

#### 2. Explain the main differences between Node.js and traditional web server environments like Apache or Nginx.
Node.js uses a single-threaded, event-driven architecture, which allows it to handle many connections concurrently. Traditional web servers like Apache and Nginx use a multi-threaded approach, where each connection might be handled by a separate thread.

#### 3. What is the V8 engine and how does Node.js utilize it?
The V8 engine is Google's open-source high-performance JavaScript and WebAssembly engine. Node.js uses the V8 engine to execute JavaScript code on the server side.

#### 4. Describe the event-driven architecture of Node.js.
Node.js operates on an event-driven architecture, where an event loop processes asynchronous callbacks. This allows Node.js to handle I/O operations without blocking the main thread.

#### 5. What are some common use cases for Node.js?
- Real-time web applications (e.g., chat applications)
- RESTful APIs
- Data streaming applications
- Single-page applications
- Microservices architecture

#### 6. How does Node.js handle asynchronous operations?
Node.js uses non-blocking I/O and asynchronous callbacks to handle operations. This allows it to continue executing other code while waiting for I/O operations to complete.

#### 7. What is the purpose of the `package.json` file in a Node.js project?
The `package.json` file is used to manage a project's dependencies, scripts, versioning, and metadata. It is essential for sharing the project with others and for reproducing the development environment.

#### 8. Explain the role of the Node Package Manager (NPM).
NPM is a package manager for Node.js that helps in installing, updating, and managing libraries and packages used in a Node.js project.

#### 9. What is the `node_modules` folder and why is it important?
The `node_modules` folder stores all the installed dependencies for a Node.js project. It is essential for running the project as it contains all the required libraries.

#### 10. How can you check the version of Node.js and NPM installed on your system?
You can check the version of Node.js by running `node -v` and the version of NPM by running `npm -v` in the terminal.

#### 11. How does Node.js handle concurrency and what are the benefits of this approach?
Node.js handles concurrency using an event loop and asynchronous callbacks. This approach allows it to manage many connections efficiently without the overhead of threading, making it lightweight and scalable.

#### 12. How does Node.js handle file I/O? Provide an example of reading a file asynchronously.
Node.js handles file I/O using the `fs` module. Here is an example of reading a file asynchronously:

```javascript
const fs = require('fs');

fs.readFile('example.txt', 'utf8', (err, data) => {
    if (err) {
        console.error(err);
        return;
    }
    console.log(data);
});
```

#### 13. What are streams in Node.js and how are they useful?
Streams in Node.js are objects that allow reading or writing data continuously. They are useful for handling large files or data in chunks, improving performance and reducing memory usage.

### Node.js Modules

#### 1. What are modules in Node.js and why are they important?
Modules in Node.js are reusable pieces of code that can be exported and imported into other files. They help in organizing code and managing dependencies.

#### 2. How do you create a module in Node.js? Provide a simple example.
To create a module in Node.js, you can use the `module.exports` object. Here is a simple example:

```javascript
// math.js
module.exports.add = (a, b) => a + b;
module.exports.subtract = (a, b) => a - b;

// main.js
const math = require('./math');
console.log(math.add(2, 3)); // 5
```

#### 3. Explain the difference between `require` and `import` statements in Node.js.
`require` is used in CommonJS modules to import modules, whereas `import` is used in ES6 modules. `require` is synchronous and can be used anywhere in the code, while `import` is asynchronous and must be at the top of the file.

#### 4. What is the `module.exports` object and how is it used?
The `module.exports` object is used to export functions, objects, or values from a module so that they can be used in other files via `require`.

#### 5. Describe how you can use the `exports` shorthand to export module contents.
The `exports` shorthand is an alias for `module.exports`. You can attach properties or methods to `exports` to export them. However, assigning a new value to `exports` does not affect `module.exports`.

```javascript
// math.js
exports.add = (a, b) => a + b;

// main.js
const math = require('./math');
console.log(math.add(2, 3)); // 5
```

#### 6. What is the CommonJS module system?
The CommonJS module system is a standard for structuring and organizing JavaScript code into reusable modules using `require` and `module.exports`.

#### 7. How can you import a module installed via NPM in your Node.js application?
You can import an NPM-installed module using the `require` statement:

```javascript
const express = require('express');
```

#### 8. Explain how the `path` module works in Node.js. Provide an example of using it.
The `path` module provides utilities for working with file and directory paths. Here is an example of using the `path` module:

```javascript
const path = require('path');
const fullPath = path.join(__dirname, 'example.txt');
console.log(fullPath);
```

#### 9. How do you handle circular dependencies in Node.js modules?
Circular dependencies occur when two or more modules depend on each other. Node.js partially resolves modules to break the circular dependency. It's essential to refactor the code to avoid such dependencies.

#### 10. What is a built-in module in Node.js? Name a few and explain their purposes.
Built-in modules are core modules provided by Node.js, such as:
- `http`: To create an HTTP server.
- `fs`: To handle file system operations.
- `path`: To work with file and directory paths.

#### 11. What is the difference between relative and absolute module paths in Node.js?
Relative module paths start with `./` or `../` and are relative to the current file's location. Absolute module paths are resolved from the root of the file system.

#### 12. What is a module wrapper function in Node.js?
A module wrapper function wraps each module to provide a private scope, preventing global namespace pollution. It looks like this:

```javascript
(function(exports, require, module, __filename, __dirname) {
    // Module code here
});
```

#### 13. Describe the buffer module and its use in Node.js.
The buffer module provides a way to handle binary data directly in Node.js. It is used when dealing with binary streams, such as reading from or writing to files or network connections.

### Starting an HTTP Server in Node.js

#### 1. How do you create a simple HTTP server in Node.js? Provide a code example.
To create an HTTP server, use the `http` module:

```javascript
const http = require('http');

const server = http.createServer((req, res) => {
    res.statusCode = 200;
    res.setHeader('Content-Type', 'text/plain');
    res.end('Hello, World!\n');
});

server.listen(3000, '127.0.0.1', () => {
    console.log('Server running at http://127.0.0.1:3000/');
});
```

#### 2. Explain the purpose of the `http` module in Node.js.
The `http` module provides the functionality to create and manage HTTP servers and clients, allowing Node.js to handle HTTP requests and responses.

#### 3. What method do you use to start the HTTP server and make it listen on a specific port?
Use the `listen` method to start the HTTP server and make it listen on a specific port:

```javascript
server.listen(port, hostname, callback);
```

#### 4. How can you send a response to the client in an HTTP server created with Node.js?
Use the `res.end` method to send a response to the client:

```javascript
res.end('Response text');
```

#### 5. Explain the request and response objects in the context of an HTTP server.
The request object (`req`) contains information about the client's request, such as the URL, method, headers, and body. The response object (`res`) is used to send data back to the client.

#### 6. How do you handle different HTTP methods (GET, POST, etc.) in a Node.js HTTP server?
Check the `req.method` property to handle different HTTP methods:

```javascript
if (req.method === 'GET') {
    // Handle GET request
} else if (req.method === 'POST') {
    // Handle POST request
}
```

#### 7. What is middleware in the context of a Node.js HTTP server?
Middleware functions are functions that process requests before they reach the main request handler. They can be used for logging, authentication, parsing request bodies, etc.

#### 8. How can you serve static files using an HTTP server in Node.js?
Use the `fs` module to

 read and serve static files:

```javascript
const fs = require('fs');

http.createServer((req, res) => {
    fs.readFile('index.html', (err, data) => {
        if (err) {
            res.writeHead(404);
            res.end('File not found');
        } else {
            res.writeHead(200, { 'Content-Type': 'text/html' });
            res.end(data);
        }
    });
}).listen(3000);
```

#### 9. Explain how to handle errors in an HTTP server created with Node.js.
Handle errors using try-catch blocks or error-first callbacks. Log errors and send appropriate HTTP status codes to the client.

#### 10. How can you implement routing in a Node.js HTTP server without using external libraries?
Implement routing by checking the `req.url` property:

```javascript
http.createServer((req, res) => {
    if (req.url === '/') {
        res.end('Home Page');
    } else if (req.url === '/about') {
        res.end('About Page');
    } else {
        res.writeHead(404);
        res.end('Page not found');
    }
}).listen(3000);
```

---

