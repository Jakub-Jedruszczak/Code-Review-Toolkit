# Why do we need code scanning tools?

Static Application Security Tools (SAST) analyse the code you and your team have written for known vulnerabilities. Also known as code scanning, it works by transforming your code into a queryable format and then looking for vulnerable patterns in it, like sending unsanitised user data to a database call. You can think of static analysis tools as linters for security vulnerabilities.  

Static analysis security testing often tends to happen late in the development cycle, as part of a security review. Moving that testing into the main developer workflow, so that every pull request is analysed with static analysis, is the best way to make security an inbuilt part of the program in the form of an application or an IDE plugin, as opposed to being an afterthought. As Avi Douglen once said, “Security at the expense of usability comes at the expense of security”.

It is important to remember that SAST’s are not a replacement for human review, as they often result in false positives and cannot catch every type of vulnerability.

While SAST’s and other code scanning techniques are a great scalable and reproducible solution, they do come at a cost; it is difficult to automate scans for many specific vulnerabilities such as authentication problems, access control issues, and configuration issues which are not present in the code. They also tend to return false positives which may lead developers to ignore real alerts and use a considerable amount of processing power which may dissuade developers from using them.

## Proactive vs Reactive Security

A reactive security approach is when teams respond to past and present threats. A proactive approach, on the other hand, prevents issues from happening in the first place. After all, it’s much more effective to prevent attacks from happening altogether rather than trying to undo the damage. Of course, there are potential advantages to reactive security—like the rare situation in which a proactive approach in a particular circumstance would be very costly. However, a proactive security approach generally offers a higher degree of control.

Taking a proactive security approach involves empowering your developers. By providing developers with the pre-commit findings and intelligence in their IDE to quickly fix issues themselves, you won’t be reliant on security experts and have to manage the accompanying bottlenecks. By empowering developers to quickly and easily secure their code themselves, you can radically decrease the industry average remediation time of six months to just a few minutes.
