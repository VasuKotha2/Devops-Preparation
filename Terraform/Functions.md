Terraform functions:
--------------------
* Terraform language includes a number of built-in functions that you can call from within expressions to transform and combine values.

Numeric Functions:
------------------
* abs:
    * abs returns the absolute value of given number. If the number is positive then it will return the number as-is but if it is negative number it multiplies with -1 and return the value.
    Ex: 1. abs(23)
            23
        2. abs(0)
            0
        3. abs(-12.4)
            12.4
* ceil:
    * ceil returns the closest whole number that is greater than or equal to the given value, which may be a fraction.
    Ex: 1. ceil(5)
            5
        2. ceil(5.1)
            6
* floor:
    * floor returns the closest whole number that is less than or equal to the given value, which may be a fraction.
    Ex: 1. floor(5)
            5
        2. floor(4.9)
            4
* log:
    * log returns the logarithm of a given number in a given base.
    * `Syntax: log(number, base)`
    > log(50, 10)
        1.6989700043360185
    > log(16, 2)
        4

    * log and ceil can be used together to find the minimum number of binary digits required to represent a given number of distinct values:
    > ceil(log(15, 2))
        4
    > ceil(log(16, 2))
        4
    > ceil(log(17, 2))
        5
* max:
    * max takes one or more numbers and returns the greatest number from the set.
    > max(12, 54, 3)
        54

    * If the numbers are in a list or set value, use ... to expand the collection to individual arguments:
    > max([12, 54, 3]...)
        54
* min:
    * min takes one or more numbers and returns the smallest number from the set.
    > min(12, 54, 3)
        3

    * If the numbers are in a list or set value, use ... to expand the collection to individual arguments:
    > min([12, 54, 3]...)
        3
* parseint:
    * parseint parses the given string as a representation of an integer in the specified base and returns the resulting number. The base must be between 2 and 62 inclusive.
    > parseint("100", 10)
        100
    > parseint("FF", 16)
        255
    > parseint("-10", 16)
        -16
    > parseint("1011111011101111", 2)
        48879
    > parseint("aA", 62)
        656
    > parseint("12", 2)
        Error: Invalid function argument
        Invalid value for "number" parameter: cannot parse "12" as a base 2 integer.
* pow:
    * pow calculates an exponent, by raising its first argument to the power of the second argument.
    > pow(3, 2)
        9
    > pow(4, 0)
        1
* signum:
    * signum determines the sign of a number, returning a number between -1 and 1 to represent the sign.
    > signum(-13)
        -1
    > signum(0)
        0
    > signum(344)
        1

String Functions:
-----------------
* chomp:
    * chomp removes newline characters at the end of a string.
    * This can be useful if, for example, the string was read from a file that has a newline character at the end.
    > chomp("hello\n")
        hello
    > chomp("hello\r\n")
        hello
    > chomp("hello\n\n")
        hello
* endswith:
    * endswith takes two values: a string to check and a suffix string. The function returns true if the first string ends with that exact suffix.
    * Syntax: endswith(string, suffix)
    > endswith("hello world", "world")
        true
    > endswith("hello world", "hello")
        false
* format:
    * The format function produces a string by formatting a number of other values according to a specification string. It is similar to the printf function in C, and other similar functions in other programming languages.
    * `Syntax: format(spec, values...)`
    * %%	Literal percent sign, consuming no value.
    * %v	Default formatting based on the value type. Accepts all types, including items of null, list, and map types.
    * %#v	JSON serialization of the value, as with jsonencode. Accepts all types, including items of null, list, and map types.
    * %t	Convert to boolean and produce true or false.
    * %b	Convert to integer number and produce binary representation.
    * %d	Convert to integer number and produce decimal representation.
    * %o	Convert to integer number and produce octal representation.
    * %x	Convert to integer number and produce hexadecimal representation with lowercase letters.
    * %X	Like %x, but use uppercase letters.
    * %e	Convert to number and produce scientific notation, like -1.234456e+78.
    * %E	Like %e, but use an uppercase E to introduce the exponent.
    * %f	Convert to number and produce decimal fraction notation with no exponent, like 123.456.
    * %g	Like %e for large exponents or like %f otherwise.
    * %G	Like %E for large exponents or like %f otherwise.
    * %s	Convert to string and insert the string's characters.
    * %q	Convert to string and produce a JSON quoted string representation.
    * Examples:
        > format("Hello, %s!", "Ander")
            Hello, Ander!
        > format("There are %d lights", 4)
            There are 4 lights
        > format("Hello, %s!", var.name)
            Hello, Valentina!
        > "Hello, ${var.name}!"
            Hello, Valentina!
        > format("%#v", "hello")
            "\"hello\""
        > format("%#v", true)
            "true"
        > format("%#v", 1)
            "1"
        > format("%#v", {a = 1})
            "{\"a\":1}"
        > format("%#v", [true])
            "[true]"
        > format("%#v", null)
            "null"
