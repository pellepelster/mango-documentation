# UI Model

The overall goal for the UI DSL is to provide a simple generic way to **C**reate **R**ead **U**pdate and **D**elete data entities (which also are modeled in the same DSL, see [Entity Model]).
Each generic UI is divided in two parts, first the search which is made up of a filter where filter criteria can be entered and the result table listing the actual search results for all entities matching the filter criteria. 

The found entity data then can be opened in an editor that provides facilities to edit and save the data or to create new entities.
From the UI model DSL a set of classes is generated for each dictionary containing the model information in a in a way the dictionary interpreter can work with it. The interpreter then builds an abstract run time model for all dictionary elements (searches, filters, editors, controls, tables, composites, ...).

The actual GWT based UI implementation then connects to this abstract runtime model using a callback mechanisms.
The abstraction of the dictionary run time comes with the benefit of the capability to add another UI implementation, in this case a simple Junit layer that can be used to test the dictionary.
The generated Java model classed also provide extensions points where you can hook in you own code, to alter the default behavior of the dictionary interpreter where needed.

![ui_model1.png](ui_model1.png "UI Model Overview")
