# Containerization-of-a-React-front-end-and-Flask-back-end-application
Using docker containers to containerize a web application and taking advantage of its deployment, scalability and reusability properties.

These are steps laid out in the FREE AWS Cloud Project Bootcamp which I am a part of as a student in the second Week. *App Containerization by Andrew Brown*

#### DISCLAIMER
So let's agree that you are using Gitpod or VsCode as your development environment and that you already have a Flask back-end app and a React front-end app ready to be containerized, or you can follow along by using the files and scripts in this repo.

#### Let's go

* Step 1: Create a Dockerfile inside the backend-Flask directory

    Inside the Dockerfile, you have specified the base image and add any necessary dependencies and packages required by your Flask. But if you want to run these, move into the working DIR of Backend-Flask, and run the following commands;.
    
RUN ``pip3 install -r requirements.txt`` to install all your dependencies 

*to RUN Flask*..

CMD  ``pythom3 -m flask run --host==0.0.0.0 --port=4567`` let us breifly discuss certain parts of the command...

  -`python3`(we are running python version 3)
  -`-m`(a module specifing to use the FLASK module)
  -`--host=0.0.0.0`(we are binding to 0.0.0.0, because we are trying to expose our application outside the scope of the environment that we are running, rather than default which is 27.0.0.1 the localhost)
  -`--port=4567`(we are telling it to start on port 4567)

* Step 2: Build the Docker image for the Flask app

Move back to your root directory, and RUN;

    ``docker build -t  backend-flask ./backend-flask``
    
