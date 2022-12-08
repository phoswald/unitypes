
# Syntax

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
{ [key] = tag value }
{ - tag value }

{ attribute : tag = value }
{ [key] : tag = value }
{ - : tag = value }

{ attribute tag value }
{ [key] tag value }
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

## Entwurf vom 17. Januar

~~~
1.23

"text"

0xDEADBEEF

<...>

{
  name = value
  name = tag : value

  [key] = value
  [key] = tag : value

  - value
  - tag : value
}

[

]

tag : value




$
@
#





name = tag[key] { }
~~~

# Open Issues (t.b.d)

- How do we distinguish between an object or map literal and a code block?
  One possible solution would be to introduce an operator or keyword (e.g. `new`) for object or map literals.
  Another possible solution would be to use the quote operator (`#`) for literals.
- How do we distinguish between empty object and empty map?
  One possible solution would be to use specific literals such as `{}` or  `{-}` or `{[]}`. 
- How do we distinguish between a function call and a tag literal?
  One possible solution would be to use the quote operator (`#`) for literals.
- Should we allow text value to be unquoted (e.g. `text` instead `"text"`)?
  This would require quote and unquote operators for expressions (e.g. `# value` and `(expression)`).
