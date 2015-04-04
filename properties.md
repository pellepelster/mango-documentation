# Properties

Mango includes everything needed to equip your application with configuration options. Parameterization is supported from the command line using Java system properties, using Spring properties from the application context and of course from the database.
The properties are defined using a Java based DSL and support features like fallback to other properties if undefined, default vales and a web interface to change properties live in the frontend.

## Defining properties

Each property is identified by an unique key that is used on the command line/application content/database. 
Furthermore an extra name may be defined that is used as a human readable description for the (in most cases) more technical key. 
Starting point to create a new property is the `PropertyBuilder`, see below for a simple example.

** simple string property stored inside the database **
```
IProperty<String> DB_PROPERTY = PropertyBuilder.createStringProperty("dbproperty").name("our first database property").database();

IPropertyService propertyService = [...];

// set the value
propertyService.setProperty(DB_PROPERTY, "my property");

// retrieve the previously set value
String dbproperty = propertyService.getProperty(DB_PROPERTY);
```

## Setting default values

Useful defaults for your properties can be defined using the `default(...)` method.

** string property with a default **
```
IProperty<String> DB_PROPERTY = PropertyBuilder.createStringProperty("dbproperty").default("abcdef").database();

// property is not set and returns the default 'abcdef'
String dbproperty = propertyService.getProperty(DB_PROPERTY);

assertEquals("abcdef", dbproperty);

```

## Setting fallback values
## Adding properties to the web UI
