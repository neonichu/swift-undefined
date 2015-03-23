# undefined for Swift

_Micro frameworks_ are popular now, so I'll go _nano framework_ :-). This is all the code:

```
/**
 * `undefined()` pretends to be able to produce a value of any type `T` which can
 * be very useful whilst writing a program. It happens that you need a value
 * (which can be a function as well) of a certain type but you can't produce it
 * just yet. However, you can always temporarily replace it by `undefined()`.
 *
 * Inspired by Haskell's
 * [undefined](http://hackage.haskell.org/package/base-4.7.0.2/docs/Prelude.html#v:undefined).
 *
 * Invoking `undefined()` will crash your program.
 *
 * Some examples:
 *
 *  - `let x : String = undefined()
 *  - `let f : String -> Int? = undefined("string to optional int function")
 *  - `return undefined() /* in any function */`
 *  - `let x : String = (undefined() as Int -> String)(42)`
 *  - ...
 *
 * What a crash looks like:
 *
 * `fatal error: undefined: main.swift, line 131`
 *
 */
func undefined<T>(_ hint:String="", file:StaticString=__FILE__, line:UWord=__LINE__) -> T {
    let message = hint == "" ? "" : ": \(hint)"
    fatalError("undefined \(T.self)\(message)", file:file, line:line)
}
```

## More information

See my slides about [`undefined()`][fltts-undef] from my [Further Leveraging the Type System][fltts] talk at [Swift Summit 2015][ss15].

[fltts]: https://speakerdeck.com/johannesweiss/further-leveraging-the-type-system
[fltts-undef]: https://speakerdeck.com/johannesweiss/further-leveraging-the-type-system?slide=6
[ss15]: http://www.swiftsummit.com
