
# Unitypes 

> One Type System to Rule Them All 

Unitypes is a univeral type system for data storage, communication and computing. 
Unitypes provides a portable programming languange for different platforms.
The power of Unitypes is based on its simplicity.

## Design Principles

- **Universality**: Provide expressive power by reducing restrictions instead of by adding features.
- **Strong typing**: Use the type system for compile time validation and for better runtime performance.
- **Identity vs. State**: Distinguish between an object's identity (an immutable reference) and its state (a mutable value).
- **Functional programming**: Do computation based on immutable values and pure functions.
- **Unix Philosopy**
  - Do one thing at a time, and do it well. 
  - Use composition to build larger systems. 
  - Store and exchange data by using strongly typed values.
- **Opionated**: Promote one way to do a thing.
- **Minimize runtime overhead**
  - Allow compilation to native code and static linking (like C++ or Go)
  - Do not rely on reflection or classpath scanning (like many Java EE standards)

## Metamodel

Type         | Description
-------------|------------
**Simple**   |
Number       | A decimal number, optionally fractional.
Text         | A sequence of unicode characters.
Binary       | A sequence of bytes.
Reference    | A hierarchical path. Each part attribute or tag name or a map key.
**Product**  |
Object       | A set of attributes and values. The type of the value is defined by the attribute.
Map          | A set of key/value-pairs. All keys and all values are of the same respective types.
List         | A map where the all keys are integers.
**Sum**      |
Tag          | A tag and a value. The type of the value is defined by the tag.

## Values

### Number

~~~
123
123.456
-1.23E-3
~~~

### Text

Text values are surrounded by double quotes.
The backslash (`\`) serves as an escape character.
Valid escape sequences are: `\\`, `\"`, `\r`, `\n`, `\t`

~~~
"text"
"first line\nsecond line\n"
""
~~~

Other possible solutions (t.b.d):

~~~
text
~~~

### Binary

Binary values are prefixed by `0x` and use uppercase hexadecimal values.

~~~
0x1234
0xDEADBEEF
0x
~~~

### Reference

~~~
@.attribute
@[key]
@:tag
@.attribute[key].attribute:tag.attribute

@:persons["P-001"].name
@:persons["P-001"].addresses[1]:email
~~~

### Object, Map and List

~~~
{ attribute = value, attribute = value }
{ [key] = value, [key] = value }
{ - value, - value }

{ name = "Philip", age = 42 }
{ ["CHF"] = "Swiss Franc", ["EUR"] = "Euro" }
{ ["P-001"] = { name = "Philip", age = 42 } }
{ [10] = "Ten", [20] = "Twenty" }
{ - "One", - "Two" }
{ - { name = "Philip", age = 42 } }
~~~

Other possible solutions (t.b.d):

~~~
{ attribute value }
{ [key] value, [key] value }
{ - value, - value }
~~~

### Tag

~~~
tag value

person { name = "Philip", age = 42 }
years 42
~~~

Other possible solutions (t.b.d):

~~~
{ attribute = tag value }
{ attribute : tag = value }
{ attribute tag value }
{ [key] = tag value }
{ [key] : tag = value }
{ [key] tag value }
{ - tag value }
{ - : tag = value }
{ - tag value }
~~~

## Functions, Statements and Expressions

~~~
function = (argument: type, argument: type): type -> expression 
~~~

~~~
variable = expression
variable : type = expression
~~~

~~~
value && value
value || value
value + value
value - value
value * value
value / value

-value
!value

value ?? default

object.attribute
object?.attribute
collection[key]
collection?[key]

function(expression, expression)
function(argument = expression, argument = expression)
function?(expression, expression)
~~~

# Open Issues (t.b.d)

- How do we distinguish between an object or map literal and a code block?
  One possible solution would be to introduce an operator or keyword (e.g. `new`) for object or map literals.
  Another possible solution would be to use the unquote operator (`#`).
- How do we distinguish between empty object and empty map?
  One possible solution would be to use specific literals such as `{}` or  `{-}` or `{[]}`. 
- How do we distinguish between a function call and a tag literal?
  One possible solution would be to use the unquote operator (`#`).
- Should we allow text value to be unquoted (e.g. `text` instead `"text"`)?
  This would require quote and unquote operators for expressions (e.g. `# value` and `(expression)`).
