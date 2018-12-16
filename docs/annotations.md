*source: https://github.com/FasterXML/jackson-annotations/wiki/Jackson-Annotations*

## Properties

* [Properties](annotations-properties.md): Naming, Inclusion, and Describing
* [Mix-ins](annotations-mixins.md): Mixing in annotations for code you don't own.
* [Serialization and Deserialization](annotations-serialization.md): Control how data is serialized (written out) and deserialized (read in).
* [JAX-RS](annotations-jax-rs.md): For use with JAX-RS, e.g., Jersey and Dropwizard.

### Type handling

* `@JsonSubTypes`: class annotation used to indicate sub-types of annotated type; necessary when deserializing polymorphic types using logical type names (and not class names)
* `@JsonTypeId`: property annotation used to indicate that the property value should be used as the `Type Id` for object, instead of using class name or external type name.
* `@JsonTypeInfo`: class/property annotation used to indicate details of what type information is included in serialization, as well as how.
* `@JsonTypeName`: class annotation used to define logical type name to use for annotated class; type name can be used as `Type Id` (depending on settings of `@JsonTypeInfo`)

### Object references, identity

* `@JsonManagedReference`, `@JsonBackReference`: pair of annotations used to indicate and handle parent/child relationships expressed with pair of matching properties
* `@JsonIdentityInfo`: class/property annotation used to indicate that `Object Identity` is to be used when serializing/deserializing values, such that multiple references to a single Java Object can be properly deserialized. This can be used to properly deal with cyclic object graphs and directed-acyclic graphs.

### Meta-annotations

This group includes annotations used on other annotations.

* `@JacksonAnnotation`: marker annotation added to all Jackson-defined annotations (which includes all other annotations contained in this package)
* `@JacksonAnnotationsInside`: marked annotation used to indicate that a custom annotation contains Jackson annotations; used to allow "annotation bundles", custom annotations that are annotated with Jackson annotations (why? to allow adding just a single annotation to represent set of multiple Jackson annotations)

## Related

It is also possible to use [JAXB annotations](https://github.com/FasterXML/jackson-module-jaxb-annotations) in addition to or instead of these core annotations.