* indent:
    * indent adds a given number of spaces to the beginnings of all but the first line in a given multi-line string.
    * `Syntax: indent(num_spaces, string)`
        > "  items: ${indent(2, "[\n  foo,\n  bar,\n]\n")}"
              items: [
                foo,
                bar,
             ]
    * The first line of the string is not indented so that, as above, it can be placed after an introduction sequence that has already begun the line.
* join:
    * join produces a string by concatenating all of the elements of the specified list of strings with the specified separator.
    * `Syntax: join(separator, list)`
    > join("-", ["foo", "bar", "baz"])
        "foo-bar-baz"
    > join(", ", ["foo", "bar", "baz"])
        foo, bar, baz
    > join(", ", ["foo"])
        foo 
* lower:
    * lower converts all cased letters in the given string to lowercase.
    > lower("HELLO")
        hello
    > lower ("АЛЛО!")
        алло!
* regex:
    * regex applies a regular expression to a string and returns the matching substrings.
    * `Syntax: regex(pattern, string)`
    * The return type of regex depends on the capture groups, if any, in the pattern:
        * If the pattern has no capture groups at all, the result is a single string covering the substring matched by the pattern as a whole.
* regexall:
* replace: 
    * replace searches a given string for another given substring, and replaces each occurrence with a given replacement string.
    * `Syntax: replace(string, substring, replacement)`
    * If `substring` is wrapped in forward slashes, it is treated as a regular expression, using the same pattern syntax as regex. If using a regular expression for the substring argument, the `replacement` string can incorporate captured strings from the input by using an `$n` sequence, where `n` is the index or name of a capture group.
        > replace("1 + 2 + 3", "+", "-")
            1 - 2 - 3
        > replace("hello world", "/w.*d/", "everybody")
            hello everybody
* split:
    * split produces a list by dividing a given string at all occurrences of a given separator.
    * `Syntax: split(separator, string)`
        > split(",", "foo,bar,baz")
        [
            "foo",
            "bar",
            "baz",
        ]
        > split(",", "foo")
            [
                "foo",
            ]
        > split(",", "")
            [
                "",
            ]
* startswith:
    * startswith takes two values: a string to check and a prefix string. The function returns true if the string begins with that exact prefix.
    * `Syntax: startswith(string, prefix)`
        > startswith("hello world", "hello")
            true
        > startswith("hello world", "world")
            false
* strcontains:
    * strcontains function checks whether a substring is within another string.
    * `Syntax: strcontains(string, substr)`
        > strcontains("hello world", "wor")
            true
        > strcontains("hello world", "wod")
            false
* strrev:
    * strrev reverses the characters in a string.
    * `Syntax: strrev(string)`
    > strrev("hello")
        olleh
    > strrev("a ☃")
        ☃ a
* substr:
    * substr extracts a substring from a given string by offset and (maximum) length.
    * `Syntax: substr(string, offset, length)`
    > substr("hello world", 1, 4)
        ello
    * The offset and length are both counted in unicode characters rather than bytes:
    > substr("🤔🤷", 0, 1)
        🤔
    * The offset index may be negative, in which case it is relative to the end of the given string. The length may be -1, in which case the remainder of the string after the given offset will be returned.
    > substr("hello world", -5, -1)
        world
    * If the length is greater than the length of the string, the substring will be the length of all remaining characters.
    > substr("hello world", 6, 10)
        world
* title:
    * title converts the first letter of each word in the given string to uppercase.
    > title("hello world")
        Hello World
* trim:
    * trim removes the specified set of characters from the start and end of the given string.
    * `Syntax: trim(string, str_character_set)`
    * Every occurrence of a character in the second argument is removed from the first argument.
    > trim("?!hello?!", "!?")
        "hello"
    > trim("foobar", "far")
        "oob"
    > trim("   hello! world.!  ", "! ")
        "hello! world."
* trimprefix:
    * trimprefix removes the specified prefix from the start of the given string. If the string does not start with the prefix, the string is returned unchanged.
    > trimprefix("helloworld", "hello")
        world
    > trimprefix("helloworld", "cat")
        helloworld
* trimsuffix:
    * trimsuffix removes the specified suffix from the end of the given string.
    > trimsuffix("helloworld", "world")
        hello
* trimspace:
    * trimspace removes any space characters from the start and end of the given string.
    * This function follows the Unicode definition of "space", which includes regular spaces, tabs, newline characters, and various other space-like characters.
    > trimspace("  hello\n\n")
        hello
