# Docker Journey
![Preview](https://brandslogos.com/wp-content/uploads/images/large/docker-logo.png)
# Learning Objectives
- [x] Define Docker and explain common use cases.
Understand how containers functionally and operationally differ from virtual machines.
- [x] Explore three key technologies that make Docker different: layered containers, the Dockerfile, and the Docker API.
- [x] Learn how to create and manage containers using the Docker CLI.
- [x] Understand how to create custom container images using Dockerfiles.
- [x] Learn how to push Docker images to the Docker registry and manage them.
- [x] Troubleshoot common container issues using Docker CLI commands.
- [x] Understand common best practices and problems when working with Docker containers and images.

# Docker best practices
:point_right: Use verify images

:point_right: Use `Container Image Scanner` to scan images if not using official images. 
              *** Example *** : Free open source scanner
                                * Clair
                                * Trivy
                                * Dagda

:point_right: Avoid using `latest` tag because of 3 issue:
    * You don't know what version of the app you are downloading
    * The app's version may change without you knowing when you run `docker pull`
    * `lastest` can be overriden by Docker Hub, making rollbacks difficult

:point_right: Use ** Non-root user ** in container to ensure security of container

:point_right: If you have a web app that needs a database, web server, and cache
                :x: don't roll them into one giant Docker images
                :white_check_mark: Create a bunch of containers and link them together through virtual networks and separate data volumes
            => Use `docker-compose` to manage multiple containers
            :closed_book: With `Compose` you can use a single file called `Compose Manifest` to define all the containers you need for your app and how they should be linked together and then start them all with `docker-compose up`
