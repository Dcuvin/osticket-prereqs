<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
<h2>Goal: Demonstrate installation and setup skills for a web server, software configuration and database management, by creating a system where users can access the osTicket application through a web browser to submit and track support tickets, and where a support team can use the application to manage and respond to those tickets.</h2>
<p>In this lab, I install osTicket from the ground up using the necessary installation files. There are a few steps to take before the installation of the ticketing system. This lab is done on Windows 10 Pro  with a VM made on Azure. The necessary installation files that are referenced and used are located <a href="https://drive.google.com/drive/u/2/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6">here!
</a><br />
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

<p>Install VC_redist.x86.exe. Microsoft Visual C++ Redistributable package is required for running PHP on Windows. This package includes essential libraries and components necessary for PHP to function correctly on a Windows system.</p>

<a href="https://imgur.com/sW56adp"><img src="https://i.imgur.com/sW56adp.png" title="source: imgur.com" height="80%" width="80%" /></a>
<a href="https://imgur.com/UQokqLd"><img src="https://i.imgur.com/UQokqLd.png" title="source: imgur.com" height="80%" width="80%"/></a>

<p>Install MySQL 5.5.62 (mysql-5.5.62-win32.msi). Within the MySQL setup wizard, click "I agree" and select a Typical install and Install. Launch the Configuration Wizard after the installation. Select Standard Configuration and select Install As Windows Service and make sure Launch the MySQL Server automatically is checked. For credentials, the username will be root and the password is Password1. This will serve as a database that will store all the data for the osTicket application.</p>

<a href="https://imgur.com/wDfAYMC"><img src="https://i.imgur.com/wDfAYMC.png" title="source: imgur.com" /></a>

<p>Open IIS as an admin and select PHP Manager. Within PHP Manager, select Register new PHP version. Select Browse and select the PHP CGI executable file (php-cgi.exe) within the PHP folder created earlier in the lab. After registering the PHP version, reload the IIS server within the management console. Registering PHP with IIS involves configuring IIS to recognize PHP files and pass them to the PHP interpreter for processing. This step is necessary for IIS to correctly handle PHP scripts and execute them as intended. Reloading IIS involves stopping and starting the IIS server to apply any configuration changes that have been made. This step ensures that the changes made to the IIS configuration, such as registering PHP, take effect.</p>

<a href="https://imgur.com/G1SOaa3"><img src="https://i.imgur.com/G1SOaa3.png" title="source: imgur.com" /></a>

<p>Navigate to the zipped osTicket v1.15.8. Extract and copy the "upload" folder to the following path: c:\inetpub\wwwroot. Within the c:\inetpub\wwwroot folder, rename "upload" to "osTicket." Reload the IIS server afterwards. Extracting the osTicket files and renaming the "upload" folder to "osTicket" prepares the application for installation./p>

<a href="https://imgur.com/RjjHq3e"><img src="https://i.imgur.com/RjjHq3e.png" title="source: imgur.com" /></a>
<a href="https://imgur.com/ItSK8ZV"><img src="https://i.imgur.com/ItSK8ZV.png" title="source: imgur.com" /></a>

<p>Within the IIS console, browse to Sites -> Default -> osTicket. Click "Browse *:80" and the installation page for osTicket will now show up.</p>

 <a href="https://imgur.com/W9TVTI0"><img src="https://i.imgur.com/W9TVTI0.png" title="source: imgur.com" /></a>
 
 <p>Some extensions are not enabled and they will be enabled with the IIS console before installing osTicket. To do so, click on PHP Manager while in the osTicket menu in IIS. Click on "Enable or disable an extension." Enable the following extentions: php_imap.dll, php_intl.dll, php_opcache.dll. Accessing the osTicket site through IIS and configuring PHP extensions like php_imap.dll, php_intl.dll, and php_opcache.dll ensures that the application has the necessary dependencies to run correctly.</p>
 
<a href="https://imgur.com/5pnmWOc"><img src="https://i.imgur.com/5pnmWOc.png" title="source: imgur.com" /></a>
<a href="https://imgur.com/Mml7ggr"><img src="https://i.imgur.com/Mml7ggr.png" title="source: imgur.com" /></a>
<a href="https://imgur.com/4cGsm8B"><img src="https://i.imgur.com/4cGsm8B.png" title="source: imgur.com" /></a>

<p>Before continuing to install osTicket, a file needs to be renamed as well as have its permissions changed. From C:\inetpub\wwwroot\osTicket\include, rename ost-sampleconfig.php to ost-config.php. The newly named ost-config.php will have its permissions changed. Open its Properties and change the following permissions: Disable inheritence -> Remove All and New Permissions -> Everyone -> All.</p>

<a href="https://imgur.com/rcj1VGY"><img src="https://i.imgur.com/rcj1VGY.png" title="source: imgur.com" /></a>
<a href="https://imgur.com/k2qCJvf"><img src="https://i.imgur.com/k2qCJvf.png" title="source: imgur.com" /></a>
<a href="https://imgur.com/9ZjA2Rk"><img src="https://i.imgur.com/9ZjA2Rk.png" title="source: imgur.com" /></a>

<p>Install HeidiSQL. Create a new session with HeidiSQL and enter the same password used in the installation of MySQL earlier. Within the new session, right-click on Unnamed and create a new database named osTicket.</p>

<a href="https://imgur.com/d9aSbeG"><img src="https://i.imgur.com/d9aSbeG.png" title="source: imgur.com" /></a>

<p>Within osTicket browser window, enter the necessary details to set up osTicket. For the MySQL database, use the credentials used for MySQL and HeidiSQL.</p>

<a href="https://imgur.com/ItSK8ZV"><img src="https://i.imgur.com/ItSK8ZV.png" title="source: imgur.com" /></a>
<p> osTicket should now bee succesdully installed!</p>
<a href="https://imgur.com/aUEDsZe"><img src="https://i.imgur.com/aUEDsZe.png" title="source: imgur.com" /></a>

<p>Before continuing to use osTicket, some clean up has to be done. First, delete the setup folder found in C:\inetpub\wwwroot\osTicket. Next, return to C:\inetpub\wwwroot\osTicket\include and change the permissions of the ost-config.php file. The file should no longer have full access to Everyone. Revert the permissions to "Read" only.</p>

<h2>osTicket Installed!</h2>

osTicket is now installed and ready to be used. I used osTicket to understand how ticketing systems work amd how to resolve tickets. In IT Support, I have to work with a team to solve a person's IT related issues through the use of a ticketing system. I used this lab as a means to set up a ticketing system from the ground up and lay the grounds for what I will do in the future.
