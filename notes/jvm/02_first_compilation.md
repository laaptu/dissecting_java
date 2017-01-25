#### Let's compile our first Java program

* JDK needs to be installed
* And path must be set i.e. when I type java in the command line, I can see the needed output
![java version](https://github.com/laaptu/dissecting_java/blob/master/notes/pics/jvm/java_version.png)

Our first program under package `jvm`

```
package jvm;
public class Basic {
	public static void main(String[] args) {
			System.out.println("Hello JVM");
	}
}
```

Let's first compile the program i.e *.java -> *.class or converting from java to bytecode. This *.class is now understood by the JVM

* To compile we need `javac` command which will run the java compiler
* `javac filename.java`
* It will produce `filname.class` which is the bytecode format and which is understood by our JVM

![java compile](https://github.com/laaptu/dissecting_java/blob/master/notes/pics/jvm/java_compile.png)

* Now we can execute or run our program into our machine using `java` command which will run the JVM and execute our code

![java run](https://github.com/laaptu/dissecting_java/blob/master/notes/pics/jvm/java_run.png)

Here `java jvm.Basic` is actually executing `Basic.class` not `Basic.java`


![java class execute](https://github.com/laaptu/dissecting_java/blob/master/notes/pics/jvm/java_class_execute.png)

Let us modify our program to run infinitely so we can see what runs in our computer when we do `java`

```
package jvm;
public class Basic {
	public static void main(String[] args) {
		while(true)
	     System.out.println("Hello JVM");
	}
}
```

* `javac jvm/Basic.java`
* `java jvm.Basic`
* And in our system monitor we are seeing the `java` process which is our JVM


![java process](https://github.com/laaptu/dissecting_java/blob/master/notes/pics/jvm/java_process.png)

