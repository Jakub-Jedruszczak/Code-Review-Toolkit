# GitHub Advanced Security (GHAS)
GitHub Advanced Security (GHAS) is a GitHub-based security service which provides code scanning, secret scanning, and dependency review services. GHAS is free to use on public repositories, but to use this service on a private repository a GitHub Enterprise license is needed.
See more at <https://github.com/features/security>
### Security policy
Make it easy for your users to confidentially report security vulnerabilities they've found in your repository.
### Dependabot security updates
The Dependabot GitHub bot automatically scans and alerts code owners as to which of their dependencies contain known vulnerabilities, and automatically creates pull requests to update these dependencies. Dependabot also automatically updates dependencies to the newest, most secure version, regardless of whether they are vulnerable or not. The dependency graph allows you to explore the ecosystems and packages that your repository depends on and the repositories and packages that depend on your repository.
### Secret scanning alerts
GHAS automatically detect leaked secrets across all public repositories. GitHub informs the relevant service provider that the secret may be compromised.
### Code scanning
GHAS uses the CodeQL engine for static code analysis, which is an open source, community driven Static Application Security Testing (SAST) engine. GHAS’s code analysis engine can be replaced with any other SAST engine, however.
CodeQL is built into the GitHub workflow, making it an easy-to-use proactive code analysis tool; CodeQL scans every commit for security vulnerabilities, allowing contributors to secure their code before it is integrated into the production branch.
GHAS and CodeQL have API and webhook integration, meaning that they may be connected to third party software and services.
While many SAST’s suffer from false positives and errors, CodeQL allows users to mark these as inaccurate, which helps to make code analysis more accurate and reduce false positives in the future.
## How to use
GHAS is a part of GitHub Actions. First, navigate to the GitHub Actions page on your repository.

![image](https://user-images.githubusercontent.com/125093474/234810546-ef72dc99-e32a-411a-a49e-f94b81f3da4e.png)

Next, find the Security section and select CodeQL Analysis.
  
![image](https://user-images.githubusercontent.com/125093474/234810578-58fa861b-3d22-4a24-b8c5-2731086ab81a.png)

Enter the languages you want to scan for in the brackets.
  
![image](https://user-images.githubusercontent.com/125093474/234810596-518e4898-ca32-4777-a877-60ca1f6da70e.png)

Commit the changes.

![image](https://user-images.githubusercontent.com/125093474/234810630-2df16172-8f43-40f4-92d7-aae447e1f08b.png)

The status of the scans will be shown when the green tick (or orange circle if the scan is ongoing, or red cross if the scan failed) is clicked.
![image](https://user-images.githubusercontent.com/125093474/234810686-41490e4a-f5ea-4d20-97d1-6f0f0f040dfa.png)

Detailed information of the results of the scans, as well as an option to automatically create a pull request to solve the vulnerability, will be available in the Security tab.

![image](https://user-images.githubusercontent.com/125093474/234810709-c256a140-fe16-4a45-8bd3-a1d19a91ce36.png)
