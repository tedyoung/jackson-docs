# Finding Jackson JavaDocs

Sadly, the SEO situation for Jackson javadoc is not very good; random google searches tend to find versions of Jackson at, well, random.

Jackson 2.x is maintained via a slew of individual github pages in the FasterXML Organization. 
The javadoc for each project is published via its gh-pages branch. So, to find the javadoc for a class, you can construct a URL like this for classes in `jackson-core`:

    https://fasterxml.github.io/jackson-core/javadoc/2.9.8/

To find JavaDoc for other projects, substitute `jackson-core` with the name of the particular project you are looking for.

You can also access JavaDocs via links in the individual project repositories.

## Core Repositories

 * [Annotations](https://github.com/FasterXML/jackson-annotations)
 * [Core (streaming API)](https://github.com/FasterXML/jackson-core)
 * [Databind](https://github.com/FasterXML/jackson-databind)

## Textual Data Formats

* [CSV](https://github.com/FasterXML/jackson-dataformat-csv/wiki)
* [Properties](https://github.com/FasterXML/jackson-dataformat-properties/wiki) (New since 2.7.4)
* [XML](https://github.com/FasterXML/jackson-dataformat-xml/wiki)
* [YAML](https://github.com/FasterXML/jackson-dataformat-yaml/wiki)

## Binary Data Formats
* [Avro](https://github.com/FasterXML/jackson-dataformats-binary/wiki)
* [CBOR](https://github.com/FasterXML/jackson-dataformats-binary/wiki)
* [Protobuf](https://github.com/FasterXML/jackson-dataformats-binary/wiki) (New since 2.6)
* [Smile](https://github.com/FasterXML/jackson-dataformats-binary/wiki)
