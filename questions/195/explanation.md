`nullptr_t` (the type of `nullptr`) is not actually a pointer type. Instead, `nullptr` is a "null pointer constant" which can be *converted* to a pointer.

[lex.nullptr]§5.13.7¶1 in the C++ standard:

"The pointer literal is the keyword `nullptr`. It is a prvalue of type `std::nullptr_t`."

This implies that it is not a pointer.
