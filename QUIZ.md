### How does the DevBoard handle received serial messages? How does this differ from the naïve approach?

The DevBoard handles serial messages by syncing them with interrupts. This way instead of a loop which keeps checking, it only runs when the specific interrupt has happened. This approach is more efficient and responsive.

### What does `detached_callback` do? What would happen if it wasn't used?

detached_callback allows a method to create a new thread in order to run. If it wasn't used, the program and gui would be susceptible to freezing. detached_callback prevents blocking actions and methods that could potentially stall the program.

### What does `LockedSerial` do? Why is it _necessary_?

LockedSerial makes sure that only one serial communication is active at a time, when reading and writing, by locking and unlocking the methods of Serial. It is necessary in order to prevent corrupted data, race conditions, and undefined behavior.
