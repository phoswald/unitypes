# Design Principles

- Type safetly
  - Null safety
- Pure Functions
  - ...
- Identity vs. State
  - State as immutable values
  - Identity as references (t.b.d: URI)
- Unix Philosopy
  - ...
- Opionated
  - ...
- Minimize runtime overhead (C++, Rust, Go)
  - No classpath scanning (CDI, Java EE)
  - No reflection
- keine undefiniteren Stellen in der Spezifikation 
  (Java vs. C/C++, https://www.heise.de/meinung/25-Jahre-Silberner-Glueckwunsch-Java-4726151.html)
- Quellcode und Dokumentation an einer Stelle vereinen
  (JavaDoc, https://www.heise.de/meinung/25-Jahre-Silberner-Glueckwunsch-Java-4726151.html)

# Anti Patterns

- Java
  - Annotations (as used in CDI / EBJ)
  - primitive types
  - Type erasure (C++ template are superior, actually, a template/generic should be a pure function)
  - Builders (use object construction syntax instead)
  - Callback hell and futures (use async / await instead) 
  - Streams (control flow should have explicit keywords: if, for, try, throw, …)

# Features

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
