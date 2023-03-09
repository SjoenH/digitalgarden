---
{"dg-publish":true,"permalink":"/vault-one/programming/c-sharp/inheritance/"}
---

# Inheritance
A class may inherit methods and properties from another class by using the "`:`" keyword.

> Note, inheritance can be done for "all type of classes". Not only [[Vault One/Programming/CSharp/Interface\|Interface]]s. 

## Benefits
- Code re-use
- Polymorphic behaviour (see [[Vault One/Programming/CSharp/Polymorphism\|Polymorphism]])

## Example

```c#
public class PresentationObject
{ 
	// Common shared ccode
}

public class Text : PresentationObject
{
	// Code specific to Text
}
```

In the example above, the `Text`-class inherits from `PresentationObject`-class.
