# Files Manager
0x04. Files manager
Back-end
JavaScript
ES6
NoSQL
MongoDB
Redis
NodeJS
ExpressJS
Kue
 Weight: 1
 Project to be done in teams of 2 people (your team: Mohamed Mohamoud)
 Ongoing second chance project - started Aug 29, 2024 6:00 AM, must end by Sep 7, 2024 6:00 AM
 Manual QA review must be done (request it when you are done with the project)
 An auto review will be launched at the deadline
In a nutshell…
Contribution: 100.0%
Manual QA review: In second deadline
Auto QA review: 0.0/86 mandatory
Altogether: waiting on some reviews
This project is a summary of this back-end trimester: authentication, NodeJS, MongoDB, Redis, pagination and background processing.

The objective is to build a simple platform to upload and view files:

User authentication via a token
List all files
Upload a new file
Change permission of a file
View a file
Generate thumbnails for images
You will be guided step by step for building it, but you have some freedoms of implementation, split in more files etc… (utils folder will be your friend)

Of course, this kind of service already exists in the real life - it’s a learning purpose to assemble each piece and build a full product.

Enjoy!

Learning Objectives
At the end of this project, you are expected to be able to explain to anyone, without the help of Google:

how to create an API with Express
how to authenticate a user
how to store data in MongoDB
how to store temporary data in Redis
how to setup and use a background worker
Requirements
Allowed editors: vi, vim, emacs, Visual Studio Code
All your files will be interpreted/compiled on Ubuntu 18.04 LTS using node (version 12.x.x)
All your files should end with a new line
A README.md file, at the root of the folder of the project, is mandatory
Your code should use the js extension
Your code will be verified against lint using ESLint
Provided files
package.json
Click to show/hide file contents
.eslintrc.js
Click to show/hide file contents
babel.config.js
Click to show/hide file contents
and…
Don’t forget to run $ npm install when you have the package.json

Tasks
0. Redis utils
mandatory
Score: 0.0% (Checks completed: 0.0%)
Inside the folder utils, create a file redis.js that contains the class RedisClient.

RedisClient should have:

the constructor that creates a client to Redis:
any error of the redis client must be displayed in the console (you should use on('error') of the redis client)
a function isAlive that returns true when the connection to Redis is a success otherwise, false
an asynchronous function get that takes a string key as argument and returns the Redis value stored for this key
an asynchronous function set that takes a string key, a value and a duration in second as arguments to store it in Redis (with an expiration set by the duration argument)
an asynchronous function del that takes a string key as argument and remove the value in Redis for this key
After the class definition, create and export an instance of RedisClient called redisClient.

bob@dylan:~$ cat main.js
import redisClient from './utils/redis';

(async () => {
    console.log(redisClient.isAlive());
    console.log(await redisClient.get('myKey'));
    await redisClient.set('myKey', 12, 5);
    console.log(await redisClient.get('myKey'));

    setTimeout(async () => {
        console.log(await redisClient.get('myKey'));
    }, 1000*10)
})();

bob@dylan:~$ npm run dev main.js
true
null
12
null
