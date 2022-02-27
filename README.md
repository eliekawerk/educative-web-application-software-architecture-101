# web-application-software-architecture-101
web application software architecture educative course 101


## Importance of getting the application architecture right

To successfully create anything, you have to get the base right. Whether it is constructing a building or making a pizza, if we don’t get the base right, we have to start over. Yeah! I know. But there is no other way around.

Building a web application is no different. The architecture is the base and has to be carefully thought through to avoid any major design changes and code refactoring at a later point.

Speaking from experience, you don’t want to delve into re-designing stuff. It sucks up your time like a black hole and has the potential to push your shipping date further down the calendar by months, if not longer. I won’t even bring up the waste of engineering and financial resources caused due to this.

How much we have to refactor largely depends on the stage of the development process we hit an impasse due to hasty decisions made during the initial design phases. So, before we even touch the code and get our hands dirty, we must make the underlying architecture right.

### An overview of the software development process

In the industry, architects, developers and product owners spend a lot of time studying and discussing business requirements. In software engineering jargon, this is known as Requirement Gathering and Analysis.

Once we are done with the business requirements, we sit down and brainstorm the use cases we have to implement. This also involves figuring out the corner cases as early as possible while trying to fit the building blocks together.

Once we understand the business requirements, use cases, including the corner cases, it’s time to start the research on picking the right technology stack to implement our application.

### Proof of concept

After we pick the fitting tech stack, we start writing a POC (Proof of Concept).

Why a POC?

A POC helps us get a closer, more hands-on view of the technology and the primary use case implementation. We get an insight into the pros and cons of the tech, performance, or other technical limitations, if any.

It helps with the learning curve if we’re working with entirely new tech. Additionally, the non-technical people, like the product owners and stakeholders, have something concrete to play with and base their future decisions on.

Now, this is only for an industry scale product. If you are an indie developer or a small group, you can always skip the POC part and start with the main code.

So, we showcase the POC to the stakeholders. If everyone is satisfied, we get a green light to finally get down to creating the main repo and our first dev branch on GitHub or any similar code hosting service the business prefers.

### Course design

## Introduction

I’ll begin the course by discussing the different tiers involved in the software architectural landscape. This is like having a bird’s eye view of the software architecture realm and it is important to be understood well.

### What is a tier?

Think of a tier as both logical and physical separation of components in an application or a service. This separation is at a component level, not the code level.

What do I mean by components?

*  Database
*  Backend application server
*  User interface
*  Messaging
*  Caching etc.

These are the components that make up a web service.

![image](https://user-images.githubusercontent.com/25869911/155874173-2f7432d2-cc62-420d-93b9-1b3f3388decd.png)


### Single-tier applications

In a single-tier application, the user interface, backend business logic, and the database reside in the same machine.

![image](https://user-images.githubusercontent.com/25869911/155874207-ad55aacc-8807-4809-9cb4-314622b95374.png)

Typical examples of single-tier applications are desktop applications like MS Office, PC Games, image editing software like Gimp, Photoshop, etc.

### Upsides of single-tier applications#

The primary upside of single-tier applications is that they have no network latency since every component is located on the same machine. This adds up to the performance of the software.

Two, three and n-tier apps have to send data requests to the backend server often. This adds network latency to the system making the user experience slow compared to single-tier apps. In single-tier apps, the data is readily available since all the components are located in the same machine.

However, the actual performance of a single-tier app largely depends on the application’s hardware requirements and how powerful the machine it runs on is.

Also, when it comes to data privacy and safety, it is of the highest order in single-tier apps since the user’s data always stays in their machine and doesn’t need to be transmitted over a network for persistence.

### Downsides of single-tier applications

One big downside of single-tier apps is that the application’s publisher has no control over the application. Once the software is shipped, no code or feature updates can be made until the customer manually updates it by connecting to the remote server or downloading and installing a patch.

Due to this, in the 90s, there was nothing that the studios could do if their game was shipped with buggy code. They eventually had to face a lot of heat from the gamers due to the buggy nature of their software. This made product testing vital, responsible for making or breaking a business. Software testing had to be thorough since there was no room for any mistakes.

The code in single-tier applications is also vulnerable to being tweaked and reversed engineered. The product security for the app publisher is minimal. An evil person with some effort can get access to the application’s source code, modifying or copying it for profit. This is unlikely in an architecture where the company controls the application server and implements security to fend off the hackers.

Finally, a single-tier applications’ performance and look and feel can be inconsistent as the app rendering largely depends on the configuration of the user’s machine.

## Two-Tier Applications

A two-tier application involves a client and a server. The client contains the user interface with the business logic in one machine. Meanwhile, the backend server includes the database running on a different machine. The database server is hosted by the business and has control over it.

![image](https://user-images.githubusercontent.com/25869911/155874395-325085bf-fb34-4798-9963-b7e4936e4c3b.png)

Why do we need two-tier applications? Why not host the business logic on a different machine and have control over it too?

Also, again isn’t the application code vulnerable to being accessed by a third person?

### The need for two-tier applications

Well, yes! The code is vulnerable. However, there are use cases where two-tier applications come in handy, for instance, a to-do list app or a similar planner or a productivity app.

In these scenarios, even if the code is accessed by a third person, it won’t cause the business much harm. On the contrary, since the business logic and the user interface reside in the same machine, there are fewer network calls to the backend server. This keeps the latency of the application low, proving to be an upside.

Taking a to-do list app as an example, the application makes a call to the database server only when the user has finished creating their list and wants to persist the data.

Another good example of two-tier apps is the browser and mobile app-based games. The game files are pretty heavy, and they only get downloaded on the client once when the user uses the application for the first time. And they make the network calls to the backend only to persist the game state.

Additionally, fewer server calls mean less money spent to keep the servers running, which is naturally economical. However, picking this tier type for our service largely depends on our business requirements and the use case. When designing our system, we can choose to keep the user interface and business logic on the client or move the business logic to a dedicated backend server, making it a three-tier application that we will learn in the lesson up-next.

## Three-Tier Applications

Three-tier applications are pretty popular and largely used on the web. Almost all simple websites like blogs, news websites, etc., are part of this category.

In a three-tier application, the user interface, business logic, and the database all reside on different machines and, thus, have different tiers. They are physically separated.

![image](https://user-images.githubusercontent.com/25869911/155874562-164e750a-f692-4731-9903-b89b2a734703.png)


Let’s take the example of a simple blog. The user interface will be written using HTML, JavaScript, and CSS, the backend application logic will run on a server like Apache and the database will be MySQL. A three-tier architecture works best for simple use cases.

## N-Tier Applications

An n-tier application is an application that has more than three components (user interface, backend server, database) involved in its architecture.

What are those components?

* Cache
* Message queues for asynchronous behavior
* Load balancers
* Search servers for searching through massive amounts of data
* Components involved in processing massive amounts of data
* Components running heterogeneous tech commonly known as web services, microservices, etc.

All the social applications like Instagram, Facebook, TikTok, large-scale consumer services like Uber, Airbnb, online massive multiplayer games like Pokémon Go, Roblox, etc., are n-tier applications. n-tier applications are more popularly known as distributed systems.

### What’s the need for so many tiers?

Two software design principles that are key to explaining this are the single responsibility principle and the separation of concerns.

#### Single responsibility principle

Single responsibility principle means giving one dedicated responsibility to a component and letting it execute it flawlessly, be it saving data, running the application logic or ensuring the delivery of the messages throughout the system.

This approach gives us a lot of flexibility, making management easy. We can have dedicated teams and code repositories for individual components keeping things cleaner.

With the single responsibility principle, the components are loosely coupled in terms of responsibility and making a change to one doesn’t impact the functionality of other components. For instance, upgrading a database server with a new operating system or a patch won’t affect other service components. Even if something amiss happens during the OS installation, just the database will go down. The application as a whole would still be up and only the features requiring the database would be impacted.

The single responsibility principle is why I was never a fan of stored procedures.

Stored procedures enable us to add business logic to the database, which is always a big no. What if, in the future, we want to plug in a different database? Where do we take the business logic? Do we take it to the new database? Or do we refactor the application code and squeeze in the stored procedure logic somewhere?

A database should not hold business logic. It should only take care of persisting the data. This is what the single responsibility principle is, which is why we have separate tiers for separate components.

#### Separation Of concerns

Separation of concerns loosely means the same thing, be concerned about your work only and stop worrying about the rest of the stuff. These principles act at all the levels of the service, be it the tier level or the code level.

Keeping the components separate makes them reusable. Different services can use the same database, messaging server or any other component as long as they are not tightly coupled with each other.

Having loosely coupled components is the way to go. This approach enables us to scale our service easily when things grow beyond a certain scale in the future.

### Difference between layers & tiers

Note: Don’t confuse tiers with the layers of the application. Some prefer to use them interchangeably. However, in the industry, application layers typically mean the user interface, business, service and the data access layers.


![image](https://user-images.githubusercontent.com/25869911/155874921-baab5870-c259-4bfd-b89a-630d4c78bfb2.png)

These layers are at the code level. The difference between layers and tiers is that layers represent the conceptual/logical organization of the code, whereas tiers represent the physical separation of components.

All these layers together can be used in any tiered application. Be it single, two, three or n-tiered. I’ll discuss these layers in detail in the course ahead.

## What is Web Architecture?

Web architecture involves multiple components like a database, message queue, cache, user interface, etc., all running in conjunction to form an online service.


![image](https://user-images.githubusercontent.com/25869911/155875138-babc25d7-a90c-4e16-9cf2-c9c04698c990.png)


### Client-Server Architecture

You already learned a bit about the client-server architecture when we discussed the two-tier, three-tier and n-tier architecture. Now, we look at it in detail.

![image](https://user-images.githubusercontent.com/25869911/155875171-f02da6d4-d8e6-4bbc-89b0-c25195ead881.png)

Client-server architecture is the fundamental building block of the web.

The architecture works on a request-response model. The client sends the request to the server for information and the server responds with it.

Every website you browse, be it a WordPress blog, an application like Facebook, Twitter, or your banking app, is built on the client-server architecture.

A very small percentage of business websites and applications use the peer-to-peer architecture, which differs from the client-server.

### Client

The client holds our user interface. The user interface is the presentation part of the application. It’s written in HTML, JavaScript, CSS and is responsible for the look and feel of the application

The user interface runs on the client. In very simple terms, a client is a gateway to our application. It can be a mobile app, a desktop or a tablet like an iPad. It can also be a web-based console, running commands to interact with the backend server.

![image](https://user-images.githubusercontent.com/25869911/155875303-772b3486-3910-449e-90f9-97dcac9d79b1.png)

### Technologies used to implement clients in web applications

The open-source technologies popular for writing the web-based user interface in the industry are vanilla JavaScript, jQuery, React, Angular, Vue, Svelte, etc. All these libraries are written in JavaScript.

Different platforms require different frameworks and libraries to write the front-end of our application. For instance, mobile phones running Android need a different set of tools than those running Apple or Windows OS.

### Types of Clients

There are primarily two types of clients:

* Thin client
* Thick client (sometimes also called the Fat client)

A thin client is a client that holds just the user interface of the application. It contains no business logic of any sort. For every action, the client sends a request to the backend server, just like in a three-tier application.

![image](https://user-images.githubusercontent.com/25869911/155875464-090eb1b4-95c2-494b-85d9-942557f42698.png)


### Thick client

On the contrary, the thick client holds all or some part of the business logic. These are the two-tier applications. We’ve already been through them.

The typical examples of fat clients are utility apps, online games, and so on.

### Server

#### What is a web server?

The primary task of a web server is to receive the requests from the client and provide the response after executing the business logic based on the request parameters received from the client.

Every online service needs a server to run. Servers running web applications are commonly known as application servers.

![image](https://user-images.githubusercontent.com/25869911/155875547-e556d461-81f3-44e8-ab47-9063782ff74e.png)

Besides the application servers, there are also other kinds of servers with specific tasks assigned. These include:

* Proxy server
* Mail server
* File server
* Virtual server
* Data storage server
* Batch job server and so on

The server configuration and the type can differ depending on the use case. For instance, if we run a backend application code written in Java, we would pick Apache Tomcat or Jetty. For simple use cases such as hosting websites, we would pick the Apache HTTP Server.

In this lesson, we will stick to the application server.

All the components of a web application need a server to run, be it a database, a message queue, a cache, or any other component. In modern application development, even the user interface is hosted separately on a dedicated server.

#### Server-side rendering

Often the developers use a server to render the user interface on the backend and then send the generated data to the client. This technique is known as server-side rendering. I will discuss the pros and cons of client-side vs. server-side rendering further down the course.

### Communication Between the Client and the Server

#### Request-response model

The client and the server have a request-response model. The client sends the request and the server responds with the data.

If there is no request, there is no response.

#### HTTP protocol

The entire communication happens over the HTTP protocol. It is the protocol for data exchange over the World Wide Web. HTTP protocol is a request-response protocol that defines how information is transmitted across the web.

It’s a stateless protocol, and every process over HTTP is executed independently and has no knowledge of previous processes.


#### REST API and API Endpoints

Speaking from the context of modern n-tier web applications, every client has to hit a REST endpoint to fetch the data from the backend.

The backend application code has a REST-API implemented. This acts as an interface to the outside world requests. Every request, be it from the client written by the business or the third-party developers, those who consume our API data have to hit the REST endpoints to fetch the data.

![image](https://user-images.githubusercontent.com/25869911/155876016-837e8fb4-aac6-4231-97d0-82a006243aad.png)


#### Real world example of using a REST API#

Let’s say we want to write an application to keep track of the birthdays of all our Facebook friends. The app would then send us a reminder a couple of days before the birthday of a certain friend.

To implement this, the first step would be to get the data of the birthdays of all our Facebook friends. We would write a client to hit the Facebook Social Graph API, which is a REST-API, to get the data and then run our business logic on the data.

### What is REST ?

REST stands for Representational State Transfer. It’s a software architectural style for implementing web services. Web services implemented using the REST architectural style are known as the RESTful web services.

A REST API is an API implementation that adheres to the REST architectural constraints. It acts as an interface. The communication between the client and the server happens over HTTP. A REST API takes advantage of the HTTP methodologies to establish communication between the client and the server. REST also enables servers to cache the response that improves the application’s performance.

![image](https://user-images.githubusercontent.com/25869911/155876168-2fd02d83-4fe1-4bf9-abc0-2658475e627b.png)


The communication between the client and the server is a stateless process. By that, I mean every communication between the client and the server is like a new one.

There is no information or memory carried over from the previous communications. So, every time a client interacts with the backend, the client has to send the authentication information to it as well. This enables the backend to figure out whether the client is authorized to access the data or not.

When implementing a REST API, the client communicates with the backend endpoints. This entirely decouples the backend and the client code.

#### REST endpoint

An API/REST/Backend endpoint means the URL of the service that the client could hit. For instance, https://myservice.com/users/{username} is a backend endpoint for fetching the user details of a particular user from the service.

The REST-based service will expose this URL to all its clients to fetch the user details using the above stated URL.

### Decoupling clients and the backend service

With the availability of the endpoints, the backend service does not have to worry about the client implementation. It just calls out to its multiple clients and says, “Hey Folks! Here is the URL address of the resource/information you need. Hit it when you need it. Any client with the required authorization to access a resource can access it”.

With the REST implementation, developers can have different implementations for different clients, leveraging different technologies with separate codebases. Different clients accessing a common REST API could be a mobile browser, a desktop browser, a tablet or an API testing tool. Introducing new types of clients or modifying the client code does not affect the functionality of the backend service.

This means the clients and the backend service are decoupled.

### Application development before the REST API

Before the REST-based API interfaces became mainstream in the industry, we often tightly coupled the backend code with the client. Java Server Pages (JSP) is one example of this.

We would always put business logic in the JSP tags. This made code refactoring and adding new features difficult because the business logic spread across different layers.

Also, on the backend, we had to write separate code/classes for handling requests from different types of clients. We needed a separate servlet for handling requests from a mobile client and a separate one for a web-based client.

After REST APIs implementation backend developers didn’t need to worry about the type of the client. All the devs had to do was provide the service endpoints to the clients and they would receive the response in a standard data transport format like JSON. It was now the responsibility of the clients to parse and render the response data.

This cut down a lot of unnecessary work for the backend developers. Also, adding new clients became a lot easier. Now, with REST, we can introduce any number of new clients without having to worry about the backend implementation.

In today’s application development landscape, there is hardly any online service implemented without a REST API. Want to access the public data of any social network? Just use their REST API.

#### API Gateway

![image](https://user-images.githubusercontent.com/25869911/155876426-1128764e-d758-44da-9d65-3cc60ccc5f8b.png)

The REST-API acts as a gateway or a single-entry point into the system. It encapsulates the business logic and handles all the client requests, taking care of the authorization, authentication, sanitizing the input data, and other necessary tasks before providing access to the application resources.

So, now we are aware of the client-server architecture. We also know what a REST API is. It acts as the interface, and the communication between the client and the server happens over HTTP.

### HTTP Push and Pull - Introduction

There are two modes of data transfer between the client and the server: HTTP PUSH and HTTP PULL.

Let’s find out what they are and what they do.

#### HTTP PULL

As I stated earlier, for every response, there has to be a request first. The client sends the request and the server responds with the data. This is the default mode of HTTP communication, called the HTTP PULL mechanism.

The client pulls the data from the server whenever required. It keeps doing this over and over to fetch the latest data.

An important thing to note here is that every request to the server and the response to it consumes bandwidth. Every hit on the server costs the business money and adds to the load on the server.

What if there is no updated data available on the server every time the client sends a request?

The client doesn’t know that, so naturally, it would keep sending the requests to the server over and over. This is not ideal and a waste of resources. Excessive pulls by the clients have the potential to bring down the server.

#### HTTP PUSH

To tackle this, we have the HTTP PUSH-based mechanism. In this mechanism, the client sends the request for certain information to the server just once. After the first request, the server keeps pushing the new updates to the client whenever they are available.

The client doesn’t have to worry about sending additional requests to the server for data. This saves a lot of network bandwidth and cuts down the load on the server by notches.

This is also known as a callback. The client phones the server for information. The server responds, “Hey!! I don’t have the information right now, but I’ll call you back whenever it is available”.

A very common example of this is user notifications. We have them in almost every web application today. We get notified whenever an event happens on the backend.

Clients use Asynchronous JavaScript & XML (AJAX) to send requests to the server in both the HTTP PULL and the HTTP PUSH mechanism.

There are multiple technologies involved in the HTTP PUSH-based mechanism, such as:

* Ajax Long polling
* Web Sockets
* HTML5 Event Source
* Message Queues
* Streaming over HTTP

### HTTP Pull - Polling With AJAX

The first is sending an HTTP GET request to the server manually by triggering an event on the user interface by clicking a button or interacting with any other element on the web page.

The other is pulling data dynamically at regular intervals using AJAX without any human intervention.

#### AJAX – Asynchronous JavaScript and XML

AJAX stands for Asynchronous JavaScript and XML. The name says it all. AJAX is used for adding asynchronous behavior to the web page.

![image](https://user-images.githubusercontent.com/25869911/155876841-41b941c8-ba91-4022-a3b3-832b524af6e0.png)


As you can see in the illustration above, instead of requesting the data manually every time with the click of a button, AJAX enables us to fetch the updated data from the server by automatically sending the requests over and over at stipulated intervals.

Upon receiving the updates, a particular section of the web page is updated dynamically by the callback method. We see this behavior all the time on news and sports websites, where the updated event information is dynamically displayed on the page without needing to reload it.

AJAX uses an XMLHttpRequest object to send the requests to the server. This object is built in the browser and uses JavaScript to update the HTML DOM (Document Object Model).

AJAX is commonly used with the jQuery framework to implement the asynchronous behavior on the UI.

This dynamic technique of requesting information from the server at regular intervals is known as polling.

It is important to note here that AJAX polling and AJAX Long polling are different techniques. Do not confuse them as one.

AJAX polling is the HTTP Pull mechanism and AJAX Long polling is a hybrid between the HTTP Push and the Pull, based on the BAYEUX protocol. I’ve discussed it in the HTTP Push-based technologies lesson.

### HTTP Push

#### Time to Live (TTL)

Time to Live (TTL)

In the regular client-server communication, which is HTTP PULL, there is a Time to Live (TTL) for every request. It could be 30 secs to 60 secs, varying from browser to browser.

If the client doesn’t receive a response from the server within the TTL, the browser kills the connection and the client has to re-send the request hoping it receives the data from the server before the TTL ends again.

Open connections consume resources, and there is a limit to the number of open connections a server can handle at one point. If the connections don’t close and new ones are introduced regularly over time, the server will run out of memory. Hence, the TTL is used in client-server communication.

But what if we are certain that the response will take more time than the TTL set by the browser?

#### Persistent connection

A persistent connection is a network connection between the client and the server that remains open for future requests and responses, as opposed to being closed after a single communication.

This facilitates HTTP PUSH-based communication between the client and the server.

![image](https://user-images.githubusercontent.com/25869911/155877146-34681780-ea49-4dfb-bf25-a08936e451fd.png)

#### Heartbeat interceptors

Now you might wonder how a persistent connection is possible if the browser kills the open connections to the server every x seconds?

The connection between the client and the server stays open with the help of Heartbeat Interceptors.

These are just blank request responses between the client and the server to prevent the browser from killing the connection.

Isn’t this resource-intensive?

#### Resource intensive

Yes, it is. Persistent connections consume a lot of resources compared to the HTTP PULL behavior. However, there are use cases where establishing a persistent connection is vital to an application’s feature.

For instance, a browser-based multiplayer game has a pretty large amount of request-response activity within a limited time than a regular web application.

It would be apt to establish a persistent connection between the client and the server in this use case from a user experience standpoint.

Long opened connections can be implemented by multiple techniques such as AJAX Long Polling, Web Sockets, Server-Sent Events, etc.

Let’s take a look into each of these methods in the lesson up next.

### HTTP Push-Based Technologies

#### Web Sockets

A Web Socket connection is preferred when we need a persistent bi-directional low latency data flow from the client to the server and back.

Typical use-cases of web sockets are messaging, chat applications, real-time social streams, browser-based massive multiplayer games, etc. These are apps with quite a significant number of read writes compared to a regular web app.

With web sockets, we can keep the client-server connection open as long as we want.

Have bi-directional data? Go ahead with web sockets. One more thing, web sockets don’t work over HTTP. The mechanism runs over TCP. Also, the server and the client should both support web sockets. Else it won’t work.

The WebSocket API and Introducing WebSockets – Bringing Sockets to the Web are good resources for further reading on web sockets.

https://www.html5rocks.com/en/tutorials/websockets/basics/
https://developer.mozilla.org/en-US/docs/Web/API/WebSockets_API

#### AJAX – Long polling

Long polling lies somewhere between AJAX and Web Sockets. In this technique, instead of immediately returning the empty response, the server holds the response until it finds an update to be sent to the client.

The connection in long polling stays open a bit longer compared to polling. The server doesn’t return an empty response. If the connection breaks, the client has to re-establish the connection to the server.

The upside of using this technique is that there are fewer requests sent from the client to the server than the regular polling mechanism. This cuts down a lot of network bandwidth consumption.

Long polling can be used in simple asynchronous data fetch use cases when you do not want to poll the server every now and then.

#### HTML5 Event-Source API and Server-Sent Events

The Server-Sent Events (SSE) implementation takes a different approach. Instead of the client polling for data, the server automatically pushes the data to the client whenever the updates are available. The incoming messages from the server are treated as events.

Via this approach, the servers can initiate data transmission towards the client once the client has established the connection with an initial request.

This helps eliminate a considerable number of blank request-response cycles cutting down the bandwidth consumption by notches.

To implement the server-sent events, the backend language should support the technology. On the UI, HTML5 Event-Source API is used to receive the incoming data from the backend.

An important thing to note here is that once the client establishes a connection with the server, the data flow is in one direction only, from the server to the client.

SSE is ideal for scenarios like a real-time Twitter feed, displaying stock quotes on the UI, real-time notifications, etc.

This is a good resource for further reading on SSE.

https://developer.mozilla.org/en-US/docs/Web/API/Server-sent_events

#### Streaming over HTTP

Streaming over HTTP is ideal for cases where we need to stream extensive data over HTTP by breaking it into smaller chunks. This is made possible with HTML5 and a JavaScript Stream API.

![image](https://user-images.githubusercontent.com/25869911/155877678-2bf89077-34a3-4d99-ac9c-501f66eea8c2.png)

Both the client and the server must agree to conform to the streaming settings to stream data. This helps them determine when the stream begins and ends over an HTTP request-response model.

The technique is primarily used for streaming multimedia content, like large images, videos, etc., over HTTP. Empowered by this technique, we can watch a partially downloaded video as it downloads by playing the downloaded chunks on the client.

For further reading on Stream API, this is a good resource.

https://developer.mozilla.org/en-US/docs/Web/API/Streams_API/Concepts

#### Summary

So, now we understand what HTTP Pull and Push are. We went through different technologies that help us establish a persistent connection between the client and the server.

Every tech has a specific use case, and AJAX is used to dynamically update the web page by polling the server at regular intervals.

Long polling has a connection open time slightly longer than the polling mechanism.

Web Sockets have bi-directional data flow, whereas server-sent events facilitate data flow from the server to the client.

Streaming over HTTP facilitates the streaming of large objects like multimedia files.

What tech would fit best for our use case depends on the application we intend to build.

In the next lesson, let’s gain an insight into the pros and cons of the client and the server-side rendering.

### Client-Side vs. Server-Side Rendering

#### Client-side rendering - How does a browser render a web page?

When a browser receives a web page from the server in response, it has to render the response on the window in the form of an HTML page.

To pull this off, the browser has several components, such as:

* The browser engine
* Rendering engine
* JavaScript interpreter
* Networking and the UI backend
* Data storage etc.

I won’t go into much detail; the gist is the browser has to do a lot of work to convert the response from the server into an HTML page. The rendering engine constructs the DOM tree and renders and paints the construction and so on.

Naturally, all this activity takes some time before the user can interact with the page.

#### Server-side rendering

To cut down all this rendering time on the client, developers often render the UI on the server, generate HTML there and directly send the HTML page to the UI.

This technique is known as server-side rendering. It ensures faster rendering of the UI, averting the UI loading time in the browser window because the page is already created and the browser doesn’t have to do much assembling and rendering work.

Here are some use cases for both approaches of rendering the UI—on the client and the server.

#### Use cases for server-side & client-side rendering

The server-side rendering approach is perfect for delivering static content, such as WordPress blogs. It’s also good for SEO because the crawlers can easily read the generated content.

However, modern websites are highly dependent on AJAX. On such websites, content for a particular module or a page section has to be fetched and rendered on the fly. In this use case, the server-side rendering doesn’t help much.

If we render the UI on the server for AJAX-based websites, for every AJAX request, the approach will generate the entire page on the server as opposed to just sending the updated content to the client in response.

This process will prove to be resource-intensive and would consume unnecessary bandwidth, failing to provide a smooth user experience.

Also, once the number of concurrent users on the website goes up, server-side rendering will exert an unnecessary load on the server.

So, for modern dynamic AJAX-based websites, the client-side rendering works best.

Moreover, we can leverage a hybrid approach to get the best of both worlds. We can use server-side rendering for the static content of our website and client-side rendering for dynamic content.

Okay, before we move on to the database, message queue and caching components, it’s essential for us to understand concepts such as:

* Scalability
* High availability
* Load balancing
* Monolith and microservices
* Understanding these concepts will help us understand the rest of the web components better.

### What is Scalability?

being in the software development universe, you’ve come across the word scalability numerous times. What is it? Why is it so important? Why is everyone talking about it? What are your plans or contingencies to scale when your app or the platform experiences significant traffic growth?

Scalability means the application’s ability to handle and withstand increased workload without sacrificing performance.

For example, if your app takes x seconds to respond to a user request. It should take the same x seconds to respond to each of your app’s million concurrent user requests.

The app’s back-end infrastructure should not crumble under a load of a million concurrent requests. It should scale well when subjected to a heavy traffic load and maintain the system’s latency.

![image](https://user-images.githubusercontent.com/25869911/155896623-2a2d6e5a-bbba-4e48-9223-4639201f8731.png)


### What is latency?

Latency is the time a system takes to respond to a user request. Let’s say you send a request to an app to fetch an image and the system takes 2 seconds to respond to your request. The latency of the system is 2 seconds.

Minimum latency is what efficient software systems strive for. No matter how much the traffic load on a system builds up, the latency should not go up. This is what scalability is.

If the latency remains the same, we can say that the application scaled well with the increased load and is highly scalable.

Let’s see scalability in terms of Big-O notation. Ideally, the complexity of a system or an algorithm should be O(1) which is constant time like in a map or a key-value database.

A program with the complexity of O(n^2) where n is the size of the data set is not scalable. As the size of the data set increases, the system will need more computational power and other resources to process the tasks.

So, how do we measure latency?

### Measuring latency

Latency is measured as the time difference between the action that a user takes on the website and the system’s response in reaction to that action. The action can be an event like clicking a button, scrolling down a web page, etc.

This latency is generally divided into two parts:

* Network latency
* Application latency

![image](https://user-images.githubusercontent.com/25869911/155896746-75041e8b-6044-4a23-ab22-c47d5d300752.png)

#### Network latency

Network latency is the time that the network takes to send a data packet from point A to point B. The network should be efficient enough to handle the increased traffic load on the website. To cut down the network latency, businesses use a CDN (Content Delivery Network) to deploy their servers across the globe as close to the end-user as possible. These close to the user locations are also known as Edge locations.

After having spent a decade in the industry writing code, I firmly believe that every software engineer should have knowledge of cloud computing. It’s the present and the future of application development and deployment.

#### Application latency

Application latency is the time the application takes to process a user request. There are more than a few ways to cut down the application latency. The first step is to run stress and load tests on the application and scan for the bottlenecks that slow down the system as a whole. I’ll talk more about it in the upcoming lessons.

#### Why is low latency so crucial for online services?

Latency plays a significant role in determining if an online business wins or loses a customer. Nobody likes to wait for a response on a website. There is a well-known saying, “If you want to test a person’s patience, give them a slow internet connection.”

If the visitor gets the response within a stipulated time, great otherwise, they’ll bounce off to another website. There is ample market research that concludes high latency in applications is a big factor in customers bouncing off a website. If there is money involved, zero latency is what businesses want. If only if this was possible.

Think of massive multiplayer online (MMO) games. A slight lag in an in-game event ruins the whole experience. A gamer with a high latency internet connection will have a slow response time despite having the best reaction time of all the players in an arena.

Algorithmic trading services need to process events within milliseconds. Fintech companies have dedicated networks to run low latency trading. The regular network just won’t cut it.

We can realize the importance of low latency by the fact that in 2011 Huawei and Hibernia Atlantic started laying a fiber-optic link cable across the Atlantic Ocean between London and New York. This property was estimated to cost approximately $300M just to save traders six milliseconds of latency.

### Types of Scalability

To scale well, an application needs solid computing power. The servers should be powerful enough to handle increased traffic loads.

There are two ways to scale an application:

* Vertically
* Horizontally

#### What is vertical scaling?

Vertical scaling means adding more power to our server. Let’s say our app is hosted by a server with 16 gigs of RAM. To handle the increased load, we now augment the RAM to 32 gigs. Here, we have vertically scaled the server.

![image](https://user-images.githubusercontent.com/25869911/155896953-0c8a76bd-b4e4-4e96-a220-a142b0f419d6.png)


Ideally, when the traffic starts to build on the app, the first step should be to scale vertically. Vertical scaling is also called scaling up.

In this type of scaling, we augment the power of the hardware running the app. This is the simplest way to scale as it doesn’t require any code refactoring or the need to make any complex configurations and so on. I’ll discuss in the next lesson why code refactoring is needed when we horizontally scale our app.

However, there is only so much we can do when scaling vertically. There is a limit to the compute power we can augment for a single server.

A good analogy would be to think of a multi-story building. We can keep adding floors to it but only up to a certain point. What if the number of people in need of a flat keeps rising? We can’t scale the building up to the moon for obvious reasons.

Now is the time to build more buildings. This is where horizontal scalability comes in.

When the traffic is too large to be handled by a single server, we bring in more servers to work together.

#### What is horizontal scaling?

Horizontal scaling, also known as scaling out, means adding more hardware to the existing hardware resource pool. This increases the computational power of the system as a whole.

![image](https://user-images.githubusercontent.com/25869911/155897034-8a2d44a1-ec3c-4cb5-a08b-b4a641c71252.png)

With this, the increased traffic influx can be efficiently dealt with. And there is no limit to how much we can scale horizontally, assuming we have infinite resources. We can keep adding servers after servers, setting up data centers after data centers.

Horizontal scaling also allows us to scale dynamically in real-time as the traffic on our website climbs and drops over a period of time. Dynamic scaling is not possible when scaling vertically.

#### Cloud elasticity

The most prominent reason cloud computing became mainstream in the industry is the ability of the cloud to scale dynamically. In case of the traffic climb, the cloud adds additional servers to the hardware resource pool and when it drops, the servers added are removed.

The ability to use and pay only for the hardware resources used by the website got popular with businesses for obvious economic reasons.

The process of adding and removing servers, stretching and returning to the original infrastructural computational capacity, on the fly is popularly known as cloud elasticity. It saves businesses truckloads of money every single day.

If you wish to know in detail how cloud platforms scale our apps and make them highly available. I’ve discussed the concept in my cloud computing 101 course how clustering works and how cloud companies deploy our apps across continents.

Having multiple server nodes on the backend also helps the website stay online even if a few server nodes crash. This is known as high availability. We’ll get to that in the upcoming lessons.

### Which Scalability Approach is Right for our App?

#### Pros and cons of vertical and horizontal scaling

Vertical scaling, as we learned before, is simpler in comparison to horizontal scaling because we do not have to touch the code or make any complex system configurations. It takes much less administrative, monitoring, and management efforts than managing a distributed environment when scaling horizontally.

A significant downside of vertical scaling is the availability risk. The servers are powerful but few in number. There is always a risk of them going down and the entire website going offline, which doesn’t happen when the system is scaled horizontally. In this scenario, the system is more highly available.

#### What about the code? Why does the code need to change when it has to run on multiple machines?

If you intend to run the code in a distributed environment, it needs to be stateless. There should be no state in the code. What do I mean by this?

There should be no static instances in the class. Static instances hold application data and when a particular server goes down, all the static data/state is lost. The app is left in an inconsistent state.

In object-oriented programming, the instance variables hold object state in them. Static variables moreover hold state that spans across multiple objects. They generally hold state per classloader. Now, if the server instance running that classloader goes down, all the data is lost.

Also, whatever data static variables hold, it’s not application-wide. For this reason, distributed memory like Redis, Memcache, etc., are used to maintain a consistent state application-wide. When writing applications for distributed systems, it’s a good practice to avoid using static instances in the class. The state is typically persisted in a distributed memory store; this facilitates components to be stateless.

This is why functional programming got popular with distributed systems. The functions don’t retain any state. However, the same behavior can also be achieved with prominent OOP languages.

#### Which scalability approach is right for our app?

Always have a ballpark estimate in mind when designing your app. How much traffic will it have to deal with?

Today, development teams are adopting a distributed microservices architecture right from the start, and workloads (applications) are meant to be deployed on the cloud. So, inherently the workloads are horizontally scaled out on the fly

![image](https://user-images.githubusercontent.com/25869911/155897396-50083607-dc82-4f70-97ea-cd7558a13421.png)


The upsides of horizontal scaling include no limit to augmenting the hardware capacity. Data is replicated across different geographical regions as nodes and data centers are set up across the globe.

If your app is a utility or tool expected to receive minimal predictable traffic. For instance, an internal tool of an organization or something similar that is not mission-critical.

Why bother hosting it in a distributed environment? A single server is enough to manage the traffic, so go ahead with vertical scaling when we know that the traffic load will not spike in the future.

If your app is a public-facing social app like a social network, a fitness app, an online game, or something similar, where the traffic is unpredictable. Both high availability and horizontal scalability are important to you.

Build these apps to deploy them on the cloud, and always have horizontal scalability in mind right from the start.

### Primary Bottlenecks That Hurt the Scalability of our Application

There are several points in a web application that can become a bottleneck and hurt the scalability of our application. Let’s take a look at them.

#### Database

Imagine we have an application that appears to be well architected. Everything looks good. The workload runs on multiple nodes, and it can scale horizontally.

However, the database is a poor single monolith, where just one server has the onus of handling the data requests from all the server nodes of the workload.

This scenario is a bottleneck. The server nodes work well, handle millions of requests at a point in time efficiently, yet, the response time of these requests and the latency of the application are abysmal due to the presence of a single database. There is only so much it can handle.

Just like workload scalability, the database needs to be scaled well.

Make wise use of database partitioning, sharding with multiple database servers to make your system efficient.

#### Application design

A poorly designed application’s architecture can become a major bottleneck as a whole.

A typical architectural mistake is not using asynchronous processes and modules wherever required; rather, all the processes are scheduled sequentially.

For example, if a user uploads a document on the portal, tasks such as sending a confirmation email to the user, sending a notification to all subscribers/listeners to the upload event should be done asynchronously.

Tasks like these should be forwarded to a messaging server or a task queue for asynchronous processing as opposed to being processed sequentially, making the user wait.

#### Not using caching in the application wisely

Caching can be deployed at several layers of the application. It speeds up the response time by notches. A cache cuts down the overall load on the app, intercepting all the requests before they hit the origin servers.

We should use caching exhaustively throughout the application to speed up things significantly.

If the system has a lot of static data, caching can bring down the deployment costs significantly. I’ve written an article on my blog: How PolyHaven manages 5 million page views and 80TB traffic a month for less than 400 USD.

Polyhaven is a 3D asset library with a large amount of static data. The article delineates how it leverages caching to bring down it’s deployment costs.

https://www.scaleyourapp.com/application-hosting-how-polyhaven-manages-5-million-page-views-and-80tb-traffic-a-month-for-400/

#### Inefficient configuration and setup of load balancers

Load balancers are the gateway to our application. Using too many or too few of them impacts the latency of our application.

#### Adding business logic to the database

No matter what justification anyone provides, I’ve never been a fan of adding business logic to the database.

The database is just not the place to put business logic. Business logic in the database makes the application components tightly coupled. Imagine how much code refactoring this would require when migrating to a different database. Also, the testing gets complex.

#### Not picking the right database

Picking the right database technology is vital for businesses. Need transactions and strong consistency? Pick a relational database. If you can do without strong consistency rather than need horizontal scalability, pick a NoSQL database.

Trying to pull things off with a not-so-suitable tech always has a profound impact on the latency of the entire application in negative ways.

#### At the code level

This shouldn’t come as a surprise, but inefficient and poorly written code has the potential to bring down the entire service in production. This typically includes:

* Using unnecessary loops or nested loops
* Writing tightly coupled code
* Not paying attention to the Big-O complexity while writing the code. (be ready to do a lot of firefighting in production)

Ideally, we should always do a DENTTAL (Documentation, Exception Handling, Null pointers, Time complexity, Test coverage, Analysis of code complexity, Logging) check of our code when doing a dry run.

In this lesson, don’t worry if a few things are not clear to you, such as strong consistency, how the message queue facilitates asynchronous behavior, or how to pick the right database

### How to Improve and Test the Scalability of our Application?

Here are some of the standard strategies to fine-tune the performance of our web application. If the application is performance-optimized, it can withstand more traffic load with less resource consumption than an application that is not optimized for performance.

Now you might be wondering, “Why are you talking about performance when you should be talking about scalability? Isn’t it what the lesson title says?”

Well, the application’s performance is directly proportional to scalability. If an application is not performant, it will certainly not scale well.

These performance optimization strategies can be implemented even before the pre-production testing stage of the application.

#### Tuning the performance of the application – Enabling it to scale better

##### Profiling

Profile the hell out of your app. Run application profiler and code profiler. See what processes are taking too long and are eating up too many resources. Find out the bottlenecks. Get rid of them.

Profiling is the dynamic analysis of our code. It helps us measure the space and the time complexity of our code and enables us to figure out issues like concurrency errors, memory errors and robustness and safety of the program. This Wikipedia resource contains a good list of performance analysis tools used in the industry.

https://en.wikipedia.org/wiki/List_of_performance_analysis_tools

##### Caching

Cache wisely, and cache everywhere. Cache all the static content. Hit the database only when it is really required. Try to serve all the read requests from the cache. Use a write-through cache.

##### CDN

Use a Content Delivery Network (CDN). Using a CDN further reduces the application’s latency due to the proximity of the data from the requesting user.

##### Data compression

Compress data. Use apt compression algorithms to compress data and store data in compressed form. Since compressed data consumes less bandwidth, the data download on the client will be faster.

##### Avoid unnecessary requests response cycles

Avoid unnecessary round trips between the client and server. Try to club multiple requests into one.

These are a few of the things we should bear in mind in the context of application performance.

##### Testing the scalability of our application

Once we are done with the essential performance testing of the application, it is time for capacity planning, provisioning the right amount of hardware—compute and storage power.

The right approach for testing the application for scalability largely depends on the design of our system. There is no standard formula for this.

Testing can be performed at both the hardware and the software level. Different services and components need to be tested—individually and collectively.

During the scalability testing, different system parameters are taken into account, such as:

* CPU usage
* Network bandwidth consumption
* Throughput
*  Number of requests processed within a stipulated time
* Latency
* Memory usage of the program
* End-user experience when the system is under heavy load and so on.

In this testing phase, simulated traffic is routed to the system to study how the system behaves and scales under the heavy load. Contingencies are planned for unforeseen situations.

As per the anticipated traffic, the appropriate hardware and computational power are provisioned to handle the traffic smoothly with some buffer.

Several load and stress tests are run on the application. Tools like JMeter are pretty popular for running concurrent user tests on the application; if you are on the Java ecosystem. There are a lot of cloud-based testing tools available that help us simulate test scenarios just with a few mouse clicks.

Businesses test for scalability all the time to get their systems ready to handle a traffic surge. If it’s a sports website, it prepares itself for the sports event day. If it’s an e-commerce website, it makes itself ready for festival season sale.

Here are a couple of good reads on the topic:

https://engineering.fb.com/2018/02/12/production-engineering/how-production-engineers-support-global-events-on-facebook/

https://www.scaleyourapp.com/how-hotstar-scaled-with-10-3-million-concurrent-users-an-architectural-insight/

In the industry, tech like Cadvisor, Prometheus and Grafana are pretty popular for tracking the system profile via web-based dashboards.

![image](https://user-images.githubusercontent.com/25869911/155898161-196e4a0e-94bb-4259-8362-5f7216b0ede3.png)

https://www.scaleyourapp.com/what-is-grafana-why-use-it-everything-you-should-know-about-it/

### What is High Availability?

Highly available computing infrastructure is the norm in the computing industry today. When it comes to cloud platforms, it is their key feature that enables the workloads running on them to be highly available.

This lesson is an insight into high availability. It covers all the frequently asked questions about it, including:

* What is it?
* Why is it so important to businesses?
* What is a highly available cluster?
* How do cloud platforms ensure the high availability of the services running on them?
* What are fault tolerance and redundancy? How are they related to high availability?

High availability, also known as HA, is the ability of the system to stay online despite having failures at the infrastructural level in real-time.

High availability ensures the service’s uptime is much more than usual. It improves the reliability of the system and ensures minimum downtime.

Reliability is defined as the probability that a product, system, or service will perform its intended function adequately for a specified period of time, or will operate in a defined environment without failure.

The sole mission of highly available systems is to stay online and stay connected. A rudimentary real-world example of staying highly available is having backup generators to ensure continuous power supply in case of any power outages in hospitals, air traffic control towers and so on.

In the industry, HA is often expressed as a percentage. For instance, when the system is 99.99999% highly available, it simply means 99.99999% of the total hosting time the service will be up. You might often see this in the Service Level Agreements (SLA) of cloud platforms.

#### How important is high availability to online services?

Social applications going down for a bit and then bouncing back might not impact businesses that much. However, there are mission-critical systems like aircraft systems, spacecrafts, mining machines, hospital servers, and finance stock-market systems that cannot afford to go down at any time. After all, lives depend on it.

The smooth functioning of the mission-critical systems relies on continual connectivity with their network/servers. These are the instances that do not work without super highly available infrastructures.

Besides, no service likes to go down, critical or not. To meet the high availability requirements, systems are designed to be fault-tolerant and their components are made redundant.

What are fault-tolerant and redundancy in distributed systems?

Fault Tolerance simply means a system's ability to continue operating uninterrupted despite the failure of one or more of its components. This is true whether it is a computer system, a cloud cluster, a network, or something else.


### Reasons For System Failures

common reasons why systems fail.

#### Software crashes

I am sure you are pretty familiar with software crashes. Applications crash all the time, be it on a mobile phone or a desktop.

We also have to deal with corrupt software files. Remember the BSOD blue screen of death in Windows? OS crashing, memory-hogging unresponsive processes. Likewise, software running on cloud nodes crashes unpredictably and takes down the entire node.

#### Hardware failures

Another reason for system failure is hardware crashes, including overloaded CPU and RAM, hard disk failures, nodes going down, and network outages.

#### Human errors

This is the biggest reason for system failures. It includes flawed configurations and whatnot. Google made a tiny network configuration error, and it took down almost half of the internet in Japan

https://thenextweb.com/news/google-japan-internet-blackout

#### Planned downtime

Besides the unplanned crashes, there are planned downtimes that involve routine maintenance operations, patching software, hardware upgrades, etc.

These are the primary reasons for system failures. Now, let’s talk about how HA systems are designed to overcome these system downtime scenarios.

### Achieving High Availability - Fault Tolerance

There are several approaches to achieve HA. The most important of them is to make the system fault-tolerant.

#### What is fault tolerance?

Fault tolerance is a system’s ability to stay up despite taking hits.

A fault-tolerant system is equipped to handle faults. Being fault-tolerant is an essential element in designing life-critical systems.

In a fault-tolerant system, out of several instances/nodes running a service, a few go offline and bounce back all the time. In case of these internal failures, the system can work at a reduced level without going down entirely.

An elementary example of a system like this is social networking platforms. In the case of backend node failures, a few services of the app, such as image upload, post likes, etc., may stop working. However, the application as a whole will still be up. This approach technically is also known as fail soft.

#### A highly available fault-tolerant service – Architecture

A fault-tolerant system can be designed at the application and the deployment level. Since apps are typically deployed on the cloud in the modern web landscape, I discuss the deployment infrastructure in detail in my cloud computing course.

So, to achieve high availability at the application level, the entire massive service is architecturally broken down into more granular loosely coupled services called microservices.

![image](https://user-images.githubusercontent.com/25869911/155898838-6afcd9e7-1fd8-411e-93b9-9abe589913c2.png)


There are many upsides of splitting a big monolith into several microservices:

* Easy management and maintenance
* Ease of development
* Ease of adding new features to a service without affecting other services
* Scalability and high availability of the system

Every microservice takes the onus of running different features of an application such as photo upload, comment system, instant messaging, groups, marketplace, etc. In this case, even if a few services go down, the other services of the application are still up.

### Redundancy

#### Redundancy – Active-passive HA mode

Redundancy is duplicating the server instances and keeping them on standby to take over in case any of the active server instances go down. It is the fail-safe backup mechanism in the deployment infrastructure.

![image](https://user-images.githubusercontent.com/25869911/155899006-b51e035b-4c25-4569-b7cd-aaf76d02cf58.png)

The illustration above shows the redundant instances. One of the redundant instances takes over when the active instance goes offline.

This instance setup approach is also known as the Active-passive HA mode. An initial set of nodes are active, and a set of redundant nodes are passive, on standby. Active nodes get replaced by passive nodes in case of failures.

There are systems like GPS, aircraft, communication satellites, etc., that have zero downtime. The availability of these systems is ensured by making the components redundant.

#### Getting rid of single points of failure

Distributed systems became mainstream with large-scale applications solely because, in them, we can eliminate the single points of failure that were a big downside of a monolithic architecture. I discussed this in the previous lesson how microservices facilitate a fault-tolerant architecture.

In a highly available system, a large number of distributed server nodes work in conjunction with each other to achieve a single synchronous application state.

When so many redundant nodes are deployed, there are no single points of failure in the system. In case a node goes down, redundant nodes take its place. The system as a whole remains unimpacted.

Single points of failure at the application component level mean bottlenecks. I discussed this earlier, having just one database instance handling requests from a number of application nodes. We should detect bottlenecks in performance testing and get rid of them as soon as possible.

#### Monitoring and automation

Systems should be well monitored in real-time to detect any bottlenecks or single point of failures. Automation enables the instances to self-recover without any human intervention. It gives the instances the power of self-healing.

Also, the systems become intelligent enough to add or remove instances on the fly as per the requirements. Kubernetes is one good example of this.

Since the most common cause of failures is human error, automation helps cut down failures considerably.

### Replication

Replication – Active-active HA mode

Replication means having a number of similar nodes running the workload together. There are no standby or passive instances. When a single or a few nodes go down, the remaining nodes bear the load of the service.

![image](https://user-images.githubusercontent.com/25869911/155899180-e2cddd5d-0ed7-4e63-a2e6-872aec09c7cd.png)

This approach is also known as the Active-active high availability mode. In this approach, all the server instances are active at any point in time.

#### Geographical distribution of workload#

As a contingency for natural disasters, regional power outages, and other big-scale failures, data center workloads are spread across different data centers across the world in different geographical locations.

This eliminates a single point of failure in the context of data center zones. If a natural disaster wipes out a few data centers in a certain zone, other data centers in different geographical zones are still powering the application. Also, the latency is reduced significantly due to the proximity of data to the user due to the global replication of data centers.

All highly-available fault-tolerant design decisions are subjective to how critical the system is? The odds of components failing and so on.

Businesses often use multi-cloud platforms to deploy their workloads which ensures further availability. If things go south with one cloud provider, they have another to fail back over.

#### High Availability Clustering

A high availability cluster, also known as the fail-over cluster, contains a set of nodes running in conjunction with each other that ensures the high availability of the service.

The nodes in the cluster are connected by a private network called the heartbeat network that continuously monitors the health and the status of each node in the cluster.

A single state across all the nodes in a cluster is achieved with the help of a shared distributed memory and a distributed coordination service like the Zookeeper.

![image](https://user-images.githubusercontent.com/25869911/155899795-78c43f88-49cc-423a-ac16-7b82fc558223.png)

To ensure availability, HA clusters use several techniques such as disk mirroring/Redundant Array of Independent Disks (RAID), redundant network connections, redundant electrical power, etc. All the possible components having a single point of failure are made redundant to ensure the availability of the service.

Multiple HA clusters run together in one geographical zone ensuring minimum downtime and continual service. If you wish to delve more into clustering please go through my cloud course.

Alright, Folks! So now we have a pretty good understanding of scalability and high availability. These two concepts are crucial to software system desig

### Introduction to Load Balancing

Introduction to Load Balancing

Load balancers distribute heavy traffic load across the servers running in the cluster based on several different algorithms. This averts the risk of all the traffic converging to a single or a few machines in the cluster.

Load balancing enables our service to scale well and stay highly available when the traffic load increases. Load balancing is facilitated by load balancers, making them a key component in the web application architecture.

Load balancers distribute heavy traffic load across the servers running in the cluster based on several different algorithms. This averts the risk of all the traffic converging to a single or a few machines in the cluster.

If the entire traffic on a particular service converges only to a few machines, this will cause an overload, subsequently spiking the latency, also bringing down the application’s performance. The excess traffic might also result in the server nodes going offline. Load balancing helps us avoid all this mess.

While processing a user request, if a server goes down, the load balancer automatically routes the future requests to other up and running server nodes in the cluster. This enables the service as a whole to stay available.

Load balancers act as a single point of contact for all the client requests.


![image](https://user-images.githubusercontent.com/25869911/155899997-b306b2ab-b66e-4c85-813a-b9f7b1b08dd5.png)

They can also be set up at the application component level to efficiently manage traffic directed towards any application component, be it the backend application server, database component, message queue, or any other. This is done to uniformly spread the request load across the machines in the cluster powering that particular application component.

![image](https://user-images.githubusercontent.com/25869911/155900041-9d6556b6-19f0-433e-a150-ee706729157e.png)

#### Performing health checks of the servers with load balancers

To intelligently route all the user requests to the active nodes in the cluster, a load balancer should be well aware of their running status.

To ensure that the user request is always routed to the machine that is up and running, load balancers regularly perform health checks on the machines in the cluster.

![image](https://user-images.githubusercontent.com/25869911/155900079-adefd1fe-0014-407c-ba56-58c0175caee2.png)

Ideally, a load balancer maintains a list of machines that are up and running in the cluster in real-time, and the user requests are forwarded to only those machines in service. If a machine goes down, it is removed from the list.

Machines that are up and running in the cluster are known as in-service machines, and the servers that are down are known as out-of-service instances.

For the record, Node, Server, Server Node, Instance, and Machine all mean the same thing and can be used interchangeably.

After the out-of-service instance comes back online and becomes in-service, the load balancer updates its list and starts routing the future requests to that particular instance all over again.

Okay! In the next few lessons, you will discover how load balancers work. To understand that well, you need to first understand the Domain Name System (DNS) that we will discuss in the lesson up next.

### Understanding DNS – Part 1

Every machine that is online and is a part of the World Wide Web (WWW) has a unique IP address that enables it to be contacted by other machines on the web using that particular IP address.

IP stands for Internet Protocol. It’s a protocol that facilitates the delivery of data packets from one machine to another using their IP addresses.

2001:db8:0:1234:0:567:8:1 - This is an example of a machine’s IP address. The server that hosts our website will have a similar IP address. To fetch content from that server, a user has to type in the unique IP address of the server in their browser’s URL tab and hit enter to interact with the website’s content.

Naturally, it is not viable to type in the website’s IP address from memory every time we visit a particular website. Even if we try to, how many IP addresses do you think you can remember?

Typing in domain names, for instance, amazon.com, is a lot easier than working directly with IP addresses. I think we can all agree on this.

#### Domain name system

Domain name system, commonly known as DNS, is a system that averts the need to remember long IP addresses to visit a website by mapping easy-to-remember domain names to IP addresses.

amazon.com is a domain name that is mapped to its unique IP address by the DNS so that we are not expected to type in the IP address of amazon.com into our browsers every time we visit that website.

Now let’s explore how DNS works?

#### How does a domain name system work?

When a user types in the URL of the website in their browser and hits enter, this event is known as DNS querying.

Four key components, or a group of servers, make up the DNS infrastructure. These are:

* DNS Recursive nameserver aka DNS Resolver
* Root nameserver
* Top-Level Domain nameserver
* Authoritative nameserver

![image](https://user-images.githubusercontent.com/25869911/155900264-95fa4c66-e7ff-466b-b8d5-a95fd6c06ee0.png)

### Understanding DNS – Part 2

In this lesson, you will get an insight into the complete DNS query lookup process and understand the role of different servers in the DNS infrastructure.

When the user hits enter after typing in the domain name into their browser, the browser sends a request to the DNS Recursive nameserver, also known as the DNS Resolver.

The role of DNS Resolver is to receive the client request and forward it to the Root nameserver to get the address of the Top-Level domain nameserver.

The DNS Recursive nameserver is generally managed by our ISP (Internet service provider). The whole DNS system is a distributed system setup in large data centers managed by internet service providers.

These data centers contain clusters of servers optimized to process DNS queries in minimal time in milliseconds.

Once the DNS Resolver forwards the request to the Root nameserver, the Root nameserver returns the address of the Top-Level domain nameserver in response. As an example, the top-level domain for amazon.com is .com.

Once the DNS Resolver receives the address of the top-level domain nameserver, it sends a request to it to fetch the details of the domain name. Top Level domain nameservers hold the data for domains using their top-level domains.

For instance, the .com top-level domain nameserver will contain information on domains using .com. Similarly, a .edu top-level domain nameserver will hold information on domains using .edu.

Since our domain is amazon.com, the DNS Resolver will route the request to the .com top-level domain name server.

Once the top-level domain name server receives the request from the Resolver, it returns the IP address of the amazon.com domain name server.

amazon.com domain nameserver is the last server in the DNS query lookup process. This nameserver is responsible for the amazon.com domain and is also known as the Authoritative nameserver. The owner of the domain name owns this nameserver.

Then, DNS Resolver fires a query to the Authoritative nameserver, and it returns the IP address of the amazon.com website to the DNS Resolver.

DNS Resolver caches the data and forwards it to the client.

On receiving the response, the browser sends a request to the amazon.com website’s IP address to fetch data from their servers.

Often all this DNS information is cached, and the DNS servers don’t have to do so much rerouting every time a client requests an IP of a certain website.

The DNS information of websites that we visit also gets cached in our local machines, that is, our browsing devices with a TTL (Time to live).

All modern browsers do this automatically to cut down the DNS query lookup time when revisiting a website.

This is how the entire DNS query lookup process works.

![image](https://user-images.githubusercontent.com/25869911/155900490-6a6061b3-033e-41c9-b588-5b50daa6126d.png)


### DNS Load Balancing

To spread the user traffic across different clusters in different data centers. There are various ways to set up load balancing. In this lesson, we will discuss DNS load balancing, which is set up at the DNS level on the authoritative server.

![image](https://user-images.githubusercontent.com/25869911/155900605-d597a7b4-0e86-4c6d-afe5-94b76d8e519b.png)

DNS load balancing enables the authoritative server to return different IP addresses of a particular domain to the clients. Every time it receives a query for an IP, it returns a list of IP addresses of a domain to the client.

With every request, the authoritative server changes the order of the IP addresses in the list in a round-robin fashion.

As the client receives the list, it sends out a request to the first IP address on the list to fetch the data from the website. The reason for returning a list of IP addresses to the client is to enable it to use other IP addresses in the list in case the first doesn’t return a response within a stipulated time.

When another client sends out a request for an IP address to the authoritative server, it re-orders the list and puts another IP address at the top of the list following the round-robin algorithm.

Also, when the client hits an IP, it may not necessarily hit an application server. Instead, it may hit another load balancer implemented at the data center level that manages the clusters of application servers.

#### Limitations of DNS load balancing

DNS load balancing is largely used by companies to distribute traffic across multiple data centers that the application runs in. However, this approach has several limitations.

For instance, it does not take into account the current load on the servers, the content they hold, their request processing time, their in-service status, and so on.

Also, since these IP addresses are cached by the client’s machine and the DNS Resolver, there is always a possibility of a request being routed to a machine that is out of service.

DNS load balancing, despite its limitations, is preferred by companies because it is an easy and less expensive way of setting up load balancing on their services.

https://en.wikipedia.org/wiki/Round-robin_DNS

### Load Balancing Methods

There are primarily three modes of load balancing:

* DNS Load Balancing
* Hardware-based Load Balancing
* Software-based Load Balancing


Hardware-based and software-based load balancing are common ways of balancing traffic loads on large-scale services. 

#### Hardware load balancers

Hardware load balancers are highly performant physical hardware. They sit in front of the application servers and distribute the load based on the number of currently open connections to a server, compute utilization, and several other parameters.

Since these load balancers are physical hardware, they need maintenance and regular updates, just like any other server hardware would need. They are also expensive to set up compared to software load balancers, and their upkeep may require a certain skill set.

Also, the hardware load balancers have to be overprovisioned upfront to deal with peak traffic, which is not the case with software load balancers.

But when it comes to performance, hardware load balancers stand out.

If the business has network specialists and an IT team in-house, they can manage these load balancers. Otherwise, the developers are expected to wrap their heads around setting up these hardware load balancers with some assistance from the vendors. This is also the primary reason why developers prefer working with software load balancers.

#### Software load balancers

Software load balancers can be installed on commodity hardware and VMs. They are more cost-effective and offer more flexibility to the developers. Software load balancers can be upgraded and provisioned easily compared to hardware load balancers.

You will also find several Load Balancers as a Service (LBaaS) services online that enable you to directly plug in load balancers into your application without you having to do any sort of setup.

Software load balancers are pretty advanced compared to DNS load balancing. They consider many parameters such as data hosted by the servers, cookies, HTTP headers, CPU and memory utilization, load on the network, etc., to route traffic across the servers.

They also continually perform health checks on the servers to keep an updated list of in-service machines.

Development teams prefer to work with software load balancers as hardware load balancers require specialists to manage them.

HAProxy is one example of a software load balancer widely used by the big guns in the industry, including GitHub, Reddit, Instagram, AWS, Tumblr, StackOverflow, to scale their systems.

Besides the round Robin algorithm, which DNS Load balancers use, software load balancers leverage several other algorithms to efficiently route traffic across the machines. Let’s take a look

https://www.haproxy.com/

#### Algorithms/Traffic routing approaches leveraged by load balancers

##### Round robin and weighted round robin

We know that the round robin algorithm sends IP addresses of machines sequentially to the clients. Parameters such as the server load, CPU consumption, and so on are not considered when sending the IP addresses to the clients.

We have another approach known as the weighted round robin, where based on the server’s compute and traffic handling capacity, weights are assigned to them. And then, based on server weights, traffic is routed to them using the round robin algorithm.

With this approach, more traffic is converged to machines that can handle a higher traffic load, thus efficiently using the resources.

This approach is pretty useful when the service is deployed across multiple data centers having different compute capacities. More traffic can be directed to the larger data centers containing more machines.

##### Least connections

When using this algorithm, the traffic is routed to the machine with the least open connections of all the machines in the cluster. There are two approaches to implement this.

In the first, it is assumed that all the requests will consume an equal amount of server resources, and the traffic is routed to the machine with the least open connections based on this assumption.

In this scenario, there is a possibility that the machine with the least open connections might already be processing requests demanding most of its CPU power. Routing more traffic to this machine would not be a good idea.

In the other approach, the CPU utilization and the request processing time of the chosen machine are also considered before routing the traffic to it. Machines with the shortest request processing time, most negligible CPU utilization, and the least open connections are suitable candidates to process future client requests.

The least connections approach comes in handy when the server has long opened connections like persistent connections in a gaming application.

##### Random

Following this approach, the traffic is randomly routed to the servers. The load balancer may also find similar servers in terms of existing load, request processing time, and so on. Then it randomly routes the traffic to these machines.

##### Hash

In this approach, the source IP where the request is coming from and the request URL are hashed to route the traffic to the backend servers.

Hashing the source IP ensures that a client’s request with a certain IP will always be routed to the same server.

This facilitates a better user experience as the server has already processed the initial client requests and holds the client’s data in its local memory. There is no need for it to fetch the client session data from the session memory of the cluster and process the request. This reduces latency.

Hashing the client IP also enables the client to re-establish the connection with the same server that was processing its request in case the connection drops.

Hashing a URL ensures that the request with that URL always hits a certain cache that already has data on it. This is to ensure that there is no cache miss.

This also averts the need for duplicating data in every cache and is, thus, a more efficient way to implement caching.

### What is Monolithic Architecture?

An application has a monolithic architecture if it contains the entire application code in a single codebase.

A monolithic application is a self-contained, tightly coupled software application. This is unlike the microservices architecture, where every distinct feature of an application may have one or more dedicated microservices powering it.

Taking example of a social networking site like Facebook. The application contains various features such as:

* User posts
* Comment system
* Groups
* Marketplace
* Portal Ads
* Photo storage
* Live streaming
* Recommendation system for recommending the latest and contextual content on the platform to the users and so on.

In a monolithic architecture, all the modules will be coded in a single codebase tightly coupled with each other as opposed to having one or more dedicated microservice for running respective features.

The diagram below represents a monolithic architecture.

![image](https://user-images.githubusercontent.com/25869911/155901462-75cf6ffc-5b67-4f57-a7a1-9f1ac353f2b8.png)

Monolithic apps are simple to build, test, and deploy in comparison to a microservices architecture.

Often during the initial stages of a business, teams choose to move forward with a monolithic architecture, intending to branch out into a distributed microservices architecture later.

Well, this decision is a trade-off. We need to bear in mind refactoring and re-writing code has significant costs associated. Dismantling features from a tightly coupled architecture and re-implementing them into separate microservices demands a lot of time and resources.

There have been instances in the past where the dev teams decided to start with a monolithic architecture and later scaled out to a distributed microservices architecture.

This is what LinkedIn did. Though I would like to state here that LinkedIn started at a time when cloud computing and microservices architecture weren’t the norm.

In the present computing landscape, applications are built and deployed on the cloud. Also, businesses have to move fast. A wise decision is to pick the loosely coupled stateless microservices architecture from the start if we have multiple distinct features in our application and expect things to grow at a rapid pace in the future.

On the flip side, if our requirements are simple, monolithic architecture would suit best. Implementing a microservices architecture in this use case would be overkill. After all, managing numerous modules running in conjunction in a distributed environment isn’t a walk in the park

https://engineering.linkedin.com/architecture/brief-history-scaling-linkedin

### When should you pick a Monolithic Architecture?

#### Pros of monolithic architecture

##### Simplicity

Monolithic applications are simple to develop, test, deploy, monitor and manage since everything resides in one repository.

Things are relatively simple when dealing with one repository averting the complexity associated when handling and monitoring multiple components deployed separately.

#### Cons of monolithic architecture

##### Continuous deployment

Continuous deployment is a pain in monolithic applications as even a minor code change in a certain application layer or a feature necessitates a re-deployment of the entire application.

##### Regression testing

The downside of re-deployment of the entire application is that we need to perform a thorough regression testing of the whole application after the deployment is done. A minor code change in one feature can potentially impact the functionality of other features significantly since all the features are tightly coupled with each other.

##### Single points of failure

Monolithic applications have a single point of failure. A bug in any of the application features can bring down the entire application.

##### Scalability issues

Maintenance and scalability are a challenge in monolith apps as all the components are so tightly coupled with each other. As the code size increases, things get trickier to manage.

##### Cannot leverage heterogeneous technologies

heterogenous - diverse in character or content.

Building complex applications with a monolithic architecture is tricky since multiple technologies and programming languages need to be leveraged to implement the respective features of an application.

Using multiple programming languages in a single codebase becomes a mess also often times not possible. Heterogeneous technologies have compatibility issues and microservices architecture suits best to leverage them.

It is tricky to use Java and NodeJS together in a single codebase, and when I say tricky, I am being optimistic. I am not sure if it is even possible.

##### Not cloud-ready, hold state

Generally, monolithic applications are not cloud-ready as they may hold state in the static variables. Though not all monolith apps are designed that way, it’s a general observation that legacy apps use static variables to quite an extent. An application to be cloud-native, to have a consistent behavior on the cloud, has to be stateless.

#### When should you pick a monolithic architecture?

Monolithic applications fit best for use cases where the app requirements are pretty simple; when the application is not that complex. Examples of this are a to-do list app, a sports news app, an organization’s internal tax calculation app, a similar open public tool, etc.

These are the use cases where the business is certain that the application will have limited features and complexity and will not require any serious expansion in the near future.

### What is Microservice Architecture?

In a microservices architecture, different features of an extensive service like Facebook are deployed separately as smaller loosely coupled services called microservices. These microservices work in conjunction to form a large distributed online service as a whole.

![image](https://user-images.githubusercontent.com/25869911/155901902-8be40cb9-9c34-4645-aec8-9d143f910199.png)

Remember the single responsibility and the separation of concerns principles? Both principles come into effect in a microservices architecture.

Every service has a single responsibility of running a specific feature and is separated from other services facilitating a loosely coupled architecture.

This particular architecture facilitates easier, cleaner app maintenance, feature development, testing, and deployment of individual modules in contrast to a monolithic architecture.

Imagine accommodating every feature in a single repository. How complex would things get? It would be a maintenance nightmare.

Also, when the project is large, it is managed by several different teams. When application modules/features are separate, they can be assigned to dedicated teams with minimal fuss, smoothing out the development process.

With microservices, scalability becomes easy too. The architecture is inherently designed to scale. Services that need scaling can be scaled independently without affecting other services.

Also, every microservice ideally has a separate database. This eliminates single points of failure and system bottlenecks.

### When should you pick Microservices Architecture?

#### Pros of microservice architecture

##### No Single Points of failure

Since microservices is a loosely coupled architecture, there is no single point of failure. Even if a few services go down, the application as a whole would still be up.

##### Leverage the heterogeneous technologies

Every microservice interacts with each other via a REST API gateway interface. A system with microservices can leverage the polyglot persistence architecture and other heterogeneous technologies like Java, Python, Ruby, NodeJS, etc.

Polyglot persistence uses multiple database types, like SQL and NoSQL, together in the architecture. 

##### Independent and continuous deployments

The deployments can be independent and continuous. We can have dedicated teams for every microservice, and they can be scaled independently without impacting other services.

#### Cons of microservices architecture

##### Management complexity

Microservices is a distributed environment with several services powered by clusters of servers. This makes system management and monitoring complex.

We need to set up additional components to manage microservices, such as a node manager like Apache Zookeeper, a distributed tracing service for monitoring the nodes, etc.

We need skilled resources and even have to set up a dedicated team just to manage these services.

##### Strong consistency

Sometimes, strong consistency is hard to guarantee in a distributed environment, especially when trying to achieve a single consistent state across several microservices.

Things are eventually consistent across the nodes, and this limitation is due to the distributed design.

In the database chapter, we will discuss both strong and eventual consistency in detail.


#### When should you pick a microservices architecture?

The microservice architecture fits best for complex use cases; for apps that need to expand quick from adding new features standpoint. A social network application is a good example of a complex use case.

A typical social networking application has various components such as messaging, real-time chat, LIVE video streaming, photo uploads, post like and share features, etc.

This use case fits best for a microservices architecture. Also, the microservices architecture enables a business move fast. A business can separately develop, test, deploy an application feature without affecting the current features. There is not much need for regression testing and so on.

Writing every feature in a single codebase would take no time to become a mess.

So, by now, we have seen three ways to proceed with the design of our application:

* Picking a monolithic architecture
* Picking a microservice architecture
* Starting with a monolithic architecture and later scaling out into a microservice architecture.

Picking a monolithic or a microservice architecture largely depends on our use case. I suggest keeping things simple and thoroughly understanding the requirements before deciding on an architecture.

### Monolith and Microservices– Understanding the Trade-Offs – Part 1

 discussion on the trade-offs of choosing between a monolith and microservices architecture to design our application.
 
#### Fault isolation

When we have a microservices architecture, it becomes easy for us to isolate faults and debug them. When a glitch occurs in a certain service, we just have to fix the issue in that particular service without the need to scan the entire codebase to locate and fix the issue. This is known as fault isolation.

#### Development team autonomy

In the case of a monolith architecture, if the number of developers and the teams working on a single codebase grows beyond a certain number, it may impede the productivity and the velocity of the teams.

In this scenario, things become a little tricky to manage. As the size of the codebase increases, the compile-time and tests runtime increase too. This is because, in a monolith architecture, the entire codebase has to be compiled after a code change as opposed to just compiling the module we work on.

A code change made, in the codebase, by any other team has a direct impact on the features we develop. It may even break the functionality of our feature. Due to this, thorough regression testing is required every time anyone pushes new code or an update to production.

Also, as the code is pushed to production, we need all the teams to stop working on the codebase until the change is pushed to production.

The code pushed by a certain team may also require approval from other teams in the organization working on the same codebase. This process is a bottleneck in the system.

On the contrary, in the case of microservices, dedicated teams have complete ownership of their codebases. They have full development and deployment autonomy over their modules with separate deployment pipelines. Code management becomes easier. It becomes easier to scale individual services based on their traffic load patterns.

So, if you need to move fast, quickly launch a lot of features to the market and scale. Moving forward with microservices architecture is a good bet.

Having a microservices architecture sounds delightful, but we cannot ignore the increase in the complexity in the architecture due to this. Adopting microservices has its costs.

With the microservices architecture comes the need to set up distributed logging, monitoring, inter-service communication, service discovery, alerts, tracing, dedicated build and release pipelines, health checks, and so on. You may even have to write a lot of custom tooling from scratch for yourself.

I believe you get the idea. There are always trade-offs involved, and there is no perfect solution. We need to be crystal clear on our use case and see what architecture suits our needs best.

Let’s understand this further with the help of the real-world example of a company called Segment that started with a monolith architecture, moved to microservices and then moved back again to the monolith architecture.

#### Segment – From monolith to microservices and back again to the monolith

Segment is a customer data platform that initially started with a monolith and later split it into microservices. As their business gained traction, they again decided to revert to the monolith architecture.

Why did they do that?

Let’s take a look.

The segment engineering team split their monolith into microservices for fault isolation and easy debugging of issues in the system.

Fault isolation with microservices helped them minimize the damage a fault caused in the system. When a fault occurred, it was confined to a particular service as opposed to impacting, even bringing down the entire system as a whole.

Given the original monolith architecture had low management overhead, there were single points of failure. A glitch in a certain functionality could impact the entire system.

Segment integrates data from many different data providers into their systems. As the business gained traction, they integrated more data providers into their system, creating a separate microservice for every data provider. The increase in the number of microservices led to a significant increase in the complexity of their architecture, subsequently taking a toll on their productivity.

The defects with regards to microservices started increasing significantly. They had three engineers solely dedicated to getting rid of these defects to keep the system online. This operational overhead became resource-intensive and slowed down the organization immensely.

To tackle the issue, they made the decision to move back to the monolith, giving up on fault isolation and other nice things that the microservices architecture brought along.

They ended up with an architecture with a single code repository called Centrifuge that handled billions of messages per day delivered to multiple APIs.

### Monolith and Microservices– Understanding the Trade-Offs – Part 2

#### Segment high-level architecture

Segment’s data infrastructure ingests hundreds of thousands of events per second. These events are then directed to different APIs and webhooks via a message queue. These APIs are also called server-side destinations, and there are over a hundred of these destinations at Segment.

When they started with a monolith architecture, they had an API that ingested events from different sources, and the events were then forwarded to a distributed message queue. The queue moved the event payload further to other destination APIs according to configuration and settings.

![image](https://user-images.githubusercontent.com/25869911/155902672-53643db3-1f9a-41fc-a66c-29002cd12633.png)

In the monolithic architecture, as all the events were moved into a single queue, some of the events often failed to deliver to the destinations and were retried by the queue after stipulated time intervals.

This made the queue contain both the new as well as the failed events waiting to be retried. As a result, the queue would be eventually flooded, resulting in delays in the delivery of events to the destinations.

To tackle the queue flooding issue, the engineering team at Segment split the monolith into microservices and created a separate microservice for every destination.

Now every service contained its own individual distributed message queue. This helped cut down the load on a single queue and enabled the system to scale, increasing the throughput.

![image](https://user-images.githubusercontent.com/25869911/155902741-1e980395-afb0-48c7-ae93-79a803c80247.png)

In this scenario, even if a certain queue got flooded, it didn’t impact the event delivery of other services. This is how Segment leveraged fault isolation with the microservices architecture.

Over time as the business gained traction, additional destinations were added. Every destination had a separate microservice and a queue. The increase in the number of services led to an increase in the complexity of the architecture.

Separate services had separate event throughput and traffic load patterns. A single-scale policy couldn’t be applied to all the queues commonly. Every service and the queue needed to be uniquely scaled based on its traffic load pattern and this process had to be done manually.

Autoscaling was implemented in the infrastructure, but every service had different CPU & memory requirements. This required manual tuning of the infrastructure, meaning more queues needed more resources for maintenance.

To tackle this, Segment eventually reverted to monolith architecture, calling their architecture a Centrifuge that combined all the individual queues for different destinations into a single monolith service.

The info I have provided on Segment architecture in this lesson is very high-level. If you wish to go into more details and take a look at the Centrifuge architecture, go through these resources:

Goodbye Microservices: From 100s Of Problem Children To 1 Superstar

Centrifuge: A Reliable System For Delivering Billions Of Events Per Day

Below is another instance of a popular service that transitioned from microservices to a monolith architecture.

https://segment.com/blog/goodbye-microservices/

https://segment.com/blog/introducing-centrifuge/

#### Istio – The move from microservices to a monolith

Istio is an open-source service mesh that enables us to connect, secure, control, and observe microservices. It allows us to control how microservices share data with each other.

It recently transitioned from a microservices to a monolith architecture. According to the Istio team, having a monolith architecture enabled them to deliver value and achieve the goals they intended to.

https://blog.christianposta.com/microservices/istio-as-an-example-of-when-not-to-do-microservices/

### Introduction to Micro Frontends

#### What are micro frontends?

Micro frontends are distinct loosely coupled components of an application’s user interface developed applying the concept of microservices to the frontend.

Writing micro frontends is more of an architectural design decision and a development approach as opposed to it being a technology.

What does applying the concept of microservices to the front end mean?

Microservices provide complete autonomy to the teams developing them. They are loosely coupled, provide fault isolation, and offer the freedom to pick the desired technology stack to the dedicated teams, to develop a certain service. Micro frontends offer the same upsides to frontend development.

Typically, in application architecture, despite having microservices on the backend, our frontend is a monolith that is developed by a dedicated frontend development team.

![image](https://user-images.githubusercontent.com/25869911/155903050-d2b79364-293a-48a4-85a2-1c4c9e72f2ac.png)


With the micro frontends approach, we split our application into vertical slices, where a single slice goes end to end right from the user interface to the database. And every slice is owned by a dedicated team.

Besides having the backend devs, the micro frontend team of a particular vertical slice also includes the frontend developers who develop the user interface component only for that specific service.

Every team builds their user interface component choosing their desired technology, and later all these components are integrated, forming the complete user interface of the application. This micro frontend approach averts the need for a dedicated centralized user interface team. Every micro frontend team becomes more of a full-stack team.

![image](https://user-images.githubusercontent.com/25869911/155903134-f582d5b2-8784-4c8c-960d-b1e2117f4cb1.png)


#### Micro frontends e-commerce application example

I’ve picked the example of an e-commerce application because the micro frontends approach is pretty popular with e-commerce websites.

Imagine an online game store that delivers video games for desktops and consoles such as Xbox, Nintendo Switch, PlayStation, and the related hardware.

Our online gaming store will have several different UI components. A few of the key components would be:

The search component – This is a search bar at the top center of the website that enables the users to search games based on the keywords they enter.

Once the user runs a search, the component enables the user to filter their search results based on several options, including the price range, type of console, game genre, and so on.

The game category component – This component displays the popular and widely searched games for different categories on the website’s homepage.

Add to cart and checkout component – This user interface component enables users to add games of their liking to their cart and proceed to the checkout filling in their address and other required information to make the final payment.

During the checkout, the website may also recommend related games to the user as upsells. The user can also feed in coupons and gift cards if they have any.

The payment component – The payment UI component offers different payment options to the user and facilitates the order payment once the user enters their card details on the page.

Every UI component has a dedicated microservice running on the backend powering that particular user interface component. All these different components are developed and managed by dedicated full-stack (micro frontend) teams.

The application’s complete user interface is rendered combining all these different UI components, also called micro frontends.

### The Need For Micro Frontends

A micro frontend team may own a more extensive UI component like the checkout page. They may own a minor component that fits in a particular component like the game category component on the home page. Or they might own both.

The smaller components that integrate into other pages/components of the application are known as fragments.

![image](https://user-images.githubusercontent.com/25869911/155903317-d6131642-d2f5-49f2-9fac-e60556a71945.png)

upsides of splitting an application into micro frontends?

#### Easier coordination between the frontend and the backend devs

When we have full-stack teams owning an entire service end to end, this averts the need for a dedicated frontend team. In addition, since the frontend devs now work alongside the backend devs on the same team, this saves a lot of time that was initially spent in the cross-team coordination.

With this new approach, communication is quick and not so formal. This improves the team’s productivity and enables them to deliver a better user experience by having more effective coordination between the backend and the frontend devs.

#### Leveraging the right technology


Since the micro frontends are loosely coupled, we can develop them leveraging different technologies, just like microservices. This opens up our options as opposed to sticking to just one UI technology to build the complete front end of the website.

There are a plethora of existing frontend technologies in the industry that cater to different use cases, in addition to the new waves of JavaScript frameworks that hit us every year.

With the micro frontends approach, we can pick the right technology to build our frontend components. We often have use cases where just plain JavaScript, HTML, and CSS suffice to build a feature, and then there are other cases where we need advanced frameworks like React, Angular, and Vue to implement our features.

With micro frontends, we don’t necessarily have to use React or a similar framework to build a certain component if we don’t need it, despite having other components being implemented using it.

On the flip side, if our website is built on plain JavaScript and we want to use React, we don’t have to re-write the entire website to use React. We can just write specific components that need React and integrate them into the website.

Even if multiple teams use the same technology to build their UI components, they can work on different versions of the technology. They can easily upgrade their libraries without impacting the website’s other UI components.

![image](https://user-images.githubusercontent.com/25869911/155903510-e738cb59-d0c2-477a-bf0d-8520939d9132.png)

Now, moving forward with the micro frontends approach may sound delightful, but it’s only fit for medium to large websites. This approach won’t be that advantageous for simple use cases. Rather, it will make things more complex and prove to be overkill.

Using multiple technologies in a project brings along a lot of architectural and maintenance complexities with it.

With micro frontends, we need to write additional code to combine all the components built with heterogeneous tech. We also have to deal with compatibility and performance issues when using multiple technologies together. So, there are always trade-offs involved. There is no silver bullet.

https://engineering.atspotify.com/2014/03/spotify-engineering-culture-part-1/

### Micro Frontends Integration

Once we have respective micro frontends ready for our online game store, we need to integrate them together to have a functional website. There are two ways we can do this -

* By integrating micro frontends on the client
* By integrating micro frontends on the server

This concept is similar to the client-side and server-side rendering, which we discussed earlier in the course.

In this micro frontend scenario, we need to write additional logic to enable the integration of the UI components.

#### Client-side integration of micro frontends

A very basic naïve way of integrating components on the client is rendering micro frontends with unique links. We just place the links on the website to enable the user to navigate to a certain micro frontend, like so:

![image](https://user-images.githubusercontent.com/25869911/155903650-d42132d6-a1aa-4741-a746-95786edd2b84.png)


Consider this scenario - our order checkout microservice is hosted on AWS having the URL - https://www.aws.amazon.com/onlinegamestore/checkout and our payment service is hosted on Google Cloud with the URL https://www.cloud.google.com/onlinegamestore/payment

When we integrate these micro frontends via basic links and the user navigates from the checkout page to the payment page clicking on the micro frontend link, the address in the user’s browser changes from the AWS URL to the Google Cloud URL. This will be visible to the end-user.

Also, following this basic approach, the micro frontends that need to be integrated within a specific page can be done using Iframes.

![image](https://user-images.githubusercontent.com/25869911/155903699-2fbe4b34-a1ad-4280-920b-9e61b23e525f.png)

Well, you would have realized that this approach is not ideal. This is more like the 90s way of building websites, connecting web pages via direct links and Iframes.

Using IFrames has several downsides: they can’t be bookmarked, they aren’t good from an SEO standpoint, they have stability and performance issues and so on. Besides, IFrames are an obsolete thing in the modern web dev landscape.

A recommended way to integrate components on the client-side is by leveraging a technology called the Web Components and frameworks such as Single SPA.

Single SPA is a JavaScript framework for frontend microservices that enables developers to build their frontend while leveraging different JavaScript frameworks.

If you wish to know more on web components, this Google Chrome devs video is a good resource.

Alright, let’s move on to understand the server-side integration process of micro frontends.

https://single-spa.js.org/

https://www.youtube.com/watch?v=YBwgkr_Sbx0&ab_channel=GoogleChromeDevelopers

### Server side integration

When the UI components are integrated on the server, on the user request, the complete pre-built page of the website is delivered to the client from the server as opposed to sending individual micro frontends to the client and having them clubbed there.

This cuts down the website’s loading time on the client significantly since the browser does not have to do any sort of heavy lifting.

Just like the client-side integration process, we have to write additional logic on the server to integrate the micro frontends that are requested by the user.

There are several technologies and frameworks available that help us to achieve this.

#### Technology and frameworks facilitating server-side integration

Some of the popular frameworks that facilitate server-side integration of micro frontends are Project Mosaic, Open Components and Podium. Server Side Includes SSI is a server-side scripting language used for clubbing the content of multiple web pages on the webserver.

Zalando is a famous fashion e-commerce company in Europe that uses Project Mosaic to manage its micro frontends. Here is a talk on the micro frontends from their engineering team - The Zalando recipe for scalable frontends.

AutoScout24 is one of the leading internet car portals in Europe. Their engineering team leverages SSI technology to build their micro frontends. They gave a talk about their micro frontends approach.

Well, this pretty much sums up our micro frontends chapter. Let’s move on to databases in the next one.

https://www.youtube.com/watch?v=m32EdvitXy4&ab_channel=code.talks%28ehem.DeveloperConference%29

https://www.thoughtworks.com/talks/a-high-performmance-solution-to-microservice-ui-composition

### Introduction and Types of Data




