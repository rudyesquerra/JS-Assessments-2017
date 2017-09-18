### Javascript Course Assessment

## Week 5 Assessment

Try your best to answer each question on your own before looking up the answer online. Once you're done writing your first answer, you can google the question and write the best answer you find.

#### 1. Comment this code from an express server to explain what each part is doing.

app.get('/', function (request, response) { //After our ports listens, it routes it to the instructions, which in //this case our app is calling the method .get and responses with 'Hello World' and sends it back to the browser and
// displays it as a web page.
 response.send('Hello World!');
//The function .get has two parameters, the first ones defines the path we want this route to respond, and the second //one is a callback function which contains the 'instructions' of what to do.
});

app.listen(3000, function () { //NOT SURE IF THE ORDER OF METHODS (FIRST LISTEN THEN GETS) IS CORRECT.
 console.log('Example app listening on port 3000!'); //When we run node app.js, our app is listening to the port
//indicated as a first parameter. Once we type the URL into our browser, it makes a request to our server on the port //we defined.
});



#### 2. We have now used both EJS and React to render views with dynamic javascript content (If you want a refresher, take a look at the "Full Stack Express" day). Compare and contrast the two approaches, include a pro and con of each. Which one did you prefer?

// Your answer
Express PROS
Simple and common templating language.
The code that runs in the browser contains very little, if any of the code that runs the app, other than the view itself.

Express CONS
Whenever the client sends a request, this must be managed by the server and send a response.
We need to define several routes, each with their own template.

React PROS
When the user interacts with page elements, the code is all run right in the browser. The only time a single page app needs to interact with the server is when data needs to be fetched or saved. Less requests for the server means a much quicker response.

React CONS
Couldn't find any cons for React other than poor documentation, JSX its hard to understand and the fact that is is difficult to integrate it with an MVC framework.

// Googled answer


#### 3. Sequelize and Express are the Model and Controller portions of our MVC structure. How the two relate and pass information between each other is important to understand but can be hard to follow. Below are some generic events that happen when a browser requests a web page, but they are not in order. Put them in order and also specify whether the task is done by Sequelize or Express. The first step has been given to you as an example:

1. Server is set to "listen" for requests coming in on a port, or range of ports (Express)

----- organize from here down:
5. Incoming requests are handled by the router
4. If incoming requests recquire information from the database, the request is parsed into a SQL query
3. SQL responses are translated into a javascript object
2. The content required for a view is sent back to the browser, along with any additional information required


** Understanding this process will be important to building full stack apps, if you have any questions about this process, write them here and I will answer them with you in the future:

I'm curious about how the structure of our app.js file inside our express app works. The way we write it seems to start with the get method first and then listen to the port, but is obvious that it first listen before we send a response or render something. Could you elaborate a bit more on how this works?


#### 4. We implement back end tests with Jest and Supertest, look back at the "Testing Express" day and do a few minutes of outside research to understand what this code is doing, and what it is testing. Add comments explaining your findings.

** Also comment any piece you don't understand with questions, and I will get back to you.


const request = require('supertest') //Sets up our Express app in a testing environment
const app = require('./App.js')//Defines which file the tests will refer to, it calls the app.

describe('Test the root path', ()=>{ //Describes the test
  it('Should respond to GET', () => { //Starts the test or promise by using the keyword "it"
    return request(app).get('/').then((response)=>{ //From the app, get the response from path '/'
      expect(response.statusCode).toBe(418) //Checks that the response from the server equals to 418
    })
  })

  it('Should respond with a message of "Relax, and have a cup of tea", ()=>{ //Starts describing the promise
    return request(app).get('/').then((response)=>{ //From the app, get the response from path '/'
      expect(response.body.greeting).toBe('Relax, and have a cup of tea') //Expect the string defined after .toBe
      //inside the body in .json format
    })
  })
})


#### 5. What are cookies and sessions? Try to explain what they are, and any differences between them that you remember.

//Your Answer
Cookies is information stored inside the browser that can be used later in URL requests. A session is all the data stored from an amount of time of a specific user.

 //Googled Answer
-Cookies are small files which are stored on a user's computer by their browser. They are designed to hold a modest amount of data specific to a particular client and website, and can be accessed either by the web server or the client computer. This allows the server to deliver a page tailored to a particular user, or the page itself can contain some script which is aware of the data in the cookie and so is able to carry information from one visit to the website (or related site) to the next.

-A session can be defined as a server-side storage of information that is desired to persist throughout the user's interaction with the web site or web application.

#### 6. Try to explain the process of how information from a user can be persisted to a database using a form, the "post" method, sequelize, and express.  Look back at the "Full Stack Express" day for a refresher.

 //Your Answer
We use forms to obtain information from the client or user, then using the post HTTP request method, the user communicates with the server managed by express. From the example in the "Full Stack Express" I couldn't associate sequelize in any way.

 //Googled Answer


 #### 7. What is sequelize "seed" data for? Why can it be helpful as you develop a project?

 //Your Answer
Sequelize data is used to do our tests and/or migrations in a dummy data environment. With this in mind, whenever we got defined what relations between our model and our tables are, we can actually do migrations into our real database.

 //Googled Answer

 Database seeding can be thought of as a way to bootstrap your database by inserting some records into it. This is run after the migrations created table structures for database.
 Seeding could be generally split into 2 types:
 - Dev/test/staging seeding: provide some initial dummy data to test data models or to demo features to customer.
 - Production seeding: bootstrap your database with some essential data (mainly to provide some initial settings for your app)

 Database seeding along with migration provide a way to package your app and its database as a whole to make it easier to deploy into any server.

https://stackoverflow.com/questions/41298745/why-we-need-sequelize-seed


 #### 8. Red, Green, Refactor is the process for TDD - what does this mean to you right now, and what do you think it might look like to do this in a work environment?
It means that by doing tests, we make sure that we are creating good code. First we make it fail, but define what we want to do, then we code to make our test pass, finally we can refactor our code if needed to improve by running our test again. In a work environment TDD can give certainty that we are doing a god and reliable job.

 #### 9. This is an example express application on github: https://github.com/shapeshed/express_example. Take a few minutes to go to the address and look around in the files. List a few things here about the project - what do you notice that is different about their setup? What looks familiar from class? What sticks out to you or gives you questions?
I noticed that he used more dependencies that we used in class, like for example 'morgan', 'jade' instead of 'ejs' and others like 'serve-favicon' and 'stylus'. Another thing that caught my attention is that he used 'mocha'as his testing framework. A major finding is that he has a routes folder, where he defines the paths of the app inside a file called 'index.js', while in class we defined our paths in an app.js file. He also runs the server in another file inside a bin folder. This part seems much more complex that we've done in class.
What looks familiar  is the process of creating the app, from the testing, even tough he used a different framework, to how he created views, required the dependencies inside the app.js file and inserted public files in a public folder.


#### 10.  Try to explain what an express router does in your own words.

 //Your Answer
An express router determines how an application responds to a client request to a particular endpoint or path.
