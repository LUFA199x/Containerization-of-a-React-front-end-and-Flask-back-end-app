# Containerization-of-a-React-front-end-and-Flask-back-end-application
Using docker containers to containerize a web application and taking advantage of its deployment, scalability and reusability properties.

These are steps laid out in the FREE AWS Cloud Project Bootcamp which I am a part of as a student in the second Week. *App Containerization by Andrew Brown*

#### DISCLAIMER
So let's agree that you are using Gitpod or VsCode as your development environment and that you already have a Flask back-end app and a React front-end app ready to be containerized, or you can follow along by using the files and scripts in this repo.

#### Let's go

* Step 1: Create a Dockerfile inside the Backend-Flask directory

    Inside the Dockerfile, you have specified the base image and added any necessary dependencies and packages required by your Flask. But if you want to run these, move into the working DIR of Backend-Flask, and run the following commands;.
    
RUN ``pip3 install -r requirements.txt`` to install all your dependencies 

*to RUN Flask*..

CMD  ``pythom3 -m flask run --host==0.0.0.0 --port=4567`` let us breifly discuss certain parts of the command...


  -`python3`(we are running python version 3)
  
  -`-m`(a module specifing to use the FLASK module)
  
  -`--host=0.0.0.0`(we are binding to 0.0.0.0, because we are trying to expose our application outside the scope of the environment that we are running, rather than default which is 27.0.0.1 the localhost)
  
  -`--port=4567`(we are telling it to start on port 4567)
  
  
 **Remember to open port 4567 from the port tab by the terminal tab, clicking the LOCK to open**
  
  you can append ``api/activities/home`` to the url of 404 page you get after you open port 4567 for backend, to get data;
  
  ![Screenshot (688)](https://user-images.githubusercontent.com/66221234/221381105-6708e064-b879-4c10-a599-b6902c3d9083.png)

  
  ![Screenshot (694)](https://user-images.githubusercontent.com/66221234/221379622-ac9e8500-1060-4cdc-a01d-f06f57e8fc4c.png)


* Step 2: Build the Docker image for the Flask app

Move back to your root directory, and RUN;

    ``docker build -t  backend-flask ./backend-flask``
![Docker Build Output]( ![Screenshot (689)](https://user-images.githubusercontent.com/66221234/221378968-eb34a183-c822-4beb-829d-5e05c40aaf56.png)
 )
 
 * Step 3: Create a Dockerfile for the React app
 
 In the root directory of your frontend-React app, create a new file “Dockerfile” Inside the Dockerfile, you have specified the base image and added any necessary dependencies and packages required by your  React app. But if you want to run these, move into the working DIR of frontend-React, and run the following commands
 
 RUN ``npm install``
 
 *to start React*
 CMD ``npm start``
 
 * Step 4: Build the Docker image for the React app
 
 Move back to your root directory, and RUN;
 
 ``docker build -t frontend-react-js ./frontend-react-js``
 
 you can append ``api/activities/home`` to the url of 404 page you get after you open port 3000 for frontend, to get a frontend interface.
 
 ![Screenshot (694)](https://user-images.githubusercontent.com/66221234/221380166-00e78911-c836-4944-8266-ed6bfb175eab.png)

After appending, output should be like this but without data of activities from the backend-flask app;


 ![Screenshot (693)](https://user-images.githubusercontent.com/66221234/221380420-b2b94ca1-facf-47b8-ba39-466b6022e38a.png)

* Step 5: Create a Docker Compose file

Create a Docker Compose file in the root directory of your project. Name the file as “docker-compose.yml”. In the file, specify the services for the React and Flask apps, including the Docker images, ports, and volumes.
You can see my *_docker-compose.yml_* file for the contents of the file. The purpose for tthis file is to build both the Backend-Flask and Frontend-React which was earier built.

* Step 5: Run a ``docker compose`` command

Outputs are as follows with both 4567 and 3000 opened; 

![Screenshot (692)](https://user-images.githubusercontent.com/66221234/221380855-a75e7c2d-e872-404a-a73a-b4c22be6e0b4.png)
![Screenshot (693)](https://user-images.githubusercontent.com/66221234/221380881-2aa94a8a-72d8-44db-8636-2a6bef59a685.png)

To check present active container images, run ``docker image`` command after every stage, I have here an output of the command after building the Backend-Flask.


![Screenshot (690)](https://user-images.githubusercontent.com/66221234/221381198-596fdda4-6013-4464-9d08-2d2f56e772a9.png)

There, we have our docker container image !

**Please, I would appreciate you feedback**


