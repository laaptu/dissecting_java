##### Step by Step

* First compile the java class using `javac `
* Then `*.class` file which is our bytecode. We need to analyze it. 
![java bytecode](https://github.com/laaptu/dissecting_java/blob/master/notes/pics/java_compile.png)

#### Step 1 using javap
![javap](https://github.com/laaptu/dissecting_java/blob/master/notes/pics/javap.png)

What it basically does is analyzes the *.class file and prints the rough class structure ( public static, protected methods and constructor). If there is no constructor at default, in the bytecode a default constructor is added.

````
public class Basic {
	public static void main(String[] args) {
		System.out.println("Hello JVM");
	}
}
````

For this Basic.class compiled file the output will be 
![basic constructor ](https://github.com/laaptu/dissecting_java/blob/master/notes/pics/basic_constructor.png)

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
![with constructor ](https://github.com/laaptu/dissecting_java/blob/master/notes/pics/with_constructor.png)

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
![only few methods ](https://github.com/laaptu/dissecting_java/blob/master/notes/pics/only_few_methods.png)


#### Let's keep it simple for now
````
public class Basic {
	public static void main(String[] args) {
		System.out.println("Hello JVM");
	}
}
````
![hello world](https://github.com/laaptu/dissecting_java/blob/master/notes/pics/hello_world.png)

Now to see the actual code or bytecode, we pass a flag -c to javap as `javap -c `
