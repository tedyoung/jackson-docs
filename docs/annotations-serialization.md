## General Annotations

* `@JsonFormat`: general annotation that has per-type behavior; can be used for example to specify format to use when serializing Date/Time values.
* `@JsonUnwrapped`: property annotation used to define that value should be "unwrapped" when serialized (and wrapped again when deserializing), resulting in flattening of data structure, compared to POJO structure.
* `@JsonView`: property annotation used for defining View(s) in which property will be included for serialization, deserialization.

## Deserialization-Specific

* `@JacksonInject`: annotation to indicate that property should get its value via "injection", and not from data (JSON).
* `@JsonAnySetter`: annotation used for defining a two-argument method as "any setter", used for deserializing values of otherwise unmapped JSON properties
* `@JsonCreator`: annotation used for indicating that a constructor or static factory method should be used for creating value instances during deserialization.
* `@JsonSetter`: alternative to @JsonProperty, for marking that specified method is a "setter-method"
* `@JsonEnumDefaultValue` (added in 2.8): annotation used for defining a default value when deserializing unknown Enum values. Requires config `READ_UNKNOWN_ENUM_VALUES_USING_DEFAULT_VALUE` feature to be enabled. See example snippet in [Deserialization Features](https://github.com/FasterXML/jackson-databind/wiki/Deserialization-Features#value-conversions-coercion)

## Serialization-Specific Annotations

* `@JsonAnyGetter`: annotation used to define a getter as "any getter", which returns a `java.util.Map`, contents of which will be serialized as additional properties for JSON Object, along with regular properties that the Object may have.
* `@JsonGetter`: alternative to @JsonProperty, for marking that specified method is a "getter-method"
* `@JsonPropertyOrder`: annotation for specifying order in which properties are serialized
* `@JsonRawValue`: per-property marker that can be used to specify that the value of property is to be included in serialization ''exactly'' as is, with no escaping or decoration -- useful for embedding pre-serialized JSON (or whatever data format is being used) in output
* `@JsonValue`: per-property marker to indicate that the POJO should serialization is to be done using value of the property, often a `java.lang.String` (like annotation `toString()` method)
* `@JsonRootName`: class annotation used to indicate name of "wrapper" entry used for root value,  if root-wrapping is enabled
