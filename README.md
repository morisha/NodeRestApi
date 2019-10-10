# NodeRestApi

Consider all the software that you use in your life. It doesn’t matter if you’re a developer or a regular user that just casually browses the internet and checks up on social networks. Almost all software that you can identify uses some form of API.

APIs (application programming interfaces) enable software applications to communicate with other pieces of software consistently. Either internally to connect to a component of the application or externally to connect to a service.

Using API-based components and services in development is also a great way of maintaining scalability and productivity as it enables you to develop multiple applications based off of modular and reusable components, allowing scalability and facilitating maintenance.

We should also take into account that multiple online services have front-facing APIs and that you can use them to easily integrate things like social media logins, credit card payments, behavior tracking, and many other functionalities.

Implementing such a variety of services via their APIs can be greatly facilitated by using a common platform for communication, a standardized protocol shared and supported by all of them. We’ll be using REST for that.

REST stands for REpresentational State Transfer and is used to access and manipulate data using several stateless operations. These operations are integral to the HTTP protocol and represent an essential CRUD functionality (Create, Read, Update, Delete).

The HTTP operations available are:

POST (create a resource or generally provide data)
GET (retrieve an index of resources or an individual resource)
PUT (create or replace a resource)
PATCH (update/modify a resource)
DELETE (remove a resource)
Using the above-listed operations and a resource name as an address, we can build a REST API by basically creating an endpoint for each operation. And by implementing the pattern, we will have a stable and easily understandable foundation enabling us to evolve the code rapidly and maintain it afterward. As mentioned before, the same foundation will be used to integrate third-party features, most of which likewise use REST APIs, making such integration faster.

While a multitude of platforms and programming languages can be used to build a REST API, in this article, we will be focusing on Node.js.

Node.js is a JavaScript runtime environment that runs server-side. Within that environment, we can use JavaScript to build our software, our REST APIs, and invoke external services through their APIs. This fact is especially convenient for developers who are crossing over from front-end development as they should already be familiar with JavaScript, making the transition more natural. It also has the bonus of unifying all of the codebase under a single programming language.

As an infrastructure, Node.js is designed for building scalable network applications. It is also relatively simple to set up on a local machine, and you can have your server running with a few lines of code. Even some cloud services such as AWS (Amazon Web Services) run Node.js, enabling you to run a serverless application.

Now, of course, nothing is quite so clear-cut in the real world, and development communities are always ripe with discussions about which programming language is the best and which environment is the most suitable for a specific purpose, but I’ll leave that up to you. If you’re curious, though, you can also find articles on REST APIs in ASP.NET Core, Laravel (PHP), Bottle (Python), and many others.

For now, let’s start creating our secure REST API using Node.js!

In this tutorial, we are going to create a pretty common but practical REST API for a resource called users.

Our resource will have the following basic structure:

id (an auto-generated UUID)
firstName
lastName
email
password
permissionLevel (used to control user’s permissions)
And we will create the following operations for that resource:

[POST] endpoint/users
[GET] endpoint/users (list users)
[GET] endpoint/users/:userId (get specific user)
[PATCH] endpoint/users/:userId (update the data for the specified user)
[DELETE] endpoint/users/:userId (remove the specified user)
We will also be using JWT (JSON Web Token) for access tokens, and to that end, we will create another resource called auth that will expect user email and password and in return will generate the token used for authentication on certain operations. If you are interested in knowing more about this, Dejan Milosevic wrote a great article on JWT for secure REST applications in Java a while back; the principles are the same.
