# Memory Management in Rust

Big Lessons:

1. Every value is _owned_ by a single varaible at a time
2. Re-assigning the valye to another variavle **moves** the value. The old variable can't be used to access the value anymore

## Ownership

1. Every value is owned by a single variable, struct, vector etc at a time

- Not Entirely accurate. It can be owned by a single variable, argument, struct, vector,etc.

2. Reassigning the value to another variable, passing it to a function, putting it into a vector, etc `moves` the value. The old value can't be used anymore!

## Borrowing

Two options for writing useful code despite the ownership rules

- Manually move values back and forth (not common)
- Use the borrowing system (this is the preferred method in Rust)

  **Rules**

3. You can create many read-only references to a value that exist at the same time'
4. You can't move a value while a ref to the value exists
5. You can make a writeable (mutable) reference to a value _only if_ there are no read-only references currently in use. One mutable reference can exist at a time
6. You can mutate a value through the owner when any ref (mutable or immutable) exists
7. Some types of values are _copied_ instead of moved (numbers, bools, chars, arrays/tuples with copyable elements)

## Lifetimes

8. When a variable goes out of scope, the value owned by it is _dropped_ (cleaned up in memory)
9. Values can't be dropped if there are still active references to it
10. References to a value can't outlive the value they refer to
11. **These rules will dramatically change how you write code**
12. **When in doubt remember that rust wants to minimize unexpected updates to data**

<!-- Wrti -->
