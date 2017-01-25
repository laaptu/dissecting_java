##### Step by Step

* First compile the java class using `javac `
* Then `*.class` file which is our bytecode. We need to analyze it. 
![java bytecode](https://github.com/laaptu/dissecting_java/blob/master/notes/pics/jvm/java_compile.png)

#### Step 1 using javap
![javap](https://github.com/laaptu/dissecting_java/blob/master/notes/pics/jvm/javap.png)

What it basically does is analyzes the *.class file and prints the rough class structure ( public static, protected methods and constructor). If there is no constructor at default, in the bytecode a default constructor is added.

````
public class Basic {
	public static void main(String[] args) {
		System.out.println("Hello JVM");
	}
}
````

For this Basic.class compiled file the output will be 
![basic constructor ](https://github.com/laaptu/dissecting_java/blob/master/notes/pics/jvm/basic_constructor.png)

So, `jvm.Basic()` is added during compile time.

But if we add our own constructor

````
public class HelloWorld {
	public static void main(String[] args) {
		System.out.println("Hello World");
	}

	public Basic(String message) {

	}
}
````
The output of `javap` will be 
![with constructor ](https://github.com/laaptu/dissecting_java/blob/master/notes/pics/jvm/with_constructor.png)

Finally for this code

````
public class Basic {
	public static void main(String[] args) {
		System.out.println("Hello JVM");
	}
	public Basic(String message) {

	}
	public void showPublic(){
		
	}
	protected void showProtected(){
		
	}
	private void willShowPrivate(){
		
	}
}
````
The output will be
![only few methods ](https://github.com/laaptu/dissecting_java/blob/master/notes/pics/jvm/only_few_methods.png)


#### Let's keep it simple for now
````
public class HelloWorld {
	public static void main(String[] args) {
		System.out.println("Hello World");
	}
	private int count;
	public HelloWorld(int count) {
		this.count = count;
	}
}
````
![hello world](https://github.com/laaptu/dissecting_java/blob/master/notes/pics/jvm/hello_world.png)

Now to see the actual code or bytecode, we pass a flag -c to javap as 

 * javac jvm/HelloWorld.java
 * javap -c jvm.HelloWorld

![javap_with_c](https://github.com/laaptu/dissecting_java/blob/master/notes/pics/jvm/javap_with_c.png)

Let's isolate `main` method for now

![bytecode_main](https://github.com/laaptu/dissecting_java/blob/master/notes/pics/jvm/bytecode_main.png)

![javap_with_c](https://github.com/laaptu/dissecting_java/blob/master/notes/pics/jvm/bytecode_main_detail.png)

#### Understanding the bytecode little

* gets the static method of PrintStream
* loads the string value
* invokes the static method with value
* return

4 codes for 1 line of `System.out.println()`. Awesome

In the next article, let us analyze how JVM eats these codes and does necessary optimization
 
