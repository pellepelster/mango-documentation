# Services

Mango provides a couple of basic services that are often needed in web applications, that are described in this chapter.

Each logical group of services is defined by an extra application context configuration file. To make use of the services you have to include them when setting up your own application context. All generated application context configurations are postfixed with `*-gen.xml`. Most services need an basic context configuration named `MangoBaseApplicationContext.xml`.

**example web.xml configuration**
```xml
<?xml version="1.0" encoding="UTF-8"?>
<web-app xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" [...] >

    <!-- [...] -->

	<listener>
		<listener-class>org.springframework.web.context.ContextLoaderListener</listener-class>
	</listener>

    <context-param>
		<param-name>contextConfigLocation</param-name>
		<param-value>

            <!-- enable DB access -->
            classpath:/DBBaseApplicationContext.xml,

            <!-- basic app. context configuration for Mango -->
            classpath:/MangoBaseApplicationContext.xml,

            <!-- basic generated application context configuration for Project1 -->
            classpath:/Project1BaseApplicationContext-gen.xml,

            <!-- generated DB context for Project1 (value like persistence unit and JDNI name are derived from the model) -->
            classpath:/Project1DB-gen.xml,

            <!-- enables mangos services (IBaseEntityService, ...) -->
            classpath:/MangoSpringServices-gen.xml,

            <!-- generated rest service controller for services defined in Project1 -->
            classpath:/Project1RestRemoteServices-gen.xml,

            <!-- enables mangos mailing functionality -->
            classpath:/MangoMailApplicationContext.xml

		</param-value>
	</context-param>

</web-app>
```
