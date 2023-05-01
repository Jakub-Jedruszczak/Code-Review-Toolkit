# Best practices and security on how to make a weather API  


## Common attacks against web API’s 

Injection attacks happen when someone is inputting a dangerous piece of code or commands into a program when normal code will be to make it look hidden such as the username or password section. An SQL injection is an example of an attack such as this  

Distributed denial of service attacks are also common as they make a network system or a website unavailable for the user to use. Increasing traffic for that website when it can not handle it can make the website crash or become slow. API endpoints are the most targeted for DDOS attacks. 

Man-in-the-middle attacks happen when a hacker intercepts traffic from a website or application between two communicating systems and impersonates each other acting like a proxy that the user will not be able to notice. API”s man in the middle attacks happen between a client which is the application and the API or between the API and its endpoint.  

Credential stuffing happens when stolen personal information is taken using API endpoints to gain unauthorised access. 

Cross-site scripting or XSS is an injection attack that happens to APIs when a vulnerability enables an attacker put a dangerous script of code into the code of a web application or webpage affecting the API in a way where it will not work anymore or act differently against the user. 

## Mitigation 

To mitigate an injection you can validate and sanitize all of the data that can be found within a API request. Limiting a response will decrease the chance for the data to accidentally be leaked 

Distributed denial of service can be mitigated by using rate limiting and limit the payload size. Rate limiting is a security measure that can limit the number of requests so that It can be sent to a server of an API within a certain Time period. This will then help prevent DDOS attacks and other malicious activity by limiting the amount of traffic that can be sent t a server at once  

Man-in-the-middle attacks can be stopped by encrypting traffic in transit. This means the data traveled between two points must be protected such as a user's computer and a website.  

Cross-site scripting or XSS can be mitigated by tutting invalid inputs and using character escaping and filtering. 

Credential stuffing can be stopped by using an intelligence feed to identify credential stuffing and apply rate limits sos it can minimise brute force attacks.  


## Best practices for securing an API  

1)Making sure that securing an API comes first.

2) Inventory and manage your API’s.

3) Using a strong authentication and authorisation solution is important.

4) Practice the principle of least privilege. This is important as it holds the users, processes, programs, systems, and devices.  

5) Encrypting traffic using TLS which is a form of encryption. 

6) Remove information that’s not meant to be shared.

7) Don’t expose more data than necessary.

8) Validate input.

9) Use rate limiting.

10) Use a web application firewall.

 

 