# HCL

HCL (HashiCorp Configuration Language) is a configuration language built
by HashiCorp. The goal of HCL is to build a structured configuration language
that is both human and machine friendly for use with command-line tools, but
specifically targeted towards DevOps tools, servers, etc.

HCL is heavily inspired by
[libucl](https://github.com/vstakhov/libucl),
nginx configuration, and others similar.

## Syntax

The complete grammar
[can be found here](https://github.com/hashicorp/hcl/blob/master/parse.y),
if you're more comfortable reading specifics, but a high-level overview
of the syntax and grammar are listed here.

  * Single line comments start with `#` or `//`

  * Multi-line comments are wrapped in `/*` and `*/`

  * Values are assigned with the syntax `key = value` (whitespace doesn't
    matter). The value can be any primitive: a string, number, boolean,
    object, or list.

  * Strings are double-quoted and can continue any UTF-8 characters.
    Example: `"Hello, World"`

  * Numbers are assumed to be base 10. If you prefix a number with 0x,
    it is treated as a hexadecimal. If it is prefixed with 0, it is
    treated as an octal.

  * Boolean values: `true`, `false`, `on`, `off`, `yes`, `no`.

  * Arrays can be made by wrapping it in `[]`. Example:
    `["foo", "bar", 42]`.

  * Objects (also known as maps) can be made with '{}'. Example:
    '{ foo = "bar" }'

In addition to these basics, the syntax supports hierarchies of
sections. These sections are actually syntactic sugar over lists of
maps, but visually end up looking much better from a configuration
standpoint. For example, these are nearly equivalent:

```
variable "ami" {
    description = "the AMI to use"
}

# is equal to:

variable = [{
    "ami": {
        "description": "the AMI to use",
    }
}]
```
