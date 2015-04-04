# Properties

Mango includes everything needed to equip your application with configuration options. Parameterization is supported from the command line using Java system properties, using Spring properties from the application context and of course from the database.
The properties are defined using a Java based DSL and support features like fallback to other properties if undefined, default vales and a web interface to change properties live in the frontend.

** simple string property stored inside the database **
```
IProperty<String> DB_PROPERTY = PropertyBuilder.createStringProperty("dbproperty").database();

IPropertyService propertyService = [...];

// set the value
propertyService.setProperty(DB_PROPERTY, "my property");

// retrieve the previously set value
String dbproperty = propertyService.getProperty(DB_PROPERTY);
```