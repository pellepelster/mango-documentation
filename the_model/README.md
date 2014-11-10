# The Model

## Overview

This chapter describes the model that builds the foundation for all Mango projects. The model is text based (backed by [Xtext](https://www.xtext.org)) and therefore comes with all amenities of the Eclipse IDE (synatax highlighting, auto-complete, outline view, ...). The model provides facilities to create entities, generic CRUD interfaces for these entities as well as services (REST, SOAP).

## Model Root

Each model starts with a model root marked by the keyword **project** followed by the name of the project. The project name is used in a variety of places as name for the generated artefacts.

**model exmaple**
```
project Project1 {
}
```

The above example is the smallest possible valid model. Despite no real model elements are contained in this model, the generator will nevertheless generate a bunch of artefacts.
The artefacts are generated each time the model is changed inside Eclipse, to call the generator from command line, run

```../gradlew :project1-model:build```

inside the build project directory. After the generator run, three directories are created in the model project directory:

```
$ls project1-model
[...]
src-gen-server
src-gen-client-gwt
src-gen-xml
```

Each directory contains a specific type of generated artefacts.

### Server Artifacts (src-gen-server)

Contains all generated Spring beans, application context definitions, JPA entities, entity import/export webservice endpoints, service rest controllers.

**Application Context definitions**

Based on the name of the project model a set of application contexts is generated, each covering a single aspect of Mangos functionality. Each file has a *-gen.xml* postfix to denote that this file is generated.

```
$ls project1-model/src-gen-server
[...]
Project1BaseApplicationContext-gen.xml
Project1DB-gen.xml
Project1GWTRemoteServices-gen.xml
Project1RestRemoteServices-gen.xml
Project1SpringServices-gen.xml
Project1Webservices-gen.xml
```

**BaseApplicationContext-gen.xml**

Definitions for all generated Spring beans that are not derived from the service model

**DB-gen.xml**

Bean definitions for the persistence parted (datasource, persistence unit, entity manager factory, ...)

**GWTRemoteServices-gen.xml**

Exports all services for asynchronous usage with GWT RPC clients.

**RestRemoteServices-gen.xml**

Generic rest controllers to access services with HTTP-REST.

**SpringServices-gen**

Actual implementations for the modelled services.

**Webservices-gen.xml**

Generic import/export webservice endpoints for the modelled entities.

### GWT Client Artifacts (src-gen-client-gwt)

The client artefacts contain value objects corresponding to the server entities, synchronous and asynchronous service interfaces and GWT module definitions.
Also a complete copy of the UI model in the form of Java classes that can be understood by the UI interpreter.

### XML Artifacts (src-gen-xml)

For each entity from the model a XML schema as well as a WSDL definition is generated that uses these schemas to provide import/export webservices for these entities.
