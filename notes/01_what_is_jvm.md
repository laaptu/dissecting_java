#### First thing first

* What is needed to run a Java program?
* A compiler and a JVM (Java Virtual Machine)
* Where can it be found? An Oracle or Open JDK has JDK (Java Development Kit) where it comes bundle with all those. Download it and install it. In my mac, it gets installed in following location and all those bin files is what needed for it to compile and run the Java program
![bin_location](https://github.com/laaptu/dissecting_java/blob/master/notes/pics/jdk_bin.png)

#### What is virtual machine

In a computer we have hardware and the most needed ones are CPU,RAM and hard disk. So, whatever program we write, it must be run by CPU and RAM. So, eventually the program we have written must be converted down to the instructions that is understood by CPU. To access or work with the hardware, we need Operating System because all those are managed by OS and we need its help to communicate with them.

There are different OS, different CPU architecture. So to make our code written in High level language to run or use the machines, we need to make it compatible to all OS and different CPU architecture. If you have to both write the code in your given high level programming language and then make necessary arrangements to make it compatible to machine code for different OS and CPU architecture, then your work becomes tedious and time consuming.

High level language are those language that is not machine understood directly. Like Java, where we write programs. The programs written in Java is not directly understood by CPU and stuff. It requires machine codes, some assembly level format. 

So, now the virtual machine comes into action. Virtual machine acts as a virtual computer. It acts as though, it is running our program i.e. it is executing our program, running it in the CPU and doing stuff. So there are virtual machine developers who make those for different OS and CPUs. Like we downloaded JDK, where it comes bundled with the virtual machine and stuff. So Windows there is different JDK and for Mac OS ,there is different.

#### Q) Where is the virtual machine in the JDK?
So far, whenever I run a Java program, in my activity monitor, I can see a process called Java. That is the actual virtual machine. So is `java` bin a virtual machine. Need to confirm this

Now as an application developer we write the code that is now understood by virtual machine only. As virtual machine will do the necessary job communicating with the actual machine.

As said earlier, the actual machine only understands the assembly language. So the virtaul machine again have to convert the code to assembly language. Further, the virtual machine won't directly understand the Java language, it again needs to be converted into the bytecode which is the language it understands.


java code --> compiler ( javac ) --> byte code ( *.class) --> JVM --> JIT ( Just in time compiler) --> machine code --> CPU

Runtime compilation from byte code --> JVM --> JIT --> machine code
when we do `java compiledclass`

![some fun](https://github.com/laaptu/dissecting_java/blob/master/notes/pics/java_to_assembly.png)

In picture above it should be machine code instead of assembly code.

Some more pictorial representation of JVM

![jvm more](https://github.com/laaptu/dissecting_java/blob/master/notes/pics/jvm_more.png)


##### There are different virtual machines for different CPU's and OS. Each JVM can understand the bytecode easily.




