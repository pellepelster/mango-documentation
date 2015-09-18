## Control Basics

There are (as in nearly every UI framework) two types of UI elements, container and controls. Controls like for example text controls/date controls/... are directly map

Because a control for a single entity attribute is likely to be used in multiple places, the dictionary provides the possibility to define a common set of controls that may be reused in other parts of the model. The *stringAttribute1* for example may be used as a text control in a filter so search for entities with this attribute, in the search result to display the actual content and finally in the editor to edit data for this attribute.

**text control definition**
```java
entity Entity1 {
    string stringAttribute1
}

dictionary Dictionary1 {

    entity Entity1

    dictionarycontrols {
        TextControl1 {
            entityattribute stringAttribute1
        }
    }
    [...]
}
```

The now defined control can subsequently be used in an dictionary editor definition. The following example defines an editor named *Editor1* containing one **textcontrol** that just **ref**ers  to the already defined **textcontrol** *TextControl1*.

**usage of a defined text control**
```java
[...]

dictionary Dictionary1 {

    entity Entity1

    dictionarycontrols {
        TextControl1 {
            entityattribute stringAttribute1
        }
    }

    dictionaryeditor Editor1 {
        textcontrol ref TextControl1
    }
}
```

Like data types the control definitions also support the a simple inheritance model, for example the maximum text length that may entered in a text control can be influenced by the **maxLength** keyword.

**setting control properties**
```java
[...]

dictionary Dictionary1 {

    [...]

    dictionarycontrols {
        TextControl1 {
            entityattribute stringAttribute1
            maxLength 42
        }
    }

    [...]
}
```

Now if this control is reused somewhere this attribute may be overridden where used.

**overriding a control attribute**
```java
[...]

dictionary Dictionary1 {

    [...]

    dictionarycontrols {
        TextControl1 {
            entityattribute stringAttribute1
            maxLength 42
        }
    }

    dictionaryeditor Editor1 {
        textcontrol ref TextControl1 {
            maxLength 23
        }
    }
}
```

## Controls

### Common control properties

All control definitions share a common set of properties influencing behavior that is shared by all control types.

#### Entityattribute
#### Labels
#### Mandatory

#### Width
The width determines the size of the input control, unit of this value is characters. So a text control having he size 12 would be big enough to show 12 characters. The width may be inherited from a datatype definition (see common datatype properties in the entity model description)

**control width example**
```java
stringdatatype StringDatatype1 {
    width 32
}

entity Entity1 {
    string StringDatatype1 stringAttribute1
}

dictionary Dictionary1 {
    entity Entity1

	dictionarycontrols {
		textcontrol TextControl1 {
			entityattribute Entity1.stringAttribute1
		}
	}
}
```

In the above example the control *TextControl1* will have the size to display 32 character, whereas the *TextControl2* will be twice the size (because the size is overridden).

#### Readonly

### IntegerControl

As the name say, the IntegerControl is for input of numbers without fractions. The control takes care of formatting and input validation to ensure that only valid integers are entered.

**integercontrol example**
```java
integerdatatype IntegerDatatype1 {
}

entity Entity1 {
    integer IntegerDatatype1 integerDatatype1
}

dictionary Dictionary1 {
    entity Entity1

	dictionarycontrols {
		textcontrol IntegerControl1 {
			entityattribute Entity1.integerDatatype1
		}
	}
}
```

#### Rating

The IntegerControl supports different input types, the default type is `textbox`  as described above.
Additionaly the type `rating` is supported, that (when activated) display a five star rating widget.

**integercontrol rating example**

```java
integerdatatype IntegerDatatype1 {
}

entity Entity1 {
    integer IntegerDatatype1 integerDatatype1
}

dictionary Dictionary1 {
    entity Entity1

	dictionarycontrols {
		textcontrol IntegerControl1 {
			entityattribute Entity1.integerDatatype1
			inputtype rating
		}
	}
}
```
