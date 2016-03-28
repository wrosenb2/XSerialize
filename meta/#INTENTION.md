XSerialize Intention
==========

Fundamentally XSerialize is an attempt to read and write
general data in an XML format, but document definitions to
allow that data to configured as objects or structs.

The following types of data must be supported.

+ text
+ styled text (i.e. m`<sup>`2`</sup>` = m<sup>2</sup>)
    + for extensibility users should define their own styles
    + HTML syntax (and potentially others) should be provided
    internally.
+ arrays
+ numbers
    + enumerations
    + ranges
    + predicates
    + types (i.e. int)
+ binary data
    + input as base 64 or space separated hex pairs
    + must specify
        + line wrapping policy
        + endianness
        + mime type
    + optionally specify
        + encoding
        + source
            + in this case no content need be provided
            + in fact, it should not be allowed to provide both content and a source definition
+ dictionaries
+ booleans
+ null
+ ENTITY's (bindings of tag/attribute value to associate value)
+ objects (collection of the above)

Every tag not associated explicitly with the type of...

+ text
+ styled text
+ array
+ number
+ data
+ boolean
+ null
+ dictionary

will be its own object, whose class definition may be derived from
from the document definition of the XML. From the given types
it should be possible to generate any data structure desireable.