# Properties

A reocurring task in many applications is the bereitstellung of configurations parameters that enable who ever is in charge of running your application to configure it according to its enviroment or influcence the behaviour using pre defined parameters.
Mango offers an abstraction for this 

There are three sources of property values the database, Java system properties (-D parameter) of Spring properties. The Mango property builder lets you define properties for one of this three sources and darüberhinaus supports the definiion of fallback and default values.

** simple string property stored inside the database **
```
IProperty<String> DB_PROPERTY = PropertyBuilder.createStringProperty("dbproperty").database();

IPropertyService propertyService = [...];

// set the value
propertyService.setProperty(DB_PROPERTY, "my property");

// retrieve the previously set value
String dbproperty = propertyService.getProperty(DB_PROPERTY);

```