
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

## Entwurf vom Notizbuch

~~~
-1.23E-3

"text"

0xDEADBEEF

<.field[key]:tag>
<:tag.field:tag[key]>

{ field = value, ... }

[ - value, ... ]
[ [key] = value, ... ]

:tag value
~~~

~~~
-1.23E-3

"text"

0xDEADBEEF

</field/[key]/@tag>
</@tag/field/@tag/[key]>

{ field = value, ... }

[ - value, ... ]
[ [key] = value, ... ]

@tag value
~~~

## Entwurf vom Fresszettel

~~~
123
1.23
1.23E5
-1.23E-5
~~~

~~~
"text"
" \\ \t \r \n "
'text'
~~~

~~~
0x
0xDEADBEEF
~~~

~~~
</field/tag/field/key>
</field/@tag/field/[key]>
</field/@tag/field/#key>
<.field:tag.field[key]>
</field/:tag/field/[key]>
@.field:tag.field[key]
@{.field:tag.field[key]}
${}
~~~

~~~
{ }
{ field = value, field = value }
{ field value, field value }
{ - value, - value }
{ [key] value }

[ ]
[ - value, - value ]
[ key = value ]
[ value, value ]
[ [key] = value ]

tag value
@tag value
[tag] value
<tag> value
: tag = value
~~~


~~~
field = value
field = { }
field = tag value
field = tag { }
- value
- { }
- tag value
- tag { }
[key] = value
[key] = { }
[key] = tag value
[key] = tag { }
~~~

~~~
( expr )

flow() { stmt, stmt }
obj { }
# { }
~~~

~~~
name : type = value
name = value : type
func ( expr, expr )
~~~

~~~
value
  123
  "text"
  0xDEADBEEF
  <field@tag.field[key]@tag>
  <field.@tag.field[key].@tag>
  </field/@tag/field/[key]/@tag>        allows ‘.’ in fields/tags
  {...}
  [...]
  tag value
  @tag value                        more explicit, better?

field | tag
  ident                            allow qualified? ‘.’?
  ("text")                        required?

key
  value

object
  { name = “Philip”, age = 43 }

list
  [ “red”, “blue”, “green” ]
  [ - { name = “Philip” }, - { name = “Marc” } ]

map
  [ [“p1”] = person { }, [“p2”] = person { } ]
  [ [[“p1”,“p2”]] = person { } ]

set
  [ [“v1”]={} ]

tag
  person { name = “philip” }
  html [ 
  head [ title “...” ]
  body [ 
    h1 “headline”, 
    p [ “text”, a [ href “http://foo.com, “foo” ] ]
    p [ 
      span “text”
      a { href=“http://foo.com”, children=[ span “foo” ] } 
    ] 
  ]
]

extension
  {
    labels = {
      foo = “a” 
      com_foo_bar = “x”
    }
  }

type
  person = record [ name = string, age = integer ]

  animal = union [ 
    dog = record { }
    cat = record { }
  ]

  list = { } |
         { head=pair, tail=list? }
  pair = { key=value, value=value }

record : map<name,any>
labels : map<qname,any>
~~~

~~~
"  '
=  :  ,  ;
()                evaluation, function application        
{}                structure
[]            
<>            
!
#                quote            
$                unquote
@                key, tag, reference
%
&
\                escape
^
_
`
|
~

: Json, Go, Swift, Yaml 
= C#
~~~

## Object Construction in Programming Languages

### Java

~~~
html(
    body(
       h1(“Titel”),
       p(“Some paragraph...”)
)
~~~

→ from j2tml HTML code generator library

~~~
new Person() {{
    name = “Philip”;
    age = 40;
    setX(x);
}}
~~~

→ usually considered an Anti-Pattern

### ideal

~~~
Person {
    name = “Philip”
    age = 40
}
~~~

Funktioniert, falls ‘=’ immer eine neue Variable definiert, wie oft das ‘val’ Keyword oder ‘:=’ in Go. Damit bleibt ‘:’ frei und kann eindeutig für Typisierung verwendet werden.
