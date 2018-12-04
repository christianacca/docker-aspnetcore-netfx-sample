# Docker with ASP.NET Core MVC targeting full .net framework

This sample demonstrates using **ASP.NET Core MVC targeting full .net framework** and deploying this to Docker

This sample requires [Docker 18.09](https://docs.docker.com/release-notes/docker-ce) or later of the [Docker client](https://store.docker.com/editions/community/docker-ce-desktop-windows).

## Try a pre-built ASP.NET Docker Image

You can quickly run a container with a pre-built [sample ASP.NET Core Docker image](https://hub.docker.com/r/christianacca/aspnetcoreapp-netfx-sample/).
 
1. Start the container:
    * `docker run --rm --name api -p 8080:80 -it -e christianacca/aspnetcoreapp-netfx-sample`
2. Browse to the api endpoint at: http://localhost:8080/api/values

To cleanup:

* `[CTRL]+C`


## Build and run the sample with Docker

You can build and run the sample in Docker using the following commands. The instructions assume that you are in the root of the repository.

1. Clone the sample repository with [git](https://git-scm.com/downloads):
    * git clone https://github.com/christianacca/docker-aspnetcore-netfx-sample.git
2. Open a powershel prompt and change directory to the folder containing `docker-compose.yml` file
3. Build and start the container:
    * `docker-compose up -d --build`
4. Browse to the api endpoint at: http://localhost:8080/api/values

To cleanup:

* `docker-compose down`
