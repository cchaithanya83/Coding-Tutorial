# Express.js

## Overview
Express.js is a fast, unopinionated, and minimalist web framework for Node.js, designed for building web applications and APIs. It simplifies server-side development with robust features and an extensive set of middleware.

## Installation
To install Express.js, use npm:
```bash
npm install express
```

## Basic Usage
Here's a simple example of an Express.js application:
```javascript
const express = require('express');
const app = express();

app.get('/', (req, res) => {
  res.send('Hello World!');
});

app.listen(3000, () => {
  console.log('Server is running on port 3000');
});
```

## Middleware
Middleware functions are functions that have access to the request object (`req`), the response object (`res`), and the `next` middleware function in the application’s request-response cycle. They can execute any code, make changes to the request and response objects, end the request-response cycle, and call the next middleware function.

Example of a middleware:
```javascript
app.use((req, res, next) => {
  console.log('Time:', Date.now());
  next();
});
```

## Routing
Express provides a robust set of features for routing. Here’s how you define a simple route:
```javascript
app.get('/example', (req, res) => {
  res.send('Example route');
});
```

## Handling Different HTTP Methods
Express allows you to handle different HTTP methods for the same route:
```javascript
app.route('/book')
  .get((req, res) => {
    res.send('Get a random book');
  })
  .post((req, res) => {
    res.send('Add a book');
  })
  .put((req, res) => {
    res.send('Update the book');
  });
```

## Static Files
To serve static files such as images, CSS files, and JavaScript files, use the `express.static` built-in middleware function:
```javascript
app.use(express.static('public'));
```

## Error Handling
Error-handling middleware always takes four arguments: (err, req, res, next):
```javascript
app.use((err, req, res, next) => {
  console.error(err.stack);
  res.status(500).send('Something broke!');
});
```

## Example Project Structure
A typical Express project structure might look like this:
```
myapp/
├── app.js
├── package.json
├── public/
│   ├── images/
│   ├── javascripts/
│   └── stylesheets/
├── routes/
│   └── index.js
└── views/
    └── index.pug
```

## Creating a Simple API
Express makes it easy to build APIs. Here’s an example of a simple API:
```javascript
const express = require('express');
const app = express();
const port = 3000;

let books = [
  { id: 1, title: '1984', author: 'George Orwell' },
  { id: 2, title: 'To Kill a Mockingbird', author: 'Harper Lee' },
];

app.use(express.json());

app.get('/api/books', (req, res) => {
  res.json(books);
});

app.post('/api/books', (req, res) => {
  const book = { id: books.length + 1, ...req.body };
  books.push(book);
  res.status(201).json(book);
});

app.listen(port, () => {
  console.log(`Server is running on port ${port}`);
});
```

## Using Templates
Express supports various template engines like Pug, EJS, and Handlebars. Here’s how to use Pug with Express:
1. Install Pug:
    ```bash
    npm install pug
    ```
2. Set up Pug in your Express app:
    ```javascript
    app.set('view engine', 'pug');
    app.set('views', './views');

    app.get('/pug', (req, res) => {
      res.render('index', { title: 'Hey', message: 'Hello there!' });
    });
    ```

## Advanced Topics

### Express Router
The `express.Router` class is a complete middleware and routing system; think of it as a “mini-application.”
```javascript
const express = require('express');
const app = express();
const router = express.Router();

router.get('/', (req, res) => {
  res.send('Router Home Page');
});

router.get('/about', (req, res) => {
  res.send('About this Router');
});

app.use('/router', router);
```

### Database Integration
You can integrate databases like MongoDB, MySQL, and PostgreSQL with Express. Here’s an example using MongoDB and Mongoose:
1. Install Mongoose:
    ```bash
    npm install mongoose
    ```
2. Connect to MongoDB:
    ```javascript
    const mongoose = require('mongoose');

    mongoose.connect('mongodb://localhost/mydatabase', { useNewUrlParser: true, useUnifiedTopology: true });

    const db = mongoose.connection;
    db.on('error', console.error.bind(console, 'connection error:'));
    db.once('open', () => {
      console.log('Connected to MongoDB');
    });
    ```

### Security
Use Helmet to secure your Express apps by setting various HTTP headers:
```bash
npm install helmet
```
```javascript
const helmet = require('helmet');
app.use(helmet());
```

## Additional Resources
- [Express.js Documentation](https://expressjs.com/en/4x/api.html)
- [Express.js GitHub Repository](https://github.com/expressjs/express)
- [Node.js Documentation](https://nodejs.org/en/docs/)
- [Mongoose Documentation](https://mongoosejs.com/)
- [Helmet Documentation](https://helmetjs.github.io/)
