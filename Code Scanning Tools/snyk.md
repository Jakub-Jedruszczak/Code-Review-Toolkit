# Snyk

Snyk (<https://snyk.io/>) is a cloud-focused Static Analysis Security Testing (SAST) tool used by developers to perform static code analysis on their code and dependencies to scan for vulnerabilities. Snyk is available as a plugin in many IDEs including Eclipse, Visual Studio, Visual Studio Code, and JetBrains. Is also available as a GitHub Action, allowing contributors to perform a code scan with every commit and merge. 

Snyk specialises in cloud deployments, performing checks on both the code and the infrastructure that your service will run on. This allows developers to also scan their Infrastructure as Code for misconfiguration-caused vulnerabilities, which is a feature not present in most SAST’s. Snyk currently supports Terraform, CloudFormation, Kubernetes, Docker, AWS, Azure, and Google Cloud.

## Snyk Container

Snyk Containers is a Snyk service which automatically allows developers to scan for and resolve container and workload vulnerabilities. Snyk scans for vulnerabilities such as Use After Free and Out of Bounds Write, as well as more complex vulnerabilities for specific cloud services such as S3 Buckets.  

## Continuous Monitoring

Snyk allows developers to continuously track and monitor your repository’s pull requests, issues, and security alerts. This is a good feature for managing and prioritising various aspects of your project such as maintenance, security patches, and changing dependencies.

## Compliance Automation

Snyk provides rudimentary automated regulatory compliance checks and resolution. Snyk also provides automated open-source license compliance that alerts developers to the licensing restrictions that apply to open-source packages so they can compare them against their enterprise’s internal legal policies to ensure that their code is compliant. Snyk Compliance Automation can perform audits for various software development lifecycle frameworks such as ISO, namely ISO27001, AWSWA, CIS Azure Benchmark, NIST, SOC, and HIPAA.

# How to Install

## Use with GitHub

_Note: The GitHub integration works per user account and not per Snyk Organization. Each person in the Organization sets up the integration and their own unique integration settings: there are no shared Organization level settings for the GitHub integration._

First, create a Snyk account. There is no fee required for the free version, although more advanced services such as reports and IaC are only available to Team and Enterprise accounts.

Next, select which integration you wish to use. For this example, we will use GitHub.
![image](https://user-images.githubusercontent.com/125093474/234808246-2d46d52d-cd05-4eab-b0cf-341d5d248012.png)
Next, select whether you want to scan all your repositories or only your public ones. Generated pull requests in public repositories will be made by the SnykBot user, while pull requests in your private repositories will be made under your username.
![image](https://user-images.githubusercontent.com/125093474/234808322-c83d8be4-3761-46dd-aeba-c82930498559.png)
Select which Snyk features you want to use, then proceed to authenticate with GitHub.
![image](https://user-images.githubusercontent.com/125093474/234808426-805af3d9-3c53-4a28-9bf2-1ceb07f71984.png)
Once the setup is complete, you may select which repository you wish to manage with Snyk.
![image](https://user-images.githubusercontent.com/125093474/234808843-2a329862-c733-4606-aec4-db07035a7206.png)
Snyk now shows the number of Critical, High, Medium, and Low risk vulnerabilities.
![image](https://user-images.githubusercontent.com/125093474/234809094-5b385f26-1037-4d92-a837-9caed1066522.png)
## Use with IDE 
In Visual Studio Code, navigate to File>Preferences>Extensions
 ![image](https://user-images.githubusercontent.com/125093474/234809254-88810d0b-31cd-42e4-bb4c-d2c834398430.png)
After searching for Snyk, select the top result as shown below.
![image](https://user-images.githubusercontent.com/125093474/234809192-47243f70-52a4-487b-8848-d2c817a98e5a.png)
Snyk will now be available as a button on the left side panel. Authenticate your code to begin.
![image](https://user-images.githubusercontent.com/125093474/234809430-c80e301c-2631-482f-8feb-34d408c21fa6.png)
Once complete, Snyk will find vulnerabilities and issues with your code. A command line interface is also available.
![image](https://user-images.githubusercontent.com/125093474/234809456-bb892bff-dcdb-4856-9727-632787791294.png)

 