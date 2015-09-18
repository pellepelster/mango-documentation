
# Dictionary

The dictionary model is to outer bracket around all model elements that build an UI model for an entity.

## Label

The dictionary label describes the content of the dictionary in a way that is understandable for the user. There are two use cases for the dictionary label, for once describing the nature of the dictionary itself (e.g. *Country*, *Currency*, ...) and on the other hand giving a understandable representation for the instance of an entity that is manged by the dictionary (e.g. *Germany*, *Euro*).

Describing the entity/dictionary itself is analog to the entity label declaration given by the keywords **label** and **pluralLabel**

**dictionary label example**
```java
dictionary CountryDictionary {
    entity Country

    label "Country"
    pluralLabel "Countries"
}
```
If no **label**/**pluralLabel** is given the dictionary falls back to the entities label/pluralLabel.

To display an actual entity instance each dictionary may specify a set of controls that are used to display the entity:

**dictionary label control example**
```java
entity Country {
    string name
    string idsoCode
}

dictionary Country {
    entity Country

    dictionarycontrols {
		textcontrol CountryName {
			entityattribute name
		}
		textcontrol CountryIso {
			entityattribute isoCode
		}
    }

    labelcontrols {
		textcontrol ref CountryIso
		textcontrol ref CountryName
    }
}
```

The above example would display an instance of the country entity for Germany (name: Germany, isoCode: GER) as *GER, Germany*.
If no label controls are defined the dictionary falls back to the natural key of the entity (if defined).

**dictionary label control example (natural key fallback)**
```java
entity Country {
    entityoptions {
        naturalkey {
            name
        }
    }
    string name
    string idsoCode
}

dictionary Country {
    entity Country
}

```
The above example would display the germany entity instance as *Germany*.
