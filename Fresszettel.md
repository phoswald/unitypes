# Fresszettel

## Types

- Root
  - Simple type
    - Number
    - Text
      - Identifier
    - Binary
    - Reference type
      - Absolute Reference
      - Relative Reference
    - Product type
      - Object (different element types)
      - Dictionary (same element types)
        - List (keys are 1..n)
    - Sum type
      - Tagged Union
    - Function type
    - Type type


- value
  - simple                          (a.k.a scalar)
    - number               -3.14E+3
    - text                "foo"
      - enum/ident        foo
        - boolean        true
    - binary            0x1234BABE
  - reference              </foo/bar/3>
    - absolute
    - relative
  - complex                            (a.k.a product)
    - struct             { foo: “bar” }
    - list                 [ “foo”, “bar” ]
    - map                  [ “foo”: “bar” ]
    - tagmap
  - tag                    foo “bar”        (a.k.a sum)
  - function               ->
  - type                   ::
  - localname                        (ident)
  - qualifiedname                    (ident^n)
  - (temporal)
    - localdatetime
    - localdate
    - localtime
    - zoneddatetime, offsetdatetime
    - instant
    - duration
    - period
    - zonedid, zoneoffset
  - (geo)
    - x y
    - x y z
    - lat lon
    - lat lon elev
  - version





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
