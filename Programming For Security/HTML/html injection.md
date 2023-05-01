# HTML injection  

HTML injection is a type of injection vulnerability that can be used to impersonate a user or modify the page content seen by the victims of the attack.  

When a user's inputs are not correctly sanitized and the output is not encoded, a malicious HTML page can be sent to a victim. Sanitizing a user’s input can mean deleting, replacing, and encoding characters which is where the vulnerability can be mitigated hence why if this is not done properly it can make the user interface more susceptible to attacks.  

### Example 1  

There are different ways in which you can display html content which is why if you put an un-sanitized input there will be a high chance of there being a HTML injection imputed within a HTML page. An example of this would be injecting a harmful HTML code by using the innerHTML  JavaScript method. The purpose of this method is to render user-inserted HTML code. If the strings are not checked by using a sanitation method, then this will trigger a HTML injection. There is also a JavaScript function that can be used for a purpose just like this and that is `document.write()`. 

```css
var userposition = location.href.indexOf("user");
var user = location.href.substring(userposition + 5);
document.getElementById("Welcome").innerHTML = "Hello, " + user;
```
This example demonstrates an un-sanitized code that will allow an unvalidated input to be used to create dynamic HTML with the page context. 
 ```css
var userposition = location.href.indexOf("user");
var user = location.href.substring(userposition + 5);
document.write("<h1>Hello, " + user + "</h1>");
```

These 3 lines of code are vulnerable, and they show using the `document.write()` function.

`http://vulnerable.site/page.html?user=<img%20src='aaa'%20onerror=alert(1)>`

Both examples can be exploited by inserting a website page link with this input. By inserting this it will add an image tag to the home page which will make a random JavaScript code that will be placed within HTML content.  

```javascript
<script src = "../js/jquery-1.7.1.js"></script>
<script>
function setMessage(){
    var t = location.hash.slice(1);
    $("div[id = " + t + "]").text("The DOM is now loaded and can be manipulated.");
}
$(document).ready(setMessage);
$(window).bind("hashchange", setMessage);
</script>
<body>
    <script src  = "../js/embed.js"></script>
    <span><a href = "#message1" > show here </a><div id = message1> showing message 1</div></span>
    <span><a href = "#message2" > show here </a><div id = message2> showing message 2</div></span>
    <span><a href = "#message3" > show here </a><div id = message3> showing message 3</div></span>
```

This is an example of proof that you can inject HTML code and by inserting it can allow DOM-based XSS attacks.