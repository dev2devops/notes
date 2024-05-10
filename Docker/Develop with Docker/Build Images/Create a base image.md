#Docker 
# Create a base image
Most Dockerfiles start from a parent image. If you need to completely control the contents of your image, you might need to create a base image instead. Here’s the difference:

-   A [parent image](https://docs.docker.com/glossary/#parent-image) is the image that your image is based on. It refers to the contents of the `FROM` directive in the Dockerfile. Each subsequent declaration in the Dockerfile modifies this parent image. Most Dockerfiles start from a parent image, rather than a base image. However, the terms are sometimes used interchangeably.
    
-   A [base image](https://docs.docker.com/glossary/#base-image) has `FROM scratch` in its Dockerfile.
    

This topic shows you several ways to create a base image. The specific process will depend heavily on the Linux distribution you want to package. We have some examples below, and you are encouraged to submit pull requests to contribute new ones.

## Create a full image using tar[](https://docs.docker.com/develop/develop-images/baseimages/#create-a-full-image-using-tar)

In general, start with a working machine that is running the distribution you’d like to package as a parent image, though that is not required for some tools like Debian’s [Debootstrap](https://wiki.debian.org/Debootstrap), which you can also use to build Ubuntu images.

It can be as simple as this to create an Ubuntu parent image:

```
$ sudo debootstrap focal focal > /dev/null
$ sudo tar -C focal -c . | docker import - focal

sha256:81ec9a55a92a5618161f68ae691d092bf14d700129093158297b3d01593f4ee3

$ docker run focal cat /etc/lsb-release

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=20.04
DISTRIB_CODENAME=focal
DISTRIB_DESCRIPTION="Ubuntu 20.04 LTS"
```

There are more example scripts for creating parent images in [the Docker GitHub repository](https://github.com/docker/docker/blob/master/contrib).

## Create a simple parent image using scratch[](https://docs.docker.com/develop/develop-images/baseimages/#create-a-simple-parent-image-using-scratch)

You can use Docker’s reserved, minimal image, `scratch`, as a starting point for building containers. Using the `scratch` “image” signals to the build process that you want the next command in the `Dockerfile` to be the first filesystem layer in your image.

While `scratch` appears in Docker’s repository on the hub, you can’t pull it, run it, or tag any image with the name `scratch`. Instead, you can refer to it in your `Dockerfile`. For example, to create a minimal container using `scratch`:

```
# syntax=docker/dockerfile:1
FROM scratch
ADD hello /
CMD ["/hello"]
```

Assuming you built the “hello” executable example by using the source code at [https://github.com/docker-library/hello-world](https://github.com/docker-library/hello-world), and you compiled it with the `-static` flag, you can build this Docker image using this `docker build` command:

```
$ docker build --tag hello .
```

Don’t forget the `.` character at the end, which sets the build context to the current directory.

> **Note**: Because Docker Desktop for Mac and Docker Desktop for Windows use a Linux VM, you need a Linux binary, rather than a Mac or Windows binary. You can use a Docker container to build it:
> 
> ```
> $ docker run --rm -it -v $PWD:/build ubuntu:20.04
> 
> container# apt-get update && apt-get install build-essential
> container# cd /build
> container# gcc -o hello -static hello.c
> ```

To run your new image, use the `docker run` command:

```
$ docker run --rm hello
```

This example creates the hello-world image used in the tutorials. If you want to test it out, you can clone [the image repo](https://github.com/docker-library/hello-world).