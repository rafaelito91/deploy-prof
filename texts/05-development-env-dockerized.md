# Run project inside docker

To run your project inside a container, a Dockerfile will be needed. The content of the docker file depends on the framework or the project. So lets focus only on the necessary here. Assume you already have a project in folder "myproject" that has a valid Dockerfile.

> docker build -t frespo .

The command above will build your project and create a image of it called frespo.