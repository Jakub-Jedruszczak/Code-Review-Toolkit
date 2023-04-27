# Automated Security Helper (ASH)
https://github.com/aws-samples/automated-security-helper
Automated Security Helper (ASH) is a reactive SAST toolkit intended for early stages of development; it consists of a library of various tools for testing programs for security vulnerabilities. ASH is equipped to work with Git, Python, Jupyter Notebook, Java, JavaScript/ Node JS, Go, Bash, C# and various Infrastructure as Code (IAC) tools like AWS SAM.
While the creator of ASH does not own any of the tools used to test the code, they regularly update them to the current version.
## How to use
This SAST is built for Linux only, therefore you need to install WSL in order to run it.

- Install a Windows Subsystem for Linux (WSL) with an Ubuntu distribution. Be sure to use the WSL 2.
- Install Docker Desktop for windows and activate the integration of the WSL.
- Clone this git repository.
- Execute the helper tool from the folder downloaded in the previous step from the Ubuntu WSL.

For Linux users, simply use the ash command to run the tool. Use `ash –h` for help.
