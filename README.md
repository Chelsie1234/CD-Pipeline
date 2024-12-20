# CD-Pipeline
CD with unit, integration, and end-to-end testing with github actions

### Instructions
The goal of this exercise is to be able to build a CD pipeline that automate the testing and building of a multi project application, built with docker compose, and automate the merging into different branches while running the appropriate steps that ensure code quality with each merge.

The Application Code

The attached file contains an application for a reverse to do list. The application contains a front end and a back end.

The app connects to a MongoDB database and you can use an online mongo DB instance by changing the connection string in "backend/app.js".

 install it locally either with npm or build and run the Dockerfile in each separate folder (frontend and backend), or use docker compose:

from the root directory of the project, where the docker-compose.yml file exists, run:

docker-compose up --build -d

Then you should be able to access the app on localhost:3000

when you want to shut down the app, use 

docker-compose down

when you want to launch a docker compose instance that you had already launched, no need to use the --build command:

docker-compose up

refer to the docker compose quick start documentation for further info:

https://docs.docker.com/compose/gettingstarted/


The Github Workflow Requirements

The expected merge process is as follows:

feature branch -> dev -> main

feature branch: create a branch, name it my-feature, make a small change to the code (add a comment for example) to justify a merge from the feature branch to dev.

Task: Build a GitHub Workflow for CI/CD Automation

Objective:
Create a GitHub Actions workflow to automate the CD process for the following scenarios:

On merging a feature branch into the dev branch:
Build the project.
Run unit tests.
If successful, automatically trigger a merge of the dev branch into the main branch.
On merging the dev branch into the main branch:
Build the project.
Run all unit tests.
run E-2-E tests
If successful, build and push Docker images (managed by docker-compose.yml) to a public Docker repository.


Steps to Accomplish the Task

1. Define Workflow Triggers

Trigger 1: On push event to the dev branch (merging feature branches).
Trigger 2: On push event to the main branch (after dev merges into main).
2. Workflow Tasks

Build and Test on dev Merge:
Checkout the code.
Install dependencies for frontend and backend.
Run unit tests for both services.
If successful, initiate a merge from dev to main.
Build, Test, and Deploy on main Merge:
Checkout the code.
Install dependencies for frontend and backend.
Run unit tests for both services.
Build Docker images using the docker-compose.yml file.
Push the images to a public Docker repository.


below is a reference to help you merge a github branch inside a workflow:



https://github.com/marketplace/actions/merge-branch


What to submit:

Your github workflow yml files
your public dockerhub repo link
a screenshot of the successful pipelines executed in the github action tab