# Mail

The provided `MailService` is a thin layer over [Springs mail support](http://docs.spring.io/spring-integration/reference/html/mail.html) using [Apache Velocity](http://velocity.apache.org/) as template engine.

The `MailService` can be injected like any other Spring bean



## Configuration

The mail service is configured via Mangos configuration file, using the following parameters

| parameter name | description | default |
| -- | -- | -- |
| mail.sender.host | smtp host | localhost |
| mail.sender.port | smtp port | 25 |
| mail.sender.username | smtp username | &lt;none&gt; |
| mail.sender.username | smtp password | &lt;none&gt; |
| mail.sender.from | defaut from for mails | mail@example.org |
