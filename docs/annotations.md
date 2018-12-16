<!-- extracted from https://github.com/FasterXML/jackson-annotations/wiki/Jackson-Annotations -->


* [Properties](annotations-properties.md): Naming, Inclusion, and Describing
* [Mix-ins](annotations-mixins.md): Mixing in annotations for code you don't own.
* [Serialization and Deserialization](annotations-serialization.md): Control how data is serialized (written out) and deserialized (read in).
* [JAX-RS](annotations-jax-rs.md): For use with JAX-RS, e.g., Jersey and Dropwizard.
* [Object Identity, Types, and References](annotations-identity-types-refs.md): For how object references and identity should be handled, as well as what parts of types should be serialized.


## Meta-annotations

This group includes annotations used on other annotations.

* `@JacksonAnnotation`: marker annotation added to all Jackson-defined annotations (which includes all other annotations contained in this package)
* `@JacksonAnnotationsInside`: marked annotation used to indicate that a custom annotation contains Jackson annotations; used to allow "annotation bundles", custom annotations that are annotated with Jackson annotations (why? to allow adding just a single annotation to represent set of multiple Jackson annotations)

## Related

It is also possible to use [JAXB annotations](https://github.com/FasterXML/jackson-module-jaxb-annotations) in addition to or instead of these core annotations.
