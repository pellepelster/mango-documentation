# The Model

## Overview

This chapter describes the model that builds the foundation for all Mango projects.
The model is text based (based on [Xtext](https://www.xtext.org)) and therefore comes with all amneties of the Eclipse IDE (synatax highlighting, autocomplete, outline view, ...)
The model provides facilites to express entities, generic CRUD interfaces for these enties as well as services.

## Model Root

Each model starts with amodel root markes by the keyword project followed by the name of the project.

**model root exmaple**
```
project Project1 {
}
```

## Generated artifacts


```
src-gen-client-gwt
src-gen-server
src-gen-xml
```