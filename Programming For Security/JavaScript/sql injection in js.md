# SQL injection in JS

JavaScript vulnerabilities are exploited by hackers to make the security of websites and web applications more vulnerable for example clickjacking is when a hacker hides an element on top of a website and or web application's user interface to cause a user to perform actions that are not supposed to happen.  

SQL injection on Node.JS can have major consequences as it can allow an attacker to gain unauthorized access to sensitive information or even modify and or delete data from a database. Node.JS does not have any built-in protection against SQL injection attacks which is why performing an SQL injection on Node.js will be easy for hackers; although if the developer has implemented sanitated techniques and a correct input validation this will make it a challenge for hackers to perform an SQL injection. Sanitation queries and using a web application firewall can further help protect against SQL injection attacks.  

The process of an SQL injection is when happens bits of dangerous SQL are inserted into your database queries. This mainly happens when a user passes an input to a database query without any validation which will then unintentionally change the original query. When SQL is injected it can allow a hacker to read restricted information, change the information and delete information. 

## How to prevent SQL injection attacks in Node.js  

When a website is run which has used a programming language that runs interactive features it is important to keep that programming language protected as it can easily be vulnerable to attack due to syntax errors, and user inputs which have no security embedded which can lead to data being stolen and or can be prone to virus attacks.  

  


javascript has error monitoring which can stop many security issues that you may face. This can help catch runtime errors you might find on the system using a try-catch-finally block system which is similar to other languages like Java or C#.

 

 

 

For example this example code:

```javascript
Try  
{ 
    //code that may throw an error  
} 
Catch(ex) 
{ 
    // code to be executed if an error occurs 
} 
Finally{ 
    // code to be executed regardless of whether an error occurs or not 
} 
```
_Try = wrap any suspicious code that might have an error in try block_  

_Catch = write code to make it do something so it can catch block when an error happens. The catch block can have parameters that will inform you of the error. generally catch block is used to display and keep a record of the error to display to the user._ 

_Finally = code in the final block will be executed even if there is no error found. The final block can be used to complete any remaking tasks or reset any variables that have been previously set before the error occurred in the try block._  

## SQL injection on Node JS and how to prevent it  

### Using placeholders  

When using placeholders you should never accept any raw input from a user as it can directly have an impact to your query string although you can use placeholders as the malicious SQL will be escaped and treated like a raw string not as a SQL code.
  
```javascript
 const query = 'SELECT * FROM Repository WHERE TAG = ? AND public = 1'
 const [rows] = await connection.query(query, [userQuery])
```
 
When the placeholders are being used the dangerous SQL code is not being run and instead being seen as a search query.

 ```javascript
SELECT * FROM Repository WHERE TAG = 'javascript';--' AND public = 1;
 ```

### Input Validation  

```javascript
app.get('/repositories/:userQuery', async (req, res) => {
    const {userQuery} = req.params;
    const onlyLettersPattern = /^[A-Za-Z]+$/;
    if (!userQuery.match(onlyLettersPattern)) {
        return res.status(400).json({err: "No special characters and no numbers, please!"]);
    }
    ...
});
```

In addition to using placeholders, you can also add logic within your applications so it can stop any invalid user input. For example,	querying a public repository by tag for example if you do not have a tag that has special characters or numbers it will just add logic to an application to validate a user’s input so it can match the correct or at. In order for this to happen you need to make a regex pattern so it can match a user's input and if it doesn’t match you can return an error. 

```javascript
app.get('/repositories/:userQuery', async (req, res) => {
    const {id} = req.params;
    if (isNaN{Number(id)}) {
        return res.status(400).json({err: "Numbers only, please!"]);
    }
...
```

This code shows that it will not get to the SQL part unless a valid input is passed. You can use his method with any validation technique that will match the data you have. For example, if a user Whats to query by an `id` property which will be a number you can then throw an error if the input is not valid.  

### Allowlisting  

Allowlisting is a specific type of input validation it is useful when you want to know every possible valid user input. From there, you can easily discard anything else you don’t need.  

 ```javascript
app.get('/repositories/:userQuery', async (req, res) => {
    const {userQuery} = req.params;
    const validTags =["javascript", "html", "css"];
    if (!validTags.includes(userQuery)) {
        return res.status(400).json({err: "Valid tags only, please!"]);
    }
    ...
});
```

This is a good example of allow listing, for example if our repository tags only show three valid tags such as JavaScript HTML, and CSS then you can check whether or not the user input is allowed listed by making a comparison against other known valid inputs.  
