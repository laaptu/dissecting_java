#### What is machine code ?
* It is language i.e. understood by machine or the CPU.

#### What is high level language ?
* It is the language in which we write code. Meaning 

```
int i =10
int j = 20
int c = i+j
```
Simply looking at this we can easily understand what is going on. So these type of language is known as high level language.

#### Does machine or CPU understand that ?
* No

#### So we need some software to convert it to machine code ?
* Yes and it is known as compiler. Compiler converts high level language to machine code. But one needs to understand that compiler not always necessarily convert high level to machine code. There are different types of compilers designed for different purpose. Some convert code from high level language to other high level language, some convert from low level to high level. So as per the way compiler is designed it performs the necessary task. At core compiler converts one language to other language.

As taken from this from this link [http://softwareengineering.stackexchange.com/questions/300593/does-an-interpreter-produce-machine-code](http://softwareengineering.stackexchange.com/questions/300593/does-an-interpreter-produce-machine-code)

```
A compiler can compile from a high-level language to another high-level language (e.g. GWT, which compiles Java to ECMAScript), 
from a high-level language to a low-level language (e.g. Gambit, which compiles Scheme to C), 
from a high-level language to machine code (e.g. GCJ, which compiles Java to native code),
from a low-level language to a high-level language (e.g. Clue, which compiles C to Java, Lua, Perl, ECMAScript and Common Lisp), 
from a low-level language to another low-level language (e.g. the Android SDK, which compiles JVML bytecode to Dalvik bytecode), 
from a low-level language to machine code (e.g. the C1X compiler which is part of HotSpot, which compiles JVML bytecode to machine code), machine code to a high-level language (any so-called "decompiler", 
also Emscripten, which compiles LLVM machine code to ECMAScript), machine code to low-level language (e.g. the JIT compiler in JPC, which compiles x86 native code to JVML bytecode) and native code to native code (e.g. the JIT compiler in PearPC, which compiles PowerPC native code to x86 native code).
```

#### What is assembly language?
 * Each machine or CPU has instruction set. What is instruction set? It simply means what instructions can be given to that machine. Say there is a machine A which understands 

 ```
 8990 = Store some value
 8110 = Fetch some value
 82230 = Add some value
 ```
    So if there are millions of such instructions like this and if we have to write a program in it, then it will be tedious for us. That's why High level language came into existence. Then what is assembly language. It is a form of low level language  that is not a machine code. The assembly language may be
    
    ```
    str = store some value
    fch = fetch some value
    ad = add some value
    ```
     
![assembly](https://github.com/laaptu/dissecting_java/blob/master/notes/pics/jvm/assembly.png)  
   It is still not so readable in comparison to high level languages.
   
  Q: Why assembly language is used and it's importance? Need to find out.
  
   And there is another software called assembler which converts assembly language to machine code.
![assembly_to_machine](https://github.com/laaptu/dissecting_java/blob/master/notes/pics/jvm/assembly_to_machine_code.png)
   
    Q: Is assembler a type of compiler then? 
   
#### What is interpreter?
* Compiler reads overall code and outputs to other format. Interpreter simply reads a single line and executes it. 

Q: Couldn't understand it properly. Need to find out 

Here are some info from this link [http://softwareengineering.stackexchange.com/questions/300593/does-an-interpreter-produce-machine-code](http://softwareengineering.stackexchange.com/questions/300593/does-an-interpreter-produce-machine-code)

```
The two basic mechanisms for processing a program are compilation and interpretation.

Compilation takes as input a source program in a given language and outputs a target program in a target language.

source program --> | compiler | --> target program
If the target language is machine code, it can be executed directly on some processor:

input --> | target program | --> output
Compilation involves scanning and translating the entire input program (or module) and does not involve executing it.

Interpretation takes as input the source program and its input, and produces the source program's output

source program, input --> | interpreter | --> output
Interpretation usually involves processing (analyzing and executing) the program one statement at a time.

In practice, many language processors use a mix of the two approaches. E.g., Java programs are first translated (compiled) into an intermediate program (byte code):

source program --> | translator | --> intermediate program
the output of this step is then executed (interpreted) by a virtual machine:

intermediate program + input --> | virtual machine | --> output
To complicate things even further, the JVM can perform just-in-time compilation at runtime to convert byte code into another format, which is then executed.

Also, even when you compile to machine language, there is an interpreter running your binary file which is implemented by the underlying processor. Therefore, even in this case you are using a hybrid of compilation + interpretation.

So, real systems use a mix of the two so it is difficult to say whether a given language processor is a compiler or an interpreter, because it will probably use both mechanisms at different stages of its processing. In this case it would probably more appropriate to use another, more neutral term.

Nevertheless, compilation and interpretation are two distinct kinds of processing, as described in the diagrams above,

To answer the initial questions.

A compiler would create machine language which runs on the physical hardware directly?
Not necessarily, a compiler translates a program written for a machine M1 to an equivalent program written for a machine M2. The target machine can be implemented in hardware or be a virtual machine. Conceptually there is no difference. The important point is that a compiler looks at a piece of code and translates it to another language without executing it.

So an interpreter doesn't produce machine language but a compiler does it for its input?
If by producing you are referring to the output, then a compiler produces a target program which may be in machine language, an interpreter does not.
```

#### More infos

* Nowadays compilers are mix of compiler and interpreters. So both the mechanism is used nowadays.
* In C language the compiler converts the high level lanuage to machine code directly ( say like *.exe) to be executed directly in the machine.
   ![compile for c ](https://github.com/laaptu/dissecting_java/blob/master/notes/pics/jvm/compile_for_c.png)

* In Java language, the compiler converts language to bytecode which is understandable by JVM and JVM later converts it to the needed machine code
   ![compile for java](https://github.com/laaptu/dissecting_java/blob/master/notes/pics/jvm/compile_for_java.png)

#### Some resources

1. Youtube video from android authority about assembler and compiler. Short video with basic concepts [https://www.youtube.com/watch?v=wA2oMRmbrfo](https://www.youtube.com/watch?v=wA2oMRmbrfo)
2. Does an interpreted produce machine code [http://softwareengineering.stackexchange.com/questions/300593/does-an-interpreter-produce-machine-code](http://softwareengineering.stackexchange.com/questions/300593/does-an-interpreter-produce-machine-code)
3. Some assembly language tutorial to get started [https://www.recurse.com/blog/7-understanding-c-by-learning-assembly](https://www.recurse.com/blog/7-understanding-c-by-learning-assembly)
4. Question about does Java code convert to assembly? The answer it says that it directly converts to machine code to speed up the process [https://coderanch.com/t/559258/java/java-codes-converted-assembly-JVM](https://coderanch.com/t/559258/java/java-codes-converted-assembly-JVM)
5. 
   

