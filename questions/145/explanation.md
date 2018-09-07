In `f()`, an `E` object is constructed, and `1` is printed. This object is then returned to `main()`, and one could expect the copy constructor to be called, printing `2`.

However, `E()` is a prvalue and as such does not constitute an object just yet by [basic.lval]§6.10¶1 

> A prvalue is an expression whose evaluation initializes an object or a bit-field, or computes the value of the operand of an operator, as specified by the context in which it appears.

A prvalue is evaluated only due to temporary materialization conversion ([conv.rval]§7.4¶1) to an xvalue.

[stmt.return]§9.6.3¶2 says:

> (...) the return statement initializes the glvalue result or prvalue result object of the (explicit or implicit) function call by copy-initialization from the operand.

And copy-initialization for a class-type by [dcl.init]§11.6¶17 goes through:

> If the initializer expression is a prvalue and the cv-unqualified version of the source type is the same class as the class of the destination, the initializer expression is used to initialize the destination object.

Which means that no copy or move constructor is called at all. This implies that the copy and move constructor could very well be deleted, and the code would still compile just fine.

The output is thus `13` because of the constructor followed by the destructor call.
