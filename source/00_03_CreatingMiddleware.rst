Creating Your Own Middleware
============================

Middleware is the meat of your web application - adding functionality
dynamically between the client's request and the end result.
Middleware functions are chosen based on the method and path of the request,
and are called in the order they are given to your Growler application object.
Any modifications you make to these objects is stored and passed to all future
This effectively creates a tree where the leaves are functions which finally
send a response to the client.
The application tracks whether a response has been sent - and if so, it will
stop processing the.

Growler makes it easy to create your own middleware; the only API is a function
that accepts two variables: the request and response objects.
The function should not return anything.
