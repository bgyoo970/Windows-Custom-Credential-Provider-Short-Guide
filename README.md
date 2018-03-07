# Windows-Custom-Credential-Provider-Short-Guide
This guide is to help with the initial build and set up of the Microsoft sample code of credential providers



For those learning how to install and implement a custom credential provider for the windows login using the Microsoft samplecredentialprovider code provided in the following link, I am creating a general list of instructions to get started. This guide is in no way associated with Microsoft and the code provided in the links will be shown as is if the resources remain available. Please note that these instructions are from my own personal use and experience and will not be held liable for damages or misuse of proprietary code and/or your personal machine. I do not claim ownership of any of the code or resources listed.

Note that registering or unregistering dlls can cause instability for your machine and prevent you from logging into your Windows machine. Take care to have a way to back up your data or use a virtual machine with a separate OS to minimize the risk of corrupting your machine.

Using a virtual machine, you will need to find a copy of a Windows OS ISO and enable (VT-x) virtualization in your BIOS

The following link contains sample Credential Provider code from Microsoft to build the dll to install as a part of your windows registry. All code was built on Visual Studio Community 2017 in my own case.

https://github.com/pauldotknopf/WindowsSDK7-Samples/tree/master/security/credentialproviders

Note: You must build this code and register in the dll in their respective OS. I had trouble running the credential providers when I had built the code on the Windows 7 OS, and then registered the dll into a Windows 10 OS. The Windows 10 OS did not display the user tiles when I registered my dll built from Windows 7.

Download Visual Studio Community edition of your choice to use as your IDE and build the sample credential provider listed above.

1.       (optional, yet highly recommended for the stability of your own machine) Set up a virtual machine with your desired Windows OS

2.       Pull/download the sample credential provider code from the github listed above

3.       Download Visual Studio (during the time I wrote this, I used the Community 2017 edition)

4.       In your installation of Visual Studio, make sure to include

5.       In the /WindowsSDK7-Samples/security/credentialproviders/ folder, CredentialProvdersSamples.sln can be run to open up the sample code in visual studio.

6.       Set your configuration to your corresponding System type (x86 or x64) by right clicking the desired project(s)->properties->Configuration Properties (or configuration Manager, it may vary from version to version) and setting Configurations and platform to the following:

-          For 32-bit (x86)

Configuration: Debug
Platform: x86

-          For 64-bit (x64)

Configuration: Release

Platform: x64

7.       Right-click your project(s)->build solution

8.       Find the dll in the directory …/credentialproviders/x64/release/ 
(or for 32-bit machines …/credentialproviders/Win32/Debug/)

9.       Take the desired the .dll of the credential provider you wish to install and put it into your System32 folder (Typically in the following directory: C:\Windows\System32)

10.   Use the .reg file located in your respective project folder to register your dll and have it show up in your windows log on (…/credentialproviders/samplecredentialprovider/Register.reg)

A Unregister.reg file is also located within the same directory if you want to unregister your dll

11.   Log out to the windows login screen and your custom credential provider should supply their custom user tiles.

 

Take snapshots of your virtual machine to help backup your work as you develop. If you cannot boot into your OS due to a crash or a perpetual loop, you can reboot the VM into safe mode, log in through the standard windows user/pass, and unregister the file. If for some reason you cannot start your OS into safe mode, you will need to revert back to a previous snapshot of your VM and resume that way.

 

 

Useful links to get you started:

1.       Starting to build your own credential provider

https://blogs.msmvps.com/alunj/2011/02/21/starting-to-build-your-own-credential-provider/

 

2.       Sharing folders/files between your local drive and your virtual machine (VirtualBox)
https://operating-systems.wonderhowto.com/how-to/share-local-drives-and-folders-using-oracle-vm-virtualbox-with-guest-windows-os-0126237/

 

3.       Credential Providers in Windows 10

https://msdn.microsoft.com/en-us/library/windows/desktop/mt158211(v=vs.85).aspx

 

4.       Credential Provider Technical Reference (Overview of variables, functions, and architecture of the sample Credential Provider code)

http://go.microsoft.com/fwlink/?LinkId=717287
