#### Types of Defects
- Functional Errors
	- Behavior varies from the functional requirements
	- Often found during testing
- Security Defects
	- Open software to attacjes
	- Discovered during security and penetration testing
	- Exmples
		- SQL injection
		- Cross site scripting
		- Buffer overflows
	- Don't trust any users input
- Syntax Errors
	- Typo errors
	- Such as a missing "" or ;
- Logic Errors
	- Coding errors that result in the wrong output
- Calculation Errors
	- A type of Logic error
	- incorrectr calculations
- Out-of-Bound bugs
	- Values are outside of an expected range
	- Data type inputted is different than expected
- Compatibility defects
	- Application doens't perform consistently when tried on different hardware, OS's, browsers or platforms
- System-level integration bugs
	- Mistake when two or more subsystems don't interact as intended
- Performance Defects
	- Software doens't perofrm to what is expected or what is acceptable
	- Found during performance testing
	- Areas of Interest include
		- Speed
		- Stability
		- Response Time
		- memory usage
		- Resource usage
- Usability Defects
	- Defects that prevent the software being used to it's fullest cpability
		- Complicated UI
		- Violation of accessbility standards
		- Ambiugous icons or instructions
		-
		

#### Debuggging in Visual Studio
- Can press F5 to start the debugger
- Can Press F10 to start debugging, but run through one line of code at a time, but skip over a method call
- Press F11 to start debugging each line, but step into a method call
- Breakpoints can be set be clicking in the far left column. When the code hits that line of code, the program will stop
- If you accidentally skip thorugh a line, you can grab the yellow arrow on the left hand column and drag it back to back to a different line of code
	- CAUTION: If values changed, they may not revert back to what they were originally
	
##### Conditional Breakpoints
- Breakpoints in VS can be given conditions. For example, if you put a break  point on an foreach loop, you have it stop after X number of iterations
- You can also use Trace Points to log statements at breakpoints as you move through them
##### System.Diagnostics.Debug and Trace Listeners
- This allows you to write messages while the app is in deb mode
- There are several Write methods, including a WriteLineIf that will only write if a conditional is met
- Debug.Write methods are removed from released code, so it only appears in the Dev builds
- Configure the Trace Listener:
	- Can create a ConfigureTraceListeners class
	- ![[Pasted image 20230310112131.png]]
	- ![[Pasted image 20230310112200.png]]
	- 


#### An Effective Approach to Debugging
- Can use the Scientific Method to debug code
|  Scientific Method | Debugging|
|---------------------|-------------|
| Gather data through repeatable experiments | Stabilize the Error|
|Form a hypothesis | Locate the Source of the Errror |
|Design an experiment to prove or disprove the hypothesis | Fix what you believe is the source of the bug |
| Execute the experiment | Run the code and see if the error persists |
|Analyze, refine and repeat as needed | Verify the fix worked, and look for similar mistakes itn the code |

##### Stabilizing the Error
- Consistently get the error to repeat it self
- Narrow the test case => What is causing the error? Input value? Null value? Syntax?
- Change these factors and re-run your tests
- Essentially - isolate the error and verify that it isn't causing issues elsewhere in the code
- Use logs to help pinpoint the source of the errors
- NOTE: Avoid using production data whenever possible. Always use test data unless it is completly unavoidable, and DO NOT copy production data to a dev environment without consulting the data owners and security groups due to the sometimes sensetive nature of data
- 