# Quickstart

## Initial project setup

Of course you can set up up the projects from scratch using the Eclipse new project wizard and write all files by hand. But because its easier and faster, we will begin with the Mango bootstrapper who will create a basic project setup to get you started.

The bootstrapper is started with a package name and a project name based on which the projects will be created. To create an example project named Project1 with the root package path org.example.Project1 call the bootstrapper like this:

`curl https://raw.githubusercontent.com/pellepelster/mango/master/bootstrap.sh | bash -s org.example.Project1`

This will trigger the bootstrapper download and afterwards starts the project template creation and build.

**Example build output**
```
downloading gradle wrapper to '/tmp/tmp.D3QTdHbnns'
writing temporary gradle bootstrap file to '/tmp/tmp.D3QTdHbnns/tmp.mu8PPkhs1J.gradle'
executing temporary gradle bootstrap file '/tmp/tmp.D3QTdHbnns/tmp.mu8PPkhs1J.gradle'
extracting /home/pelle/.gradle/mango_development/io/pelle/mango/mango-bootstrap/0.0.7-20141107085009/mango-bootstrap-0.0.7-20141107085009.jar to /tmp/tmp.D3QTdHbnns ###/bootstrap.gradle### :extractBootstrapGradle BUILD SUCCESSFUL Total time: 4.254 secs
temporary bootstrap returned bootstrap gradle file at '/tmp/tmp.D3QTdHbnns//bootstrap.gradle'
starting bootstrap with: package name 'org.example', project name 'Project1', output dir '/tmp'
copying templates to /home/pelle/tmp/project1
:createWrapper
:extractProjectTemplate
:copyProjectTemplate

[...]

:project1-build:project1-server-web:eclipseJdt
:project1-build:project1-server-web:eclipseProject
:project1-build:project1-server-web:eclipse

BUILD SUCCESSFUL
```

After a while, a set of projects and additional files are created in a subfolder named after your project. The files being the Gradle wrapper **(1)** for building, the build project **(2)** acting as root project for a Gradle multiple project build, the client project **(3)** and server project **(4)** for client respectively server code and finally the model project **(5)** holding the Mango DSL model for the application as well as the generated artefacts.

```
$ ls project1/
(1) gradle
    gradlew
    gradlew.bat
(2) project1-build/
(3) project1-client/
(4) project1-server-web/
(5) project1-model/
```
To check if everything works, change into the build project directory, build the project and start it in a Jetty container by calling:

```
$ cd project1/project1-build/
$ ./gradlew jettyEclipseRun
```

After a while you are greeted with

```
:project1-server-web:jettyEclipseRun > Running at http://localhost:9090/
```

Open the url with the browser of yout choice and you will see the running example application.
