# Code Injection

## What is code injection?

Code injection exploits improper input/output data validation. When untrusted data is handled incorrectly an attacker can use code injection to execute a range of commands and is only limited by the language they’re injecting. This differs from command injection where the attacker is limited by the commands in the system, usually a shell. While both are a serious risk, code injection depending on the language is much less constricting for the attacker and can allow for much more serious exploits. A code injection attack could lead to unauthorised data being accessed or the attacker potentially gains access to the system leading to malware/ loss of availability. 
```java
string userInput = request.getParameter("input");
Runtime.getRuntime().exec("echo " + userInput);
```
This is a basic piece of java code that takes and executes a user's input via HTTP request. This could be used for a search bar or file upload. 

The code example does not however have proper input validation and is therefore vulnerable to attacks:
```java
; rm -rf /
```
This is an example of code that an attacker could inject into the piece of Java code. If injected it would delete all the files on the system starting from the root directory which would have serious effects on the web application, how it runs and its users.

## Input Validation
```java
string userInput = request.getParameter("input");
if (userInput.matches("^[a-zA-Z0-9]+$")) {
    Runtime.getRuntime().exec("echo " + userInput);
} 
else {
    response.sendError(HttpServletResponse.SC_BAD_REQUEST, "Invalid input");
}
```
Using the same example code as before and adding the ‘matches()’ command the user input is validated. The matches() command in this example ensures that the user's input only contains letters and digits preventing code execution. If an attacker attempted to do code execution error 400 (bad request) would be returned. 

## Output Sanitisation
```java
string userInput = request.getParameter("input");
string sanitizedInput = userInput.replaceAll("[^a-zA-Z0-9]", "");
Runtime.getRuntime().exec("echo " + sanitizedInput);
```
Again using the same example of code but now adding output sanitization. It uses the `replaceAll()` command to remove any characters that are not letters or digits again preventing any attackers from attempting code execution.
