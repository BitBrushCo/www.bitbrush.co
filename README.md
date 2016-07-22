# www.bitbrush.co

## What do we like to do?

We want to build an Apache httpd server using CentOS 7. After a successful build we would like to develop our web pages using Windows environment using Notepad++ or IntelliJ or some other Windows editor. The source html and other artifacts should be exposed seamlessly to running docker container for easy workflow of write, deploy, and test. To achieve this we would expose our Windows source code folder to Docker container. The following steps will demonstarte this scenario.

## Build CentOS Apache Image.

The following steps were taken from CentOS's Docker GitHub [documents](https://github.com/CentOS/CentOS-Dockerfiles/tree/master/httpd/centos7)

### Create Dockerfile 
Download the Dockerfile from CentOS's github repository and place it into your project folder.

### Create docker-compose.yml


Add an external project sources.

- Export an environment varialbe which contains the path name to project source directory
```$ export PROJECT_SOURCE_PATH=Users/projects/my/bitbrushco/DCLWebsite```

- Create a docker-compose.yml file.
- Add environment variable for "PROJECT_SOURCE_PATH" exactly as shown. Notice the extra "/" pre-pending the "$" character. I've tried adding "/" character when I exported "PROJECT_SOURCE_PATH" as "/Users/projects/my/bitbrushco/DCLWebsite" but ran into problem. If I added "/" in exported varialbe docker-compose evaluates it and append my given path with MingW's windows path like "/C:/Program Files/Git/Users/projects/my/bitbrushco/DCLWebsite:/var/www/html". Watch the extra "/C:/Program Files/Git" that was pre-pended to my environment variable. The work around was to define the export variable without the leading "/" and add the leading "/" at docker-compose.yml file.

