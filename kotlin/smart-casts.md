Code depending on condition based on Type has not to be casted as in Java to desired Type. This is automatic in Kotlin


```kotlin 
interface Expr
class Num(val value: Int) : Expr
class Sum(val left: Expr, val right: Expr) : Expr

fun eval(e: Expr): Int {
    if (e is Num){
        return e.value
    }
    if (e is Sum){
        return eval(e.right) + eval(e.left)
    }   
    throw IllegalArgumentException("No expr")
}

fun main() {
println(eval(Sum(Num(1), Num(2))))
}
```

<https://pl.kotl.in/Dzek9XmCO>