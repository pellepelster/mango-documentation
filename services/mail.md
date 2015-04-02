# Mail

The provided `MailService` is a thin layer above [Springs mail support](http://docs.spring.io/spring-integration/reference/html/mail.html) using [Apache Velocity](http://velocity.apache.org/) as template engine.
To make the mail service available, include `MangoMailApplicationContext.xml` in your application context configuration.

**Velocity mail template example**
```java
Hello ${name},

welcome to ${link}, your username is ${username}
```

**example mail service usage**
```java
@Autowired
MailService mailService;

Map<String, Object> model = new HashMap<String, Object>();
model.put("name", "Steve");
model.put("link", "http://www.example.org");
model.put("username", "steve23");

mailService.sendMail("steve@yahoo.com", "classpath://mailtemplate.vm", model);

```

## Configuration

The mail service is configured via Mangos configuration file, using the following parameters

| parameter name | description | default |
| -- | -- | -- |
| mail.sender.host | smtp host | localhost |
| mail.sender.port | smtp port | 25 |
| mail.sender.username | smtp username | &lt;none&gt; |
| mail.sender.username | smtp password | &lt;none&gt; |
| mail.sender.from | defaut from for mails | mail@example.org |
