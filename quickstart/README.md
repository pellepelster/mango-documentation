# Quickstart

## Initial project setup

Of course you can set up up the projects from scratch using the eclipse new project wizard and write all files by hand. But because its easier and faster, we will begin with the Mango bootstrapper who will create a basic project set to get you started.

The bootstrapper is started with a package name and a project name based on which the projects will be created. To create an example project named Project1 with the root package path org.example.Project1 call the boorstrapper like this:

`curl https://raw.githubusercontent.com/pellepelster/mango/master/bootstrap.sh | bash -s org.example.Project1`

After a while, a bunch of projects and additional files are created in a subfolder named after your project. The files being the Gradle wrapper 1 for building, the build project 2 acting as root project for a Gradle multiple project build, the client project 3 and server project 4 for client respectively server code and finally the model project 5 holding the model for the application expressed in the Mango DSL as well as the generated artefacts.

```
$ ls project1/
1 gradle
1 gradlew
1 gradlew.bat
2 project1-build/
3 project1-client/
4 project1-server-web/
5 project1-model/
```
To see if everything works, change into the build project directory, build the project and start it in a Jetty container by calling:

```
$ cd project1/project1-build/
$ ./gradlew jettyEclipseRun
```

After a while you are greeted with

> :project1-server-web:jettyEclipseRun > Running at http://localhost:9090/
