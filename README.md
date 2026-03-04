Deploying python application developed using framework called FLASK.

## Gunicorn is not a Python framework.
>>Django/Flask/FastAPI: These are Web Frameworks. They handle routing (URL to code), business logic, and database interactions. They are the "brains" of your app.

>>Gunicorn (Green Unicorn): This is a WSGI HTTP Server. It is the "engine" that sits between the outside world (the internet) and your Python code.

>>Why do you need Gunicorn?
Python frameworks usually come with a built-in "development server." However, those servers are single-threaded and fragile. If two users click a button at the same time, the second user has to wait for the first one to finish.

Gunicorn solves this by using a "Pre-fork Worker Model":

Master Process: It starts up and manages the application.

Worker Processes: It forks several "worker" processes (children).

Concurrency: If you have 4 workers, your app can handle 4 simultaneous requests. If one worker crashes, the Master process simply spawns a new one.

SUMMARY:
"Gunicorn isn't a framework; it’s a WSGI HTTP Server designed for UNIX. Its job is to provide a robust, concurrent environment for Python web frameworks like Django or Flask to run in production. It uses a pre-fork worker model to handle multiple simultaneous requests, which the built-in development servers of those frameworks cannot safely do."