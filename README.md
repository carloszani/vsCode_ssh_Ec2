## vsCode_ssh_AwsEc2
 
 How to connect Visual Studio Code remotely via **Windows 10 Home** to an AWS EC2 instance via SSH to work remotely in an IDE.

## Description
The process below is for those who have Windows 10 Home Edition and want to use Visual Studio Code to take full advantage of VS Code's feature set. Once connected to a server, you can interact with files and folders anywhere on the remote filesystem. This lets VS Code provide a local-quality development experience — including full IntelliSense (completions), code navigation, and debugging — regardless of where your code is hosted. **No source code needs to be on your local machine to gain these benefits**.
 
## Table of contents
* [Prerequisites](#Prerequisites)
* [Getting started](#Getting-started)

## Prerequisites
* Have an AWS account with permission to create and run EC2 instances. (If you don't have it, follow the instructions [link!](https://portal.aws.amazon.com/billing/signup?nc2=h_ct&src=header_signup&redirect_url=https%3A%2F%2Faws.amazon.com%2Fregistration-confirmation#/start)
* Basic knowledge of AWS, how to create EC2 instances and access remotely.
* Have an EC2 instance created on AWS and with the public and private key files on your local computer. 
* If you are not yet aware of this process, read the AWS [documentation!](https://docs.aws.amazon.com/efs/latest/ug/gs-step-one-create-ec2-resources.html).
* [Putty!](https://www.chiark.greenend.org.uk/~sgtatham/putty/) - a free SSH and Telnet client
 
## Getting started
