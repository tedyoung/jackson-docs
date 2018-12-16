## Type handling

* `@JsonSubTypes`: class annotation used to indicate sub-types of annotated type; necessary when deserializing polymorphic types using logical type names (and not class names)
* `@JsonTypeId`: property annotation used to indicate that the property value should be used as the `Type Id` for object, instead of using class name or external type name.
* `@JsonTypeInfo`: class/property annotation used to indicate details of what type information is included in serialization, as well as how.
* `@JsonTypeName`: class annotation used to define logical type name to use for annotated class; type name can be used as `Type Id` (depending on settings of `@JsonTypeInfo`)

## Object references, identity

* `@JsonManagedReference`, `@JsonBackReference`: pair of annotations used to indicate and handle parent/child relationships expressed with pair of matching properties
* `@JsonIdentityInfo`: class/property annotation used to indicate that `Object Identity` is to be used when serializing/deserializing values, such that multiple references to a single Java Object can be properly deserialized. This can be used to properly deal with cyclic object graphs and directed-acyclic graphs.
