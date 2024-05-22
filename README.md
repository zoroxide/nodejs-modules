# nodejs-modules
a list of awesome nodejs modules and their usages
<br>

### 1. `express`
Express is a minimal and flexible Node.js web application framework that provides a robust set of features for web and mobile applications.

#### Installation
```bash
npm install express
```

#### Example
```javascript
const express = require('express');
const app = express();
const port = 3000;

app.get('/', (req, res) => {
  res.send('Hello World!');
});

app.listen(port, () => {
  console.log(`Example app listening at http://localhost:${port}`);
});
```
This example sets up a basic web server that responds with "Hello World!" when accessed.

### 2. `mongoose`
Mongoose is an Object Data Modeling (ODM) library for MongoDB and Node.js, which provides a straightforward, schema-based solution to model your application data.

#### Installation
```bash
npm install mongoose
```

#### Example
```javascript
const mongoose = require('mongoose');

mongoose.connect('mongodb://localhost/test', { useNewUrlParser: true, useUnifiedTopology: true });

const Cat = mongoose.model('Cat', { name: String });

const kitty = new Cat({ name: 'Zildjian' });
kitty.save().then(() => console.log('meow'));
```
This example connects to a MongoDB database and saves a simple document.

### 3. `jsonwebtoken`
jsonwebtoken is a library to work with JSON Web Tokens (JWTs). It can be used for securely transmitting information between parties as a JSON object.

#### Installation
```bash
npm install jsonwebtoken
```

#### Example
```javascript
const jwt = require('jsonwebtoken');

const token = jwt.sign({ foo: 'bar' }, 'shhhhh');
console.log('Generated Token:', token);

jwt.verify(token, 'shhhhh', (err, decoded) => {
  if (err) {
    console.error('Token verification failed:', err);
  } else {
    console.log('Decoded Token:', decoded);
  }
});
```
This example generates a JWT and verifies it.

### 4. `lodash`
Lodash is a modern JavaScript utility library delivering modularity, performance, & extras.

#### Installation
```bash
npm install lodash
```

#### Example
```javascript
const _ = require('lodash');

const array = [1, 2, 3, 4, 5, 6];
const evens = _.filter(array, num => num % 2 === 0);

console.log('Even numbers:', evens);
```
This example uses Lodash to filter an array for even numbers.

### 5. `chalk`
Chalk is a terminal string styling library that allows you to style your terminal output.

#### Installation
```bash
npm install chalk
```

#### Example
```javascript
const chalk = require('chalk');

console.log(chalk.blue('Hello world!'));
console.log(chalk.red('This text is red!'));
console.log(chalk.green('This text is green!'));
```
This example demonstrates how to style terminal text using Chalk.

### 6. `dotenv`
dotenv is a zero-dependency module that loads environment variables from a `.env` file into `process.env`.

#### Installation
```bash
npm install dotenv
```

#### Example
Create a `.env` file:
```
DB_HOST=localhost
DB_USER=root
DB_PASS=s1mpl3
```

Load the environment variables in your code:
```javascript
require('dotenv').config();

console.log('Database Host:', process.env.DB_HOST);
console.log('Database User:', process.env.DB_USER);
console.log('Database Password:', process.env.DB_PASS);
```
This example shows how to load environment variables from a `.env` file.

### 7. `moment`
Moment is a library for parsing, validating, manipulating, and formatting dates.

#### Installation
```bash
npm install moment
```

#### Example
```javascript
const moment = require('moment');

const now = moment();
console.log('Current date and time:', now.format('YYYY-MM-DD HH:mm:ss'));

const tomorrow = moment().add(1, 'days');
console.log('Tomorrow:', tomorrow.format('YYYY-MM-DD'));
```
This example shows how to manipulate and format dates using Moment.

### 8. `bcrypt`
bcrypt is a library to help you hash passwords.

#### Installation
```bash
npm install bcrypt
```

#### Example
```javascript
const bcrypt = require('bcrypt');
const saltRounds = 10;
const myPlaintextPassword = 's0/\/\P4$$w0rD';

bcrypt.hash(myPlaintextPassword, saltRounds, (err, hash) => {
  if (err) {
    console.error('Error hashing password:', err);
  } else {
    console.log('Hashed password:', hash);
    
    bcrypt.compare(myPlaintextPassword, hash, (err, result) => {
      if (err) {
        console.error('Error comparing password:', err);
      } else {
        console.log('Password match:', result);
      }
    });
  }
});
```
This example demonstrates how to hash and compare passwords using bcrypt.

Absolutely! Here are some additional useful Node.js modules along with examples:

### 9. `async`
The `async` library provides powerful functions for working with asynchronous JavaScript, making it easier to manage complex flows.

#### Installation
```bash
npm install async
```

#### Example
```javascript
const async = require('async');

async.series([
  function(callback) {
    setTimeout(() => {
      console.log('Task 1');
      callback(null, 1);
    }, 1000);
  },
  function(callback) {
    setTimeout(() => {
      console.log('Task 2');
      callback(null, 2);
    }, 500);
  }
], (err, results) => {
  console.log('Results:', results);
});
```
This example shows how to run tasks in series.

### 10. `winston`
Winston is a versatile logging library for Node.js.

#### Installation
```bash
npm install winston
```

#### Example
```javascript
const winston = require('winston');

