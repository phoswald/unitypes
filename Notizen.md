# Notizen

## Features

- Null-safe Operators ( a?.b, a?(b), a ?? b) 
- Named parameters & Default Parameters
- Linux, Unix, POSIX
  - Files
  - Process
    - Arguments
    - Environment
    - Standard input, output and error
- Web
  - HTML
  - CSS

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

## Open Issues (t.b.d)

- How do we distinguish between an object or map literal and a code block?
  One possible solution would be to introduce an operator or keyword (e.g. `new`) for object or map literals.
  Another possible solution would be to use the quote operator (`#`) for literals.
- How do we distinguish between empty object and empty map?
  One possible solution would be to use specific literals such as `{}` or  `{-}` or `{[]}`. 
- How do we distinguish between a function call and a tag literal?
  One possible solution would be to use the quote operator (`#`) for literals.
- Should we allow text value to be unquoted (e.g. `text` instead `"text"`)?
  This would require quote and unquote operators for expressions (e.g. `# value` and `(expression)`).
