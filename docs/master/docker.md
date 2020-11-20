# Getting started with docker

## Introduction
This is about the Docker container build with Zest framework development environment

## Installation
Clone the Zest Docker repo provided by [peter279k](https://github.com/peter279k) 

```sh
git clone https://github.com/zestframework/zest-docker.git
```

Before building this Docker image, you should have the `docker` command firstly

Then executing following command:

```sh
docker build -t zest-docker .
```

After building Docker image successfully, we should use this command to check Docker image is available:

```sh
docker images zest-docker
```

To run this environment as a Docker container, we can use this command:

```sh
docker run -d -p 8000:80 zest-docker
```

Then visit the `http://localhost:8000` via we browser.

It will see the following captured picture and the container build is done

![Zest_Framework default page](https://i.imgur.com/Bn0YXIZ.png)