* upper:
    * upper converts all cased letters in the given string to uppercase.
    > upper("hello")
        HELLO
    > upper("алло!")
        АЛЛО!

Collection Functions:
---------------------
Encoding Functions:
-------------------
Filesystem Functions:
---------------------
Date and Time Functions:
------------------------
Hash and Crypto Functions:
--------------------------
IP Network Functions:
---------------------
* cidrhost:
    * cidrhost calculates a full host IP address for a given host number within a given IP network address prefix.
    * `Syntax: cidrhost(prefix, hostnum)`
    * `prefix` must be given in CIDR notation
    * `hostnum` is a whole number that can be represented as a binary integer with no more than the number of digits remaining in the address after the given prefix. If `hostnum` is negative, the count starts from the end of the range. For example, `cidrhost("10.0.0.0/8", 2)` returns `10.0.0.2` and `cidrhost("10.0.0.0/8", -2)` returns `10.255.255.254`.
    > cidrhost("10.12.112.0/20", 16)
        10.12.112.16
    > cidrhost("10.12.112.0/20", 268)
        10.12.113.12
    > cidrhost("fd00:fd12:3456:7890:00a2::/72", 34)
        fd00:fd12:3456:7890::22
* cidrnetmask: 
    * cidrnetmask converts an IPv4 address prefix given in CIDR notation into a subnet mask address.
    * `Syntax: cidrnetmask(prefix)`
    * `prefix` must be given in IPv4 CIDR notation
    * The result is a subnet address formatted in the conventional dotted-decimal IPv4 address syntax, as expected by some software.
    * CIDR notation is the only valid notation for IPv6 addresses, so `cidrnetmask` produces an error if given an IPv6 address.
    > cidrnetmask("172.16.0.0/12")
        255.240.0.0
* cidrsubnet:
    * cidrsubnet calculates a subnet address within given IP network address prefix.
    * `Syntax: cidrsubnet(prefix, newbits, netnum)`
    * `prefix` must be given in CIDR notation
    * `newbits` is the number of additional bits with which to extend the prefix. For example, if given a prefix ending in /16 and a newbits value of 4, the resulting subnet address will have length /20.
    * `netnum` is a whole number that can be represented as a binary integer with no more than newbits binary digits, which will be used to populate the additional bits added to the prefix.
    * This function accepts both IPv6 and IPv4 prefixes, and the result always uses the same addressing scheme as the given prefix.
    * Unlike the related function cidrsubnets, cidrsubnet allows you to give a specific network number to use. cidrsubnets can allocate multiple network addresses at once, but numbers them automatically starting with zero.
    > cidrsubnet("172.16.0.0/12", 4, 2)
        172.18.0.0/16
    > cidrsubnet("10.1.2.0/24", 4, 15)
        10.1.2.240/28
    > cidrsubnet("fd00:fd12:3456:7890::/56", 16, 162)
        fd00:fd12:3456:7800:a200::/72
* cidrsubnets:
    * cidrsubnets calculates a sequence of consecutive IP address ranges within a particular CIDR prefix.
    * `Syntax: cidrsubnets(prefix, newbits...)`
    * prefix must be given in CIDR notation
    * he remaining arguments, indicated as newbits above, each specify the number of additional network prefix bits for one returned address range. The return value is therefore a list with one element per newbits argument, each a string containing an address range in CIDR notation.
    > cidrsubnets("10.1.0.0/16", 4, 4, 8, 4)
        [
            "10.1.0.0/20",
            "10.1.16.0/20",
            "10.1.32.0/24",
            "10.1.48.0/20",
        ]
    > cidrsubnets("fd00:fd12:3456:7890::/56", 16, 16, 16, 32)
        [
            "fd00:fd12:3456:7800::/72",
            "fd00:fd12:3456:7800:100::/72",
            "fd00:fd12:3456:7800:200::/72",
            "fd00:fd12:3456:7800:300::/88",
        ]
    * You can use nested cidrsubnets calls with for expressions to concisely allocate groups of network address blocks:

    > [for cidr_block in cidrsubnets("10.0.0.0/8", 8, 8, 8, 8) : cidrsubnets(cidr_block, 4, 4)]
        [
            [
                "10.0.0.0/20",
                "10.0.16.0/20",
            ],
            [
                "10.1.0.0/20",
                "10.1.16.0/20",
            ],
            [
                "10.2.0.0/20",
                "10.2.16.0/20",
            ],
            [
                "10.3.0.0/20",
                "10.3.16.0/20",
            ],
        ]








Type Conversion Functions:
--------------------------
