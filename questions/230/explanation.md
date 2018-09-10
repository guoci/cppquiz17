`int var1 : 3;` declares a bit-field, and you can not apply `operator&` to a bit-field. [class.bit]§12.2.4¶3 in the C++ standard:
> The address-of operator & shall not be applied to a bit-field, so there are no pointers to bit-fields.
