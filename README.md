# ProSharp-design
ProSharp is a objective programing language. It’s inspiret by C#/java/C++.
It can by use to create:
- ultrafast code – using pointers, assembler injection, code generation and expand inlines, processor cache manipulation (on system with that ability)
- low memory systems, but generated code will not be fast
- portable – x86, arm, atmel
- buisness process - allows writing long life process, process that can be serialized and deserialized during execution.

The code is compiled to intermediate form and then compile to native code or interpreted.

# ProSharp assumptions

ProSharp is:
- filozofii of creating code
- language 
- framework containing compiler, IDE, execution environment


# ProSharp filozofii
1) There is no file with the source code. Each code is in the IDE and immediately transforms into a representation of the object code model (DOM). Inside, the entire code is represented as a code tree.
It is possible to export the solution to the file source code and import it from files code, but it is not a recommended method.



# ProSharp language assumptions
1)


# ProSharp Framework
1) access to the system takes place through the executive context.
The execution context includes the object: access to the file system, memory allocation, JIT compilation, exception transfer, hardware context.

The reason for this is that we want to have full control over what is being executet. For example, suppose we want to create a copy of each edit file in the application. The easiest way is to set a new execb contex using our file system access object. (we not create new file system, we create only another layer between file system and application)
The point is that we can change the behavior of the external execution code.
