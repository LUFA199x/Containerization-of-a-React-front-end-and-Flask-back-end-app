FROM python:3.10-slim-buster

# Inside the container
# make a new directory inside the container
WORKDIR /backend-flask

# Outside the Container --> Inside the Container
# Copy the following to inside the container; because this contains the libraries we want to install
COPY requirements.txt requirements.txt

# Inside the Container
# Install the python images to use for the app inside the container
RUN pip3 install -r requirements.txt


# Outside container --> Inside Container
# . means everything in the current directory
# The first . represents: backend-flask outside the container
# The second . represents: backend-flask inside the container
COPY . .

# set Env-VAR to remain set when the app is running
# inside the container
ENV FLASK_ENV=development

EXPOSE ${PORT}

# CMD (Command)
# python3 -m flask run --host=0.0.0.0 --port=4567
# -m is for the module: Flask
# to start on ports 4567 
# expose the app outside the scope of what we are running, so we bind it to 0.0.0.0, on default we do port 25 the localhost  
CMD [ "python3", "-m" , "flask", "run", "--host=0.0.0.0", "--port=4567"]