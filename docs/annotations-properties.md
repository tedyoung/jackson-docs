*source: https://github.com/FasterXML/jackson-annotations/wiki/Jackson-Annotations*


### Property Naming

* `@JsonProperty` (also indicates that property is to be included) is used to indicate external property name, name used in data format (JSON or one of other supported data formats)
    * `@JsonProperty.value`: name to use
    * `@JsonProperty.index`: physical index to use, if dataformat (other than JSON) is index-based
    * `@JsonProperty.defaultValue`: textual default value defined as metadata. **NOTE**: core databind does NOT make any use of this value; it is currently only exposed to extension modules.

### Property Inclusion

* `@JsonAutoDetect`: class annotation used for overriding property introspection definitions
* `@JsonIgnore`: simple annotation to use for ignoring specified properties:
    * Only needs to be added to one of accessors/mutators (field, getter/setter, constructor parameter), but will have effect on the "whole" property: that is, adding annotation to a "getter" will also disable "setter"
        * ... unless "setter" has `@JsonProperty`, in which case this is considered a "split property" with enabled "setter" but no "getter" ("read-only", so that property may be read from input, but is not written output)
* `@JsonIgnoreProperties`: per-class annotation to list properties to ignore, or to indicate that any unknown properties are to be ignored.
    * On serialization, ```@JsonIgnoreProperties({"prop1", "prop2"})``` ignores listed properties
    * On deserialization, ```@JsonIgnoreProperties(ignoreUnknown=true)``` ignores properties that don't have getter/setters
* `@JsonIgnoreType`: per-class annotation to indicate that all properties of annotated type are to be ignored.
* `@JsonInclude`: annotation used to define if certain "non-values" (nulls or empty values) should not be included when serializing; can be used on per-property basis as well as default for a class (to be used for all properties of a class)

### Property documentation, metadata

* `@JsonPropertyDescription` (added in 2.3): Annotation used to define a human readable description for a logical property.
    * Not use by core databinding, but is used by [JSON Schema generator](../../jackson-module-jsonSchema) for adding description in schema.
