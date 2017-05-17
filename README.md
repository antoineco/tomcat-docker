# Supported tags and respective `Dockerfile` links

* `6.0.53-jre7-centos`, `6.0-jre7-centos`, `6-jre7-centos`, `6.0.53-centos`, `6.0-centos`, `6-centos` [(6/jre7-centos/Dockerfile)](https://github.com/antoineco/tomcat/blob/a2f72759f1102eb8d34711d38e0c3b704549ba6f/6/jre7-centos/Dockerfile)
* `6.0.53-jre8-centos`, `6.0-jre8-centos`, `6-jre8-centos` [(6/jre8-centos/Dockerfile)](https://github.com/antoineco/tomcat/blob/a2f72759f1102eb8d34711d38e0c3b704549ba6f/6/jre8-centos/Dockerfile)
* `7.0.78-jre7-centos`, `7.0-jre7-centos`, `7-jre7-centos`, `7.0.78-centos`, `7.0-centos`, `7-centos` [(7/jre7-centos/Dockerfile)](https://github.com/antoineco/tomcat/blob/3ee5b5e9e663a71631465e152e8346e13201db8c/7/jre7-centos/Dockerfile)
* `7.0.78-jre8-centos`, `7.0-jre8-centos`, `7-jre8-centos` [(7/jre8-centos/Dockerfile)](https://github.com/antoineco/tomcat/blob/3ee5b5e9e663a71631465e152e8346e13201db8c/7/jre8-centos/Dockerfile)
* `8.0.44-jre7-centos`, `8.0-jre7-centos`, `8.0.44-centos`, `8.0-centos` [(8.0/jre7-centos/Dockerfile)](https://github.com/antoineco/tomcat/blob/3ee5b5e9e663a71631465e152e8346e13201db8c/8.0/jre7-centos/Dockerfile)
* `8.0.44-jre8-centos`, `8.0-jre8-centos` [(8.0/jre8-centos/Dockerfile)](https://github.com/antoineco/tomcat/blob/3ee5b5e9e663a71631465e152e8346e13201db8c/8.0/jre8-centos/Dockerfile)
* `8.5.15-jre8-centos`, `8.5-jre8-centos`, `8-jre8-centos`, `jre8-centos`, `8.5.15-centos`, `8.5-centos`, `8-centos`, `centos` [(8.5/jre8-centos/Dockerfile)](https://github.com/antoineco/tomcat/blob/0874787f33c6480ca5a1f846a2cec87862c80be9/8.5/jre8-centos/Dockerfile)
* `9.0.0.M21-jre8-centos`, `9.0.0-jre8-centos`, `9.0-jre8-centos`, `9-jre8-centos`, `9.0.0.M21-centos`, `9.0.0-centos`, `9.0-centos`, `9-centos` [(9.0/jre8-centos/Dockerfile)](https://github.com/antoineco/tomcat/blob/0874787f33c6480ca5a1f846a2cec87862c80be9/9.0/jre8-centos/Dockerfile)

![logo](https://raw.githubusercontent.com/antoineco/tomcat/master/logo.png)

# What is the `tomcat` image?

An extension of the official [`tomcat`][docker-tomcat] image with extra OS variants.

# How to use the `tomcat` image?

This image shares all its features with the official [`tomcat`][docker-tomcat] image.

# Image Variants

The `tomcat` images come in different flavors, each designed for a specific use case.

## Base operating system

### `tomcat:<version>-centos`

This image is based on the [CentOS](https://www.centos.org/) operating system, available in [the `centos` official image][docker-centos].

## Components

A tagging convention determines the version of the components distributed with the `tomcat` image.

### `<version α>`

* Tomcat release: **α**
* OpenJDK JRE release: *recommended version for that particular Tomcat release*

### `<version α>-jre<β>`

* Tomcat release: **α**
* OpenJDK JRE release: **β** (latest patch version)

### `jre<β>`

* Tomcat release: *as distributed with the [`tomcat:latest`][docker-tomcat] image*
* OpenJDK JRE release: **β** (latest patch version)

# Maintenance

## Updating configuration

You can automatically update OpenJDK versions and regenerate the repository tree with:

```
./generate-dockerfiles.sh
```

## Updating library definition

After committing changes to the repository, regenerate the library definition file with:

```
./generate-bashbrew-library.sh >| tomcat
```

## Rebuilding images

All images in this repository can be rebuilt and tagged manually using [Bashbrew][bashbrew], the tool used for cloning, building, tagging, and pushing the Docker official images. To do so, simply call the `bashbrew` utility, pointing it to the included `tomcat` definition file as in the example below:

```
bashbrew --library . build tomcat
```

## Automated build pipeline

Any push to the upstream [`openjdk`][docker-openjdk] repository or to the source repository triggers an automatic rebuild of all the images in this repository. From a high perspective the automated build pipeline looks like the below diagram:

![Automated build pipeline][pipeline]


[banner]: https://raw.githubusercontent.com/antoineco/tomcat/master/logo.png
[docker-tomcat]: https://hub.docker.com/_/tomcat/
[docker-centos]: https://hub.docker.com/_/centos/
[docker-openjdk]: https://hub.docker.com/r/antoineco/openjdk/
[bashbrew]: https://github.com/docker-library/official-images/blob/master/bashbrew/README.md
[pipeline]: https://raw.githubusercontent.com/antoineco/tomcat/master/build_pipeline.png
