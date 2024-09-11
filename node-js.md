What is Node JS?  
Node JS is neither a language nor a framework. It is a runtime environment for executing Javascript code on the server-side. The runtime environment is responsible for memory management and convertion of high language code to machine language code. So,  
Express JS is a framework that uses Node JS to execute Javascript code on the server side.

What is a framework?  
A framework is a wrapper over the runtime environment. Which eases the development process by providing built-in methods.

How does Javascript run on client-side and server-side?  
On client-side browsers use the V8 engine to run Javascript code. On the server-side Node JS uses the V8 engine to run Javascript code.

How does a network request from client-side to the browser-side work?  
A user opens a browser and hits the client-side server. If the data is already present there he can perform basic operations on the client-side like filtering, sorting... If the data is not present on the client-side then the request will go to the server-side  
where Node JS and Express JS check the request and then fetch the data from the database and sends it to the client-side which is then presented to the UI on the browser.

Main features of Node JS?

1. Single Threaded
2. Event-Driven Architecture
3. Asynchronous
4. Real-Time Capabilities

What is single-threaded?  
A single-threaded operation performs only one task at a time.

How does Node JS handle multiple tasks if it is a single-threaded language?  
In Node.js, asynchronous flow can be achieved by its single-threaded, non-blocking, and event-driven architecture.  
Suppose,  
If there are 4 tasks (Task1, Task2, Task3, Task4) to be completed for an event. Then below steps will be executed:  
First, Thread T1 will be created.  
Thread T1 initiates Task1, but it won't wait for Task1 to complete. Instead, T1 proceeds to initiate Task2, then Task3 and Task4 (This asynchronous execution allows T1 to efficiently handle multiple tasks concurrently).  
Whenever Task1 completes, an event is emitted.  
Thread T1, being event-driven, responds to this event, interrupting its current task and delivering the result of Task1. And then proceeds with whatever it is doing.

When not to use Node JS?  
It would be best not to use Node JS when the application demands CPU-intensive tasks like image/ video processing.

What is a Module in Node JS?  
A module is a specific functionality (like orders, payments, shipping) that can be easily reused within an application.  
Ideally, In Node JS we represent individual files as modules.

How many ways are there to export module data?  
We can export module data in two ways.

1. module.exports.myFunction = myFunction;
2. exports.myFunction = () => console.log("Hello world")

How to import module data?  
const moduleData = require('./moduleData');

What is the module wrapper function?  
In Node JS each module is wrapped in a function called the module wrapper function. Such that app.js is wrapped in a function and  
when we run node app.js the file is executable.

How many types of modules are there in Node JS?  
There are three types of modules in Node JS.

1. Built-in Modules (File, HTTP, Path, Math)
2. Local Modules (Which we develop in our project)
3. Third-Party Modules (Lodash)

Explain how the request is handled from the back-end side?  
When a request is generated from the front-end server upon receiving it from the back-end server an event is created and for that particular event, a function  
is triggered after the completion of that function a response is sent back to the front-end server.

What is the role of the HTTP module in Node JS?  
An HTTP module creates an HTTP server that listens to HTTP requests.

List some of the advantages of Express JS?

1. Simplified Web Development
2. Middleware Support
3. Flexible Routing System
4. Template Engine Integration

What is a middleware?  
A middleware is a function that handles HTTP requests, performs operations on it, and passes the control to the next middleware in line.

What is the role of app.use() method?  
The app.use(middleware) method is used to execute the middleware functions globally (for every request).

What is the role of the next parameter?  
The next parameter is a callback function which is used to pass control to the next middleware function in the stack.

What is a request pipeline in Express JS?  
A request pipeline contains multiple middleware functions in line.

How many types of middleware are there?

1. Application Level app.use(middleware);
2. Router Level app.use('/example', middleware);
3. Error-handling app.use((err,req,res,next)=>{});
4. Built-in app.use(express.static("public"));
5. Third-party app.use(bodyParser.json());

If you have 5 middleware then in which middleware you will do the error handling?  
I will do the error handling in the last middleware because suppose the error is generated in the 3 middleware and our error middleware is located at the second position  
and when the Node tries to trigger the error middleware it will not be able to find the error middleware.

Example of routing in Express JS?  
app.get('/orders/:orderId', (req,res)=>{});  
or  
app.get('/orders/:orderId', ordersController.getOrderById);

What is a router method? And why do we need it?  
A router method is imported from express and by using it we can export our routes from a seperate file.  
const router = express.Router();  
router.get('/orders/:orderId', (req,res)=>{});

module.exports = router;  
and we can import it by using this syntax  
const router = require("./router");  
app.use("/api", router);

Differences between app.get() and router.get() methods?

1. The app.get() method defines routes automatically on the application objectt while router.get() method is used to define routes on router object.
2. Routes defined using app.get() are automatically mounted on the root path "/" while routes defined using router.get() must be explicitly mounted using app.use() method.
3. The app.get() is not modular and does not support reusability while router.get() method is modular and supports modularity.