const logger = winston.createLogger({
  level: 'info',
  format: winston.format.json(),
  transports: [
    new winston.transports.Console(),
    new winston.transports.File({ filename: 'combined.log' })
  ]
});

logger.info('Hello, this is an info message');
logger.error('Hello, this is an error message');
```
This example demonstrates basic logging with Winston.

### 11. `multer`
Multer is a middleware for handling `multipart/form-data`, which is primarily used for uploading files.

#### Installation
```bash
npm install multer
```

#### Example
```javascript
const express = require('express');
const multer = require('multer');
const upload = multer({ dest: 'uploads/' });
const app = express();

app.post('/upload', upload.single('file'), (req, res) => {
  res.send('File uploaded successfully');
});

app.listen(3000, () => {
  console.log('Server started on port 3000');
});
```
This example sets up a route to handle file uploads.

### 12. `nodemailer`
Nodemailer is a module for sending emails from Node.js applications.

#### Installation
```bash
npm install nodemailer
```

#### Example
```javascript
const nodemailer = require('nodemailer');

let transporter = nodemailer.createTransport({
  service: 'gmail',
  auth: {
    user: 'your-email@gmail.com',
    pass: 'your-email-password'
  }
});

let mailOptions = {
  from: 'your-email@gmail.com',
  to: 'recipient-email@example.com',
  subject: 'Test Email',
  text: 'Hello, this is a test email sent from Node.js'
};

transporter.sendMail(mailOptions, (error, info) => {
  if (error) {
    console.error('Error sending email:', error);
  } else {
    console.log('Email sent:', info.response);
  }
});
```
This example shows how to send an email using Nodemailer.

### 13. `cors`
CORS is a middleware to enable Cross-Origin Resource Sharing in Express applications.

#### Installation
```bash
npm install cors
```

#### Example
```javascript
const express = require('express');
const cors = require('cors');
const app = express();

app.use(cors());

app.get('/', (req, res) => {
  res.send('CORS enabled');
});

app.listen(3000, () => {
  console.log('Server started on port 3000');
});
```
This example sets up an Express server with CORS enabled.

### 14. `helmet`
Helmet helps secure Express apps by setting various HTTP headers.

#### Installation
```bash
npm install helmet
```

#### Example
```javascript
const express = require('express');
const helmet = require('helmet');
const app = express();

app.use(helmet());

app.get('/', (req, res) => {
  res.send('Helmet security headers enabled');
});

app.listen(3000, () => {
  console.log('Server started on port 3000');
});
```
This example demonstrates how to enhance security using Helmet.

### 15. `pm2`
PM2 is a production process manager for Node.js applications that allows you to keep applications alive forever, reload them without downtime, and facilitate common system admin tasks.

#### Installation
```bash
npm install pm2 -g
```

#### Example
```bash
pm2 start app.js
pm2 list
pm2 stop app.js
pm2 restart app.js
pm2 delete app.js
```
This example shows basic commands for managing a Node.js application with PM2.

### 16. `compression`
Compression middleware for compressing HTTP responses in Express.

#### Installation
```bash
npm install compression
```

#### Example
```javascript
const express = require('express');
const compression = require('compression');
const app = express();

app.use(compression());

app.get('/', (req, res) => {
  res.send('Hello, compressed world!');
});

app.listen(3000, () => {
  console.log('Server started on port 3000');
});
```
This example shows how to enable response compression in an Express app.

### 17. `socket.io`
Socket.IO enables real-time, bidirectional, and event-based communication.

#### Installation
```bash
npm install socket.io
```

#### Example
```javascript
const express = require('express');
const http = require('http');
const socketIo = require('socket.io');

const app = express();
const server = http.createServer(app);
const io = socketIo(server);

io.on('connection', (socket) => {
  console.log('A user connected');
  socket.on('disconnect', () => {
    console.log('User disconnected');
  });
});

server.listen(3000, () => {
  console.log('Server started on port 3000');
});
```
This example sets up a basic Socket.IO server.

### 18. `sequelize`
Sequelize is a promise-based Node.js ORM for Postgres, MySQL, MariaDB, SQLite, and Microsoft SQL Server.

#### Installation
```bash
npm install sequelize
npm install pg pg-hstore  # for PostgreSQL
```

#### Example
```javascript
const { Sequelize, DataTypes } = require('sequelize');
const sequelize = new Sequelize('database', 'username', 'password', {
  host: 'localhost',
  dialect: 'postgres'
});

const User = sequelize.define('User', {
  username: {
    type: DataTypes.STRING,
    allowNull: false
  },
  birthday: {
    type: DataTypes.DATE,
    allowNull: false
  }
});

sequelize.sync()
  .then(() => User.create({
    username: 'john_doe',
    birthday: new Date(1990, 1, 1)
  }))
  .then(user => {
    console.log('User created:', user.toJSON());
  });
```
This example demonstrates how to define a model and interact with a PostgreSQL database using Sequelize.
