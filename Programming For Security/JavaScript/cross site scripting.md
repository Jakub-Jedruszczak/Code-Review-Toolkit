# Cross Site Scripting (XSS)
## What is XSS?
Cross Site Scripting (also known as XSS) is a type of script injection where an attacker enters malicious code into input fields, variables; flaws that allow these attacks to succeed are quite widespread and occur anywhere a web application uses input from a user without sanitising or validating it.
There are three main categories of Cross Site Scripting.
**Reflected XSS** occurs when an attacker socially engineers (tricks) a victim to click on a malicious link or enter a specially crafted payload into a form. When the request is posted, the website processes the request, and the output is sent back to the user’s browser.
**Stored XSS** occurs when a XSS payload is stored in the website’s database, such as a comment on a blog post or message on a messaging application. Stored XSS is particularly dangerous as the payload is executed whenever a user retrieves the data.
**DOM XSS**, also known as Client Side XSS, is a rarer subtype of XSS which occurs when an attacker modifies the HTML response from a server to make the code behave in an unexpected manner.
# How to solve XSS vulnerabilities
## Reflected & Stored XSS
The best way to find flaws is to perform a security review of the code and search for all places where input from an HTTP request could possibly make its way into the HTML output. All user input should be validated as for XSS attacks to be successful, an attacker needs to insert and execute malicious content in a webpage. 
### HTML Context
A HTML Context refers to inserting a variable into a pair of HTML tags instead of a hardcoded value, as shown below.
``` html
<div> $variable </div>
```
An attacker could modify data that is rendered as `$variable`. This could lead to a malicious payload being added to a webpage, such as:

``` html
<div> <script>alert(1)</script> </div>

```
In order to add a variable to a HTML context safely, use HTML entity encoding for that variable as you add it to a web template.
In JavaScript, the `.textContent` attribute is the safe attribute to process as JavaScript will automatically HTML Entity Encode the content of the variable into non-special characters, rendering many payloads ineffective.
### HTML Attribute Context
HTML Attribute Contexts are similar to HTML Contexts, where they contain variables within a HTML object’s attributes.

``` html
<div attr="$variable">

```
Using double or single quotes is important to mitigating the risk of XSS as it forces the variable into a string, making it difficult for attackers to change the context of the input into an executable JavaScript payload.
Using `.setAttribute` for passing data to attributes also automatically HTML Attribute Encodes, given that the attribute is a hardcoded type such as id and class.
### URL Context
URL Contexts are parameters inserted into the URL, usually preceded by a ? symbol. An attacker could enter a malicious payload using the GET protocol to execute JavaScript on the server.

``` html
<a href="http://www.example.com?data=$variable">link</a >

```
Encode all characters with the `%HH` encoding format; make sure any attributes are fully quoted, same as JS and CSS.
There will be situations where you use the same URL in different contexts. In these scenarios, you should do URL encoding followed by HTML attribute encoding.

``` html
url = "[https://example?data=](https://example/?data=)" + urlencode(parameter)
<a href='attributeEncode(url)'>link</a>

```
If you're using JavaScript to construct a URL Query Value, look into using `window.encodeURIComponent(x)`. This will automatically URL encode data in it.
There are many HTML attributes which are often described as “safe sinks”. This means that they will always treat their input as a text or string, making them very hard to use them to exploit. The safe HTML attributes to use in your code are: `align`, `alink`, `alt`, `bgcolor`, `border`, `cellpadding`, `cellspacing`, `class`, `color`, `cols`, `colspan`, `coords`, `dir`, `face`, `height`, `hspace`, `ismap`, `lang`, `marginheight`, `marginwidth`, `multiple`, `nohref`, `noresize`, `noshade`, `nowrap`, `ref`, `rel`, `rev`, `rows`, `rowspan`, `scrolling`, `shape`, `span`, `summary`, `tabindex`, `title`, `usemap`, `valign`, `value`, `vlink`, `vspace`, `width`.
## DOM XSS
Document Object Model (DOM) XSS is an attack where a payload is injected into the application during runtime in the client directly, bypassing most server-side controls entirely by processing the payload as JavaScript on the victim’s machine. All this code originates on the server, which means it is the application owner's responsibility to make it safe from XSS, regardless of the type of XSS flaw it is.
In JavaScript code, the main context is JavaScript but with the right tags and context closing characters, an attacker can try to attack the HTML, HTML attribute, CSS and URL contexts using equivalent JavaScript DOM methods.
Below is an example vulnerability which occurs in the JavaScript and HTML contexts:

```javascript
<script>
variable x = '<%= variable %>';
variable d = document.createElement('div');
d.innerHTML = x;
document.body.appendChild(d);
 </script>

```
Dynamic HTML updates, as shown below, may lead to a DOM XSS vulnerability if the untrusted input is not  HTML or JavaScript encoded.

```javascript
element.innerHTML = "HTML data";
document.write("HTML data");

```
To securely parse dynamic HTML updates in the JavaScript execution subcontext, we recommend using Enterprise Security API (ESAPI), an open-source security library provided by OWASP.

```javascript
var ESAPI = require('node-esapi'); 
element.innerHTML = "<%=ESAPI.encoder().encodeForJavascript(ESAPI.encoder().encodeForHTML(data))%>";
document.write("<%=ESAPI.encoder().encodeForJavascript(ESAPI.encoder().encodeForHTML(data))%>");
```