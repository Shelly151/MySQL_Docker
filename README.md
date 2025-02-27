Docker Basics: Running a Simple Python App

This project introduces the basics of Docker by running a simple Python script inside a container. We will start by printing "Hello, World!" using Docker.

Prerequisites

Before starting, ensure you have the following installed on your system:

Docker Desktop (Download Here)

Python (Download Here)

Step 1: Setting Up the Project

Create a new project directory and navigate into it:

mkdir docker-hello-world  
cd docker-hello-world  

Create a Python script named app.py:

# app.py
print("Hello, World!")

Step 2: Verify Docker and Python Installation

To check if Docker and Python are installed, run the following commands:

Check Docker Version:

docker --version

Check Python Version:

python --version

If both commands return their respective versions, you are ready to proceed.

Step 3: Creating a Dockerfile

Inside the project directory, create a file named Dockerfile (without any extension) and add the following content:

# Use the official Python image
FROM python:3.9  

# Set the working directory inside the container
WORKDIR /app  

# Copy the Python script to the container
COPY app.py .  

# Command to run the script
CMD ["python", "app.py"]

Step 4: Building the Docker Image

Run the following command to build the Docker image:

docker build -t hello-world-app .

After the build is complete, you can verify the created image by running:

docker images

Step 5: Running the Docker Container

Now, run the Docker container using the following command:

docker run hello-world-app

If everything is set up correctly, the output should be:

Hello, World!

Running MySQL Using Docker

This section will guide you through setting up and running a MySQL database inside a Docker container.

Step 1: Creating a MySQL Database Script

Create a SQL file named database_students.sql with the following content:

CREATE DATABASE student;
USE student;

CREATE TABLE students (
  StudentID INT NOT NULL AUTO_INCREMENT,
  FirstName VARCHAR(100) NOT NULL,
  Surname VARCHAR(100) NOT NULL,
  PRIMARY KEY (StudentID)
);

INSERT INTO students (FirstName, Surname)
VALUES ("John", "Andersen"), ("Emma", "Smith");

Step 2: Creating the Dockerfile

Inside the project directory, create a Dockerfile for MySQL:

FROM mysql:latest

ENV MYSQL_ROOT_PASSWORD=root

COPY ./database_students.sql /docker-entrypoint-initdb.d/

Step 3: Deploying MySQL Using Docker

Check Running Containers

docker container ls

Build the MySQL Docker Image

docker build -t mysql_db .

Verify Image Creation

docker images

Run the MySQL Container

docker run --name mysql_container -d mysql_db

Access the Running MySQL Container

docker exec -it mysql_container /bin/bash

Interact with the MySQL Database

mysql -u root -p

Enter the root password (default: root), then run:

USE student;
SELECT * FROM students;

Conclusion

Congratulations! 🎉 You have successfully created and run a MySQL database using Docker. This guide covered both running a simple Python app and setting up a MySQL database inside a Docker container. 🚀

For further learning, you can:

Modify the SQL script to add more data.

Use Docker Compose to manage multiple containers.

Connect the MySQL database to a backend application.

Happy coding! 🚀

