# Entity API

## REST

For each entity a REST API is generated that can be reached via the base URL
`http://{url}/remote/api/entity/country/{action}` the available `{action}s` provide several way the access the entites in the system which are described in the following chapters.

## Load by id

If you know the id of the entity you want to load, you can use `{baseUrl}/byid/{entityId}` followed by the entity id.

**load by id example**

```bash
$ curl http://mango-demo-dev.elasticbeanstalk.com/remote/api/entity/country/byid/1

{
  "id": 1,
  "countryIsoCode2": "AF",
  "countryIsoCode3": "AFG",
  "countryRating": null,
  "countryName": "Afghanistan",
  [...]
}
```

## Load by natural key

If the entity has an natural key, this key can also be used to load the entity using `{baseUrl}/bynaturalkey/{naturalKey}` followed by the natural key.

**load by natural key example**

```bash
$ curl http://mango-demo-dev.elasticbeanstalk.com/remote/api/entity/country/bynaturalkey/af

{
  "id": 1,
  "countryIsoCode2": "AF",
  "countryIsoCode3": "AFG",
  "countryRating": null,
  "countryName": "Afghanistan",
  [...]
}
```

## Load by expression

To load more than one entity you can use a query to match the entities send as query parameter `{baseUrl}/query?query={query}` or as content of the HTTP request.
The expression is based on the [Spring Expression Language (SpEL)](http://docs.spring.io/spring/docs/current/spring-framework-reference/html/expressions.html).

**load by query expression example**

```
$ curl http://mango-demo-dev.elasticbeanstalk.com/remote/api/entity/country/query?query=countryName%20matches%20%27a%%27

[
    {
      "id": 1,
      "countryIsoCode2": "AF",
      "countryIsoCode3": "AFG",
      [...]
    },
    {
      "id": 6,
      "countryIsoCode2": "AS",
      "countryIsoCode3": "ASM",
      [...]
    },
	{
      "id": 7,
      "countryIsoCode2": "VI",
      "countryIsoCode3": "VIR",
      "countryRating": null,
      "countryName": "Virgin Islands, U.s.",
      [...]
    }
]
```

## Expressions

The expression syntax is loosely based on Java/JavaScript (see [SpEL documentation](http://docs.spring.io/spring/docs/current/spring-framework-reference/html/expressions.html) for more info). All attributes that are modeled in the entity model can be used, combined with a set of comparators and the usual **||** and **&&** boolean operators as well as brackets **()**.

**example expression**
```bash
countryName == 'France' || (countryCode > 23 && countryName matches 'Ger%')
```

#### String comparators

**equals**

`countryName == 'abc'`

**begins with**

`countryName matches 'abc%'`
