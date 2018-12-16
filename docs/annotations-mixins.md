<!-- extracted from: https://github.com/FasterXML/jackson-docs/wiki/JacksonMixInAnnotations -->

*WARNING* -- content bit out of date, could use rewriting

## Mix-in Annotations

"Mix-in" annotations are a way to associate annotations with classes, without modifying (target) classes themselves, originally intended to help support 3rd party datatypes where user can not modify sources to add annotations.

With mix-ins you can:

 1. Define that annotations of a '''mix-in class''' (or interface)
 2. will be used with a '''target class''' (or interface) such that it appears
 3. as if the ''target class'' had all annotations that the ''mix-in'' class has (for purposes of configuring serialization / deserialization)

You can think of it as kind of aspect-oriented way of adding more annotations during runtime, to augment statically defined ones.

### How does it work?

You just configure `ObjectMapper` with associations between mix-in and target classes, to be used for serialization and deserialization.

You do this by, for example:

```java
objectMapper.addMixInAnnotations(Target.class, MixIn.class);
```

Or, you can do this more conveniently via `Module` interface: if you extend `SimpleModule`, you can do:

```java
public class MyModule extends SimpleModule
{
  public MyModule() {
    super("ModuleName", new Version(0,0,1,null));
    setMixInAnnotation(targetClass, mixinClass);
  }
}
```

which will register mix-ins as expected.

### Example use case

Let us consider an example, where you have an existing class ("target class") {{{Rectangle.class}}}, defined as:

```java
public final class Rectangle {
    final private int w, h;
    public Rectangle(int w, int h) {
      this.w = w;
      this.h = h;
    }
    public int getW() { return w; }
    public int getH() { return h; }
    public int getSize() { return w * h; }
  }
```

which would serialize, but not quite as you would want since:

* Names "w" and "h" seem silly -- why not "width" and "height"?
* There is no need to serialize "size", as it can be computed from width and height; so it should be suppressed

or deserialize, because:

* There are no setters to use, just a 2-argument constructor -- it can be used with Jackson 1.2, but needs annotations

### Mix-ins to the rescue!

So, here's one possible mix-in class that can be used to inject ("mix in") annotations we would want:

```java
abstract class MixIn {
  MixIn(@JsonProperty("width") int w, @JsonProperty("height") int h) { }

  // note: could alternatively annotate fields "w" and "h" as well -- if so, would need to @JsonIgnore getters
  @JsonProperty("width") abstract int getW(); // rename property
  @JsonProperty("height") abstract int getH(); // rename property
  @JsonIgnore int getSize(); // we don't need it!
  
}
```

and to configure our {{{ObjectMapper}}} we'd use:

```java
objectMapper.addMixInAnnotations(Rectangle.class, MixIn.class);
```

### Usage notes

Here are some notes on what kinds of annotations can be used, and for what purpose:

* All annotation sets that Jackson recognizes ([[core annotations | JacksonAnnotations]], [[JAXB extensions | JacksonJAXBAnnotations]]) can be mixed in
* All kinds of annotations (member method, static method, field, constructor annotations) can be mixed in
* Only method (and field) name and signature are used for matching annotations: access definitions (private, protected, ...) and method implementations are ignored
    * hint: since method implementations are ignored, it often makes sense to define mix-ins as interfaces or abstract classes
    * hint: if you can, it often makes sense to define mix-in class as a sub-class of target class, and use @Override JDK annotation to ensure  method name and signature match
* Mix-ins work as expected within inheritance hierarchy: it is feasible (and useful) to attach mix-in annotations to super-classes -- if so, mix-in annotations can further be overridden by annotations sub-classes (of target) provide.

### External Documentation

Here is some related documentation:

* [Jackson 1.2: use Mix-In Annotations to reuse, decouple](http://www.cowtowncoder.com/blog/archives/2009/08/entry_305.html)
