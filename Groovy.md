## groovy (http://groovy-lang.org/semantics.html)
##### 1，def：可以简单理解为Object，但它不等同于Object。例如，def str = "abc"，它可以自动识别str为String类型。
##### 2，switch / case：groovy的switch是向后兼容Java的，groovy可以支持任意类型的case匹配。
~~~java
def x = 1.23
def result = ""

switch ( x ) {
    case "foo":
        result = "found foo"
        // lets fall through

    case "bar":
        result += "bar"

    case [4, 5, 6, 'inList']:
        result = "list"
        break

    case 12..30:
        result = "range"
        break

    case Integer:
        result = "integer"
        break

    case Number:
        result = "number"
        break

    case ~/fo*/: // toString() representation of x matches the pattern?
        result = "foo regex"
        break

    case { it < 0 }: // or { x < 0 }
        result = "negative"
        break

    default:
        result = "default"
}
~~~
