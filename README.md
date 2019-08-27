
# The magical "right-associative" colons

## Right associative colons

Right-associative colons works with operator overloading only

It flips the way we call our methods using it as an infix operator

Let’s take our famous example, given:


```scala
class Foo(x:Int) {
   def bar(y:Int) = x + y
}
```




    defined class Foo
    



Let’s rename it with a right-associative colon


```scala
class Foo(x:Int) {
   def ~:(y:Int) = x + y
}
```




    defined class Foo
    



Invoking the right associative colon
Now how do invoke the right associative colon given the following?


```scala
class Foo(x:Int) {
   def ~:(y:Int) = x + y
}
```




    defined class Foo
    



We can call it just like any method and it will return 50:


```scala
val foo = new Foo(10)
foo.~:(10)
```




    foo: Foo = Foo@7bea7d
    res55: Int = 20
    



Or we can call it as an infix operator and get a compiler error:


```scala
val foo = new Foo(10)
foo ~: 10 //Compiler error: value ~: is not a member of Int
```


    <console>:30: error: value ~: is not a member of Int

           foo ~: 10 //Compiler error: value ~: is not a member of Int

               ^

    


To still use it as an infix operator let’s flip it!


```scala
val foo = new Foo(10)
10 ~: foo
```




    foo: Foo = Foo@154a073b
    res57: Int = 20
    



**Mind trick!** The "col"on always attaches to the "col"lection or the object, we will see with a list

## **Lab:** Creating and Manipulating a List

Although we may not use it too much, it will still show up so where do you see it? 
We see it in alternate construction for a `List`

**Step 1:** We will start off with `Nil` which is an empty `List`


```scala
Nil
```




    res59: scala.collection.immutable.Nil.type = List()
    



**Step 2:** Use the `::` operator of the list to create a list of `"Bar"`, `"Baz"`, `"Qux"` off of a `Nil`. Notice that the `::` operator ends in a colon. Assign it to a `val` called `metasyntactics`

**Step 3:** Append an element called `Quuz` to the `metasyntactics` variable using the `:+` method

**Step 4:** Prepend the element `Foo` to `metasyntactics` list using the `:+` method

**Step 5:** Combine all the techniques above to make the list of `Foo`, `Bar`, `Baz`, `Qux`, `Quuz`.

## Magic Right Associative Colons Conclusion
* Right associative colons, will flip how it is invoked
* Not often used but there will moments where you will need it
* It is used to flexibly do things to the language
