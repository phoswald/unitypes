
# Desirable Properties

- Values should be immutable
- Variables should allow a single assignment only
  - a = b genügt, a := b braucht es nicht
  - Named Parameters sind trivial: foo(arg1=val1, arg2=expr2)
- Functions should be pure
- Frameworks sind schlecht, Libraries sind besser
- Exceptions passen nicht zu strikt funktionalen Sprachen 
  (throwing exceptions is considered a side effect)
  (aber Exceptions können auch als syntactic sugar für Monaden angesehen werden)
- Callbacks und Futures sind nicht wirklich wünschenswert, async / await (in JavaScript) oder 
  Goroutinen & Channels (Go) sind eleganter, da sie verschachtelten Code verhindern.
- Emphasize readable code

# Concepts

Algebra
- Product type (record, tuple)
- Sum type (tagged union, disjoint union, discriminated union, variant, choice)

Java 
- Marker Interfaces sind schlecht (-> Serializable)
- Type coercion ist schlecht (1.0 == 1 ???)
- Checked Exceptions haben sich nicht wirklich bewährt

Scala
- kein Punkt vor Strich?
- kein break, continue
- Named Parameters mit =, gleich wie Zuweisung

Go
- Polymorphismus ausschliesslich via Interfaces
- Composition over Inheritance at language level
- Nebenläufigkeit: 
  - Keine Threads und Locks als Primitiven
  - Stattdessen Goroutinen und Channels  (→ CSP)
  - Syntax “go foo(bar)” führt Funktion asynchron aus
  - Syntax “c <- val” und “val := <- c” sendet bzw empfängt Wert.
  - Mit dem Keyword “select” kann syntaktisch ähnlich wie “switch” auf einen von mehreren Channeln gewartet werden.
  - Keine Callbacks oder Futures notwendig
  - Allgemeiner als Aktoren, diese können einfach so implementiert werden
  - Egal ob ein oder mehrere echte Threads
  - Race Conditions nicht ausgeschlossen, solange Objekte mutierbar sind
- Imports sind URLs, mit Kurzformen 

Typescript
- Imports sind Pfade

JavaScript
- Syntax “async function f() { }” definiert eine Funktion mit einem Promise
- Syntax “v = await p;” wartet auf Promise. 
- Ist eigentlich nur eine komplexe Form von Syntactic Sugar, da es nicht wirklich blockiert und
  nur innerhalb von Methoden mit “async” verwendet werden kann.

Rust
- Fail Safe (im Gegensatz zu C/C++): 
  - “u32” bzw. “mut u32” statt “const int” bzw. “int”.
  - keine undefinierten Zugriffe, z.B “array[index]”
- Ownership und Channels für Thread Safety 

# Syntax

## Object Construction - Java

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

## Object Construction - ideal

~~~
Person {
    name = “Philip”
    age = 40
}
~~~

Funktioniert, falls ‘=’ immer eine neue Variable definiert, wie oft das ‘val’ Keyword oder ‘:=’ in Go. Damit bleibt ‘:’ frei und kann eindeutig für Typisierung verwendet werden.
