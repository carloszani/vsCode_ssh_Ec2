## vsCode_ssh_AwsEc2
 
 How to connect Visual Studio Code remotely via **Windows 10 Home** to an AWS EC2 instance via SSH to work remotely in an IDE.

## Description
The process below is for those who have Windows 10 Home Edition and want to use Visual Studio Code to take full advantage of VS Code's feature set. Once connected to a server, you can interact with files and folders anywhere on the remote filesystem. This lets VS Code provide a local-quality development experience — including full IntelliSense (completions), code navigation, and debugging — regardless of where your code is hosted. **No source code needs to be on your local machine to gain these benefits**.
 
## Table of contents
* [Prerequisites](#Prerequisites)
* [Getting started](#Getting-started)
* [SSH host setup](#SSH-host-setup)
* [SSH host setup](#SSH-host-setup)
* [Connect Visual Studio Code to EC2](#Connect-Visual-Studio-Code-to-EC2)
* [Next steps](#Next-steps)

## Prerequisites
* Have an AWS account with permission to create and run EC2 instances. (If you don't have it, follow the instructions [link](https://portal.aws.amazon.com/billing/signup?nc2=h_ct&src=header_signup&redirect_url=https%3A%2F%2Faws.amazon.com%2Fregistration-confirmation#/start).
* Basic knowledge of AWS, how to create EC2 instances and access remotely.
* Have an EC2 instance created on AWS and with the public and private key files on your local computer. 
* If you are not yet aware of this process, read the AWS [documentation](https://docs.aws.amazon.com/efs/latest/ug/gs-step-one-create-ec2-resources.html).
* [Putty](https://www.chiark.greenend.org.uk/~sgtatham/putty/) - a free SSH and Telnet client.
* [Git](https://git-scm.com/download/win) for Windows - for obvious use and also serves as an SSH client in Windows 10 Home. There is a possibility to use another SSH client - Windows OpenSSH Client, but I think it is unnecessary for those who have Git.
* [Visual Studio Code](https://code.visualstudio.com).
* After installing Visual Studio Code, you must install the extension *[Remote Development extension pack](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.vscode-remote-extensionpack)*. There are two ways: by the link contained in this description or by the extension manager of Visual Studio Code itself that can search for the name of the extension and install it.
 
## Getting started
* Assuming that **all prerequisites have been made and are ready**, let's first validate that the extension in Visual Studio Code is ready for use:
* In the **lower left corner of the VSCode**, a small green rectangle should appear and if you place the mouse pointer over it, the hint "**Open a remote window**" will appear. If it is not showing, make sure the extension has been installed correctly.

![Visual Studio Code Footer](https://imgur.com/vN2EsPg.png)

## SSH host setup 
When creating an EC2 instance on AWS, they provide a public and private key pair to remotely access the instance via SSH (default port 22). However, the extension installed in Visual Studio Code uses another coding standard to remotely access the EC2 instance. 
Follow the next steps to convert the private key reported by Amazon to the standard supported by the extension.

1. Open PuTTYGen locally and load the private key you want to convert.
2. Select **Conversions > Export OpenSSH key** from the application menu. Save the converted key (for example **aws_instance** - this file has no extension) to a local location **under the.ssh directory** in your user profile folder (for example **C:\Users\youruser\.ssh**).
3. Validate that this new local file is owned by you and no other user has permissions to access it.
4. In VS Code, run **Remote-SSH: Open Configuration File...** in the Command Palette (**F1**), select the SSH config file you wish to change, and add (or modify) a host entry in the config file as follows to point to the file:

![Remote Host File](https://imgur.com/yc2bhmn.png)

For exemple:
    **Host aws-ec2-instance**
        **User ec2-user** (remember: in a AWS EC2 Linux, the user is alway **ec2-user**)
        **HostName 18.15.0.11** (remember: when you create a new AWS EC2 instance, an IPv4 Public IP is always provided by AWS and associated with the instance, check the AWS console for your public IP of your instance. Important: the IP changes every time you STOP and START the instance. Whenever there is an error when connecting through Visual Studio, make sure that the EC2 IP is updated in the file.)
        **IdentityFile c:\user\.shh\aws_instance** (Full path and name of the file generated in step 2 above.)

## Connect Visual Studio Code to EC2
1. In Visual Studio Code, press **F1** and search for: **Remote-SSH: Connect to Host...**
2. Select the host name provided by the file in the previous **SSH host setup** step **4**, in this case **aws-ec2-instance**
3. If the extension does not automatically identify the EC2 operating system, select from a list that will be displayed and follow the instructions.
4. Check if the connection has been successfully established by looking at the bottom left corner, if the name of the host you selected appears inside the green rectangle.

![Connected Ok](https://imgur.com/znRKW2J.png)

## Next Steps

I hope you have successfully managed to get here with your remote remote connection between Visual Studio Code and your AWS EC2 instance. Since you are connected with VSCode, you can download Git repositories through VSCode and they will be in the EC2 instance. You can also download Docker extensions to use in VSCode remotely and take advantage of everything the IDE provides.

**I hope this short tutorial will help you**.

Thank you.