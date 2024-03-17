<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
<p>In this lab, I install osTicket from the ground up using the necessary installation files. There are a few steps to take before the installation of the ticketing system. This lab is done on Windows 10 Pro  with a VM made on Azure. The necessary installation files that are referenced and used are located <a href="https://drive.google.com/drive/u/2/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6">here!</a><br />
 </p>

 <h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop Connection
- Internet Information Services (IIS)
- MySQL

<h2>Operating Systems Used </h2>

- Windows 10 Pro</b> (21H2)

 <a href="https://imgur.com/7Luq7Se"><img src="https://i.imgur.com/7Luq7Se.png" title="source:imgur.com" height="50%" width="50%"/></a>

<p>Since I am using a mac, I have gone ahead and installed Microsoft Remote Desktop from the app store in order to SSH into the VM. I will then copy and paste the IP address of my virtual machine into Microsoft Remote Desktop and attempt to connect from there.</p>

<a href="https://imgur.com/ji2hilZ"><img src="https://i.imgur.com/ji2hilZ.png" title="source: imgur.com" height="80%" width="80%"/></a>

<p>Before installing any files, Internet Information Services (IIS) needs to be enabled. We are installing osTicket locally and it needs IIS in order to function. To turn on IIS, open the Control Panel. From the Control Panel, open Programs and click on "Turn Windows Features On or Off". Within this menu, expand "Internet Information Services", expand "Web Management Tools" and enable "IIS Management Console". Click and expand "World Wide Web Services" and expand "Application Development Features". In "Application Development Features", enable "CGI" and click ok to confirm.
</p>
<a href="https://imgur.com/9RxHeZX"><img src="https://i.imgur.com/9RxHeZX.png" title="source: imgur.com" /></a>

<p> These are all the files needed for this lab </p>

<a href="https://imgur.com/vROpHZx"><img src="https://i.imgur.com/vROpHZx.png" title="source: imgur.com" height="80%" width="80%"/></a>

<p>Install PHP Manager for IIS (PHPManagerforIIS_V1.5.0.msi)</p>

<a href="https://imgur.com/RqG2uIb"><img src="https://i.imgur.com/RqG2uIb.png" title="source: imgur.com" height="80%" width="80%"/></a>

<p>Install the Rewrite Module (rewrite_amd64_en-US.msi) after installing PHP Manager for IIS.</p>

<a href="https://imgur.com/pt04x5B"><img src="https://i.imgur.com/pt04x5B.png" title="source: imgur.com" /></a>


<p>After installing the Rewrite Module, create a new folder called "PHP" on the Windows (C:) drive. This new folder will be used to unzip the contents from the PHP 7.3.8 (php-7.3.8-nts-Win32-VC15-x86.zip) zip folder in the Downloads folder. Extract all contents from the zip folder into the PHP folder. The above image shows that we are in (C:) drive inside PHP with all the folder contents fromPHP 7.3.8 (php-7.3.8-nts-Win32-VC15-x86.zip)</p>

<a href="https://imgur.com/KaQJZU5"><img src="https://i.imgur.com/KaQJZU5.png" title="source: imgur.com" height="80%" width="80%" /></a>

<p>Install VC_redist.x86.exe </p>

<a href="https://imgur.com/sW56adp"><img src="https://i.imgur.com/sW56adp.png" title="source: imgur.com" height="80%" width="80%" /></a>

<p>Install MySQL 5.5.62 (mysql-5.5.62-win32.msi). Within the MySQL setup wizard, click "I agree" and select a Typical install and Install. Launch the Configuration Wizard after the installation. Select Standard Configuration and select Install As Windows Service and make sure Launch the MySQL Server automatically is checked. For credentials, the username will be root and the password is Password1. This will serve as a database that will store all the data for the osTicket application.</p>

