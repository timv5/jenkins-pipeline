# jenkins-pipeline
Example Jenkins file template connected to git, docker and nexus. 

# Description
This is project consists of jenkins file in which a pipeline project is defined. It is just an example jenkins
file which can be used as a template.

Environment: here are defined your app module names like (names are self-explanatory):
- yourFirstMicroservice
- yourSecondMicroservice
- yourWebApp
- yourRepositoryCredentials
- yourRepositoryServer
- dockerImage
- yourGitUrlFirstMicroservice
- yourGitUrlSecondMicroservice
- yourGitUrlWebApp

Then for stages are defined:
- Workspace preparation: This is an optional step and is defined for transparency purposes only. In our case we create 3 different directories in which we will checkout the code.
- Git code checkout: Checkout your code from git
  - by default master branch is selected
  - yourGitUrlFirstMicroservice (url to your git repository)
  - credentialsId (your git credentials set on jenkins)
  - relativeTargetDir (directory created in a previous step - Workspace preparation)
- Building docker image 
  - each of your project must contain a dockerfile, because the command in this step will execute it and build an image
- Uploading images to Nexus 
  - this step will take your image build in previous step and push it into a repository (in our case Nexus)
  - this will be done for all three modules

# Pre-requisite
- running jenkins
- running nexus
- working web application
  - frontend application
  - backend application (this project assumes that backend application consists from two microservices - jenkins file can be configured to one with deleting one of them)

# Technologies
- git
- docker
- nexus
- jenkins
