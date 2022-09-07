# CLASS 12

## part 1

1. Describe in your own words what each group of status codes represents:

    100's = The request has been received, and the server will attempt to complete it

    200's indicate that the request has been successfully completed

    300's = Informs the client that the requested resource is no longer available at the expected location

    400s denote invalid requests

    500s indicate a server-side error

2. What is a status code 202?

    This code informs the client that the request was valid, but that it will be processed later

3. What is a status code 308?

    This instructs the client to use a different URL to access the resource rather than the current one

4. What code would you use if an update didn't return data to a client?

    204 or 404

5. What code would you use if a resource used to exist but no longer does?

    409

6. What is the 'Forbidden' status code?

    4.3

## part 2

1. Why do we need to pull our MongoDB database string out of our server and put it into our .env?

    so that we can easily change it later, and to hide it

2. What is middleware?

     Software that is between the operating system and the programs that run on it. Middleware allows for communication and data management for distributed applications, essentially acting as a hidden translation layer

3. What does app.use(express.json()) do?

     It parses incoming JSON requests and stores the results in the request variable

4. What does the /:id mean in a route?

5. What is the difference between PUT and PATCH?

    PUT is a resource modification method in which the client sends data that updates the entire resource.

    PATCH is a resource modification method in which the client sends incomplete data to be modified without adjusting the entire data

6. How do you make a default value in a schema?

     almost like creating an object

7. What does a 500 error status code mean?

     the server didnt complete the request properly for some reason

8. What is the difference between a status 200 and a status 201?

     200 means that the request was received, understood, and is being processed.

     201 status code indicates that a request was successful and that a resource was created as a result.

---------------------------
