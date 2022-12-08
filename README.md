
# Unitypes 

> One Type System to Rule Them All 

Unitypes is a univeral type system for data storage, communication and computing. 
Unitypes provides a portable programming languange for different platforms.
The power of Unitypes is based on its simplicity.

## Design Principles

- **Universality**: Provide expressive power by reducing restrictions instead of by adding features.
- **Strong typing**: Use the type system for compile time validation and for better runtime performance.
- **Identity vs. State**: Distinguish between an object's identity (an immutable reference)
  and its state (a mutable value).
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
