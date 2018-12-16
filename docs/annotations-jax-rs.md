
## Use with JAX-RS (DropWizard, Jersey)

Although value annotations are usable anywhere Jackson itself is, without extra work, there are some additional things to consider when using Jackson on a JAX-RS container.
Such containers require use of [Jackson JAX-RS provider](../../jackson-jaxrs-providers) (or equivalent implementation of bit of glue to register Jackson for converting content between external format like JSON, and POJOs).

One specific limitation is that although Jackson can introspect annotations from within values it is passed, it does not have direct access to annotations on Resource Methods. Provider is handed these definitions, however, and it can use some of the annotations.

For more information, check out [JAX-RS provider wiki](../../jackson-jaxrs-providers/wiki), but short story is that following annotations are supported to some degree:

* `@JsonView`: applicable for both return value (method annotation) and input argument(s) (parameter annotation)
* `@JsonRootName`: similar applicable to return and input value(s).
* `@JacksonAnnotationsInside`: fully supported so you can create and use "annotation bundles"
* `@JacksonFeature`: JAX-RS provider specific annotation (not included in `jackson-annotations`) allows enabling/disabling `SerializationFeature`s and `DeserializationFeature`s for the endpoint

also note that annotations are NOT shared (that is, deserializer is NOT passed method annotations; nor is serializer passed parameter annotations), so in some cases you may need to violate DRY principle and add duplicate annotations
