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

2) everything is serialized and deserialized.
and everything means everything - data, code and execution

Data serialization is very well used in C #, java and js. The problem is rather to deserialize, but there is no easy way for general transformation / deserialization. In the ProSharp database, the object has the function of easy conversion into serial form and deserialization

Code serialization at a first look strange, useless and even deangerous but can by usefull for example to sent do database 'where expression'. In some case this can by done by 'Serialize.Linq'. Code serialization can by usefull to send execution to another cpu. IMO: Compilation it's kind of serialization.

Execution serialization - this featur usefull in buisness logic and in particular long life process with can by serialized in any time, save to DB and then loaded from dDB and restored. (something like hibernation in Windows, but we hibernete one process)


# ProSharp language assumptions
1) The comments can be compiled into the execution code.
At first, it may seem strange to insert comments into the code, but:
a) Is optional
b) Can be useful in integration and testing. The comment can be displayed on the error console. Thanks to that we have additional information about what is happening in the executed code. It can be used, for example, buissnes process for acceptance loan for a person. Even if the person does not receive a loan, we will get information which has been included in such a decision. 


# ProSharp Framework
1) access to the system takes place through the executive context.
The execution context includes the object: access to the file system, memory allocation, JIT compilation, exception transfer, hardware context.The reason for this is that we want to have full control over what is being executet. For example, suppose we want to create a copy of each edit file in the application. The easiest way is to set a new execb contex using our file system access object. (we not create new file system, we create only another layer between file system and application)
The point is that we can change the behavior of the external execution code.

