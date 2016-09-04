Getting Started
===============

A full guide to installing growler can be found in the installation guide,
but for most use-cases, a standard :code:`pip install growler` will be
all that is needed.

To get started creating a growler service, import the ``App`` class and create
an instance (typical name is ``app``).
To this object you add functions (using ``app.use`` method) which will be
called, one after another, with a request and response object created from a
connecting client.
These objects are mutable, and any changes in them will be visible to any other
functions 'downstream'.

In addition to ``app.use`` method, which is intended to be used for functions
that should be run for every request, there are 'http-verb' methods (eg. get,
put, post) that only execute the function if the request method matches.
Additionally, these methods require a path string argument, which the request
must match.

App objects contain two methods, ``create_server`` & ``create_servers_and_run_forever``
which create an ``asyncio`` server and effectively runs the web application.
Growler does not force you to use the ``asyncio`` library, but includes these
helper functions to reduce the boilerplate required for getting started.

Here is an example of a trivial growler application:

.. code:: python

  from growler import App

  app = App()

  @app.use
  def log_file(req, res):
      print("<{ip}> {req_path}".format(ip=req.ip, req_path=req.path))

  @app.get("/")
  def index_file(req, res):
      res.send_text("index.")

  app.create_server_and_run_forever(host='0.0.0.0', port='8080')

The application is created, and two functions are added:
  * ``log_file`` which prints the client's ip address and the request path on
    every request
  * ``index_file`` simply sends the text 'index.' back to the client if the
    request method was GET and and the path matched exactly '/'

The default behavior of all other is to return a simple 404 error.

The use of methods as decorators (like ``@app.use``) may be a foreign concept
for some programmers, but just know that the code would be equivalent to:

.. code:: python

  from growler import App

  app = App()

  def log_file(req, res):
      print("<{ip}> {req_path}".format(ip=req.ip, req_path=req.path))

  def index(req, res):
      res.send_text("index.")

  app.use(log_file) # use in a non-decorated fashion
  app.get("/", index)

  app.create_server_and_run_forever(host='0.0.0.0', port='8080')

The use of decorators is recommended as it reduces code redundancy, but traditional
method calling is supported.
