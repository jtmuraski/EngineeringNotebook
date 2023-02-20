- Java application are built using the Java Development Kit (JDK), which can be obtained from either an Open Source (OpenJDK) or direct from Oracle
- Users running a Java application requite the Java Runtime Environment (JRE) installed on the machine to run the application
	- This is because Java applications are NOT native applications, so they require the JDK to proivde the necessary resources to run and provide the Java environment
- When running a Java application from the command line, you need to launch the Java environment:
```
C:ProgramFiles\JavaApp\FileLocation> java Main
```
---
#### Java Code Basics
- Statements are ended with a ';' (like C#).
- Parts of statements are seperated by zero or more white spaces in Java. So whitespaces do not matter.
	- This statement:
	```
	System.out.println( "Hello"     )    ;
	```
	- Is the same as this one:
	  ```
	  System.out.printlin("Hello");
	  ```
  - Whitespace does not control the behavior of the statement.
  - Java supports 3 types of comments
	  - Line Comment  //......
	  - Block Comment  /* ....*/
	  - Javadoc comment /** ... */
- Packages
	- Packages provide organization of code
	- Follow standard naming convention
	- Affect the source code structure
	- package names are written in all lowercases
	- packages use reverse name notation to assure global uniqueness
	- Add further qualifier to assure uniqueness within a company or group
	- the name of packages should match the folder structure of the code
	- ![[Pasted image 20230217235224.png]]
- Variables
	- Java is strongly typed language
	- Can use the 'final' keyword when declaring a variables. This locks the variable data once set
	- There are 4 primitive data types:
		- Integer
		- ![[Pasted image 20230219224232.png]]
		- Floating point
		- ![[Pasted image 20230219224356.png]]
		- Character
			- Stores a single Unicode character
			- Can use unicode points to assign a value that is not on your keyboard. This is done my starting a character with a \u before the 4-digit hex value, enclosed in single brackets. 
			- Example: '\u00DA'
		- Boolean
			- true/false value
- Prefix and Postfic Operators
	- ++ increases a var by 1
	- -- subtracts 1 from a var
	- These can be placed either before or after the variable name
 ```
 int somevalue = 5;
 System.out.println(++somevalue);
 // Outputs 6
 System.out.println(somevalue);
 // Outputs 6

 int someOtherValue - 5;
 System.out.println(someOtherValue++);
 // Outputs 5
 System.out.println(someOtherValue);
 // OUtputs 6
```
		- THe order in which the operators are added matter. If the ++ is a prefix, it returns the value after the operator is applied. If on the right, it outputs the orignal value, and then adds the 1.
- Operaotr Precedence
- ![[Pasted image 20230219225438.png]]
	- Note, anything in parantheses takes precendence
- Logical Operators
	![[Pasted image 20230219232029.png]]
	![[Pasted image 20230219232230.png]]
	