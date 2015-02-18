# Configuration

Mangos behaviour can be customized by numerous configuration parameters that are stored in a central configuration property file.
Because the file is read by Springs [PropertySourcesPlaceholderConfigurer](http://docs.spring.io/spring/docs/current/javadoc-api/org/springframework/context/support/PropertySourcesPlaceholderConfigurer.html)
in can be either a simple line bases property file, or an XML property file (see [java.util.Properties](http://docs.oracle.com/javase/8/docs/api/java/util/Properties.html) fore more information on the format).
Also all properties can be overriden via Java system properties (`-Dproperty=value`). The default location for the coniguration file expects it on the classpath root (`classpath:/mango.properties`) and can be overidden using the system property (`-Dmango.config.file=/tmp/myownfile.properties`).


To get an overview over the current running configuration an overview ist dumped to system out on Springs application content startup.

**Example configuration dump**

```bash
=========================================================
|                  Mango Configuration                  |

=========================================================

+-------------------------------------------------------+
|                      Properties                       |
+-------------------------------------------------------+
|property            |value |default                    |
+--------------------+------+---------------------------+
|mango.config.file   |<none>|classpath:/mango.properties|
+--------------------+------+---------------------------+
|mail.sender.host    |<none>|localhost                  |
+--------------------+------+---------------------------+
|mail.sender.port    |<none>|25                         |
+--------------------+------+---------------------------+
|mail.sender.username|<none>|<none>                     |
+--------------------+------+---------------------------+
|mail.sender.password|<none>|<none>                     |
+--------------------+------+---------------------------+
|hibernate.sql.show  |<none>|false                      |
+--------------------+------+---------------------------+
|hibernate.sql.format|<none>|false                      |
+--------------------+------+---------------------------+

```
