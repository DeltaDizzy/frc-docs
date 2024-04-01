Structured Data
===============

While the normal range of topic types is suffcient for most use cases, teams often need to send data consisting of multiple components over NetworkTables. Multiple topics can be used, but then naming, boilerplate, and timestamp sync become problems. Protobuf and Struct topics allow teams to send certain data types over NetworkTables just like any primtive type.

How to use
----------

Protobuf vs Struct
------------------

Adding your own Struct support
------------------------------

Adding support for StructTopic to a type that does not already have it is simple. 

1. Create a new class that extends ``Struct<T>`` (Java) or ``wpi::Struct<T>`` (C++), where ``T`` is the class you are adding support to.
2. Implement the ``getTypeString()``, ``getSize()``, ``getSchema()``, ``unpack()``, ``pack()`` (Java and C++), and ``getTypeClass()`` (Java only) methods.
3. In the base class, add a static object of the struct type you have just created.

Your class now has full NT4 struct support!

Adding your own protobuf support
--------------------------------

While in many ways similar to adding Struct support, Protobuf is more complex. 

1. Write the Message specification file. For documentation on the message format, see `the Protobuf documentation <https://protobuf.dev/programming-guides/proto3/>__` and `WPILib proto defintions <https://github.com/wpilibsuite/allwpilib/tree/main/wpimath/src/main/proto>__`.

2. Install the Protobuf Compiler and (if using Java) the QuickBuffers plugin

3. Run `this script <https://github.com/wpilibsuite/allwpilib/blob/main/wpimath/generate_quickbuf.py>__` to generate source files if.

4. 