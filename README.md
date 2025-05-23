<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
This tutorial walks through the full deployment of osTicket, an open-source help desk ticketing system. Outlining all key installation steps, from provisioning a VM in Microsoft Azure to configuring IIS, PHP, MySQL, and the osTicket web interface.

Whether you're simulating a help desk environment for learning or testing a production-style deployment, this guide demonstrates practical setup experience valuable for IT support and sysadmin roles.<br />


<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Internet Information Services (IIS)
- Heidi SQL

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)

<h2>List of Prerequisites</h2>

- Microsoft Azure account(deployes windows 10 VM)
- ### [Consolidated osTicket-Installation files](https://drive.google.com/uc?export=download&id=1b3RBkXTLNGXbibeMuAynkfzdBC1NnqaD)

<h2>Installation Steps</h2>

**Step 1: Provision a Windows 10 VM in azure**
![RDC](https://github.com/user-attachments/assets/f439ca3e-aad4-49ed-8db7-65ebc21c79c1)

- In Microsoft Azure, create a new Windows 10 virtual machine.
- Allocate at least 2 vCPUs for proper performance.
- After provisioning, connect to the VM using Remote Desktop Protocol (RDP) with the public IP, username, and password you set during VM creation.

**Step 2: Downloas and prep install**
![extract all](https://github.com/user-attachments/assets/d13ddc47-48cf-4519-ba2f-5fbb1228aac6)

- Once logged into the VM, download the osTicket Installation Package from the link listed in the prerequisites.
- Move the zipped folder to the desktop for easy access.
- Right-click the folder and choose “Extract All” to unpack the contents.

**Step 3: Eanble IIS & required windows feature**
![control panel](https://github.com/user-attachments/assets/8cbff76f-a3a0-46cc-acbd-268336023512)

- Open the control panel and click "uninstall a program"
- Instead of choosing a program to uninstall we will be enabling CGI

![CGInIIS](https://github.com/user-attachments/assets/4f81468a-ab0d-48f6-a7c2-b23eb35f2668)

- On the left-hand side, click “Turn Windows features on or off.”
- In the Windows Features window:
- Expand Internet Information Services (IIS)
- Expand World Wide Web Services > Application Development Features
- Check CGI
- Click OK to apply the changes.

**Step 4: Begin installing osTicket**
![image](https://github.com/user-attachments/assets/d20126a5-5d5c-4078-9fa3-7f6136bfa2f9)
![image](https://github.com/user-attachments/assets/9e2f9c21-1464-43a9-8664-82f62fa3c7c4)

- Open the extracted osTicket installation folder.
- Start by installing PHP Manager and IIS Rewrite Module

**Step 5: Configure PHP Directory**
![NEW FOLDR](https://github.com/user-attachments/assets/6cdb918f-7736-4634-ae2e-3bfd853d43a0)
![image](https://github.com/user-attachments/assets/8ddaf5ba-2503-413a-8eb3-17ef195df182)

- Navigate to *C:* and create a new folder named PHP.
- In the installation folder, locate the zipped PHP files, and extract them to the newly created C:\PHP folder.

**Step 6: Install SQL server and supporting components**
![image](https://github.com/user-attachments/assets/e1c51271-5d7b-457b-b49f-ebda1dfa748c)
![image](https://github.com/user-attachments/assets/b71688e9-cb84-4215-a73c-8f1cededf2a6)

- Run the VC_redist installer first, followed by the SQL Server Installer.
- During SQL installation:
  - Choose the Typical setup option
  - Select Standard Configuration when prompted
  - Set a secure password and make a note of it (you'll use it in SQL and osTicket setup)
The 2 pictures below will display the only SQL configurations you'll have to adjust
![image](https://github.com/user-attachments/assets/eb919599-6d0a-46a0-942c-2a3573fe766a)
![PW](https://github.com/user-attachments/assets/557d9cf1-589e-4967-886e-e34567c2de45)

**Step 7: Register PHP in IIS**
![iisadmin](https://github.com/user-attachments/assets/7c6d32e9-c220-49d0-9168-08defa75e2c7)
- Open IIS as an administrator


![php manager](https://github.com/user-attachments/assets/60a7d90c-723e-4443-b151-b67f849cade5)
![cgi](https://github.com/user-attachments/assets/bb1a7495-dff8-4181-ac51-dda16ca0d195)

- Click on the osTicket site connection in the left pane.
- Open PHP Manager and click “Register new PHP version.”
-  a pop-up will ask you to provide a file, in our ase it is CGI
-  Browse to C:\PHP and select the file named php-cgi.exe.

**Step 8: Deploy osTicket files to IIS**
![osticket1](https://github.com/user-attachments/assets/c77655be-53ef-4aae-85c4-5dea51f2d689)
![osticket2](https://github.com/user-attachments/assets/49938d34-e9a9-4d54-bba7-efe8b1d01e65)

- In the installation folder, extract "osTicket-v1.15.8"
- once extracted it will present 2 folders, upload and scripts as shown in the image
- move the upload folder to the root folder, found via the c drive to "inetpub" folder to "wwwroot" folder(C:\inetpub\wwwroot)
- once transfered rename it to osTicket

**Step 9: Launch osTicket in browser**
![browse](https://github.com/user-attachments/assets/d358ee5a-5330-4e7f-a109-023e2310b9a6)

- now going back into IIS expand the site list/folder until reaching the osTicket file
- To open our osTicket site, on the right click "browse*80(http)" launching the web installer as displayed in the image above

 **Step 10: Enable PHP Extensions**
![image](https://github.com/user-attachments/assets/675a5509-36a4-4c2e-af2c-3e349155ac97)

- Most likely the installer will report missing extensions we will enable the required ones.
- Open PHP Manager again and this time under PHP extenions open "enable or disable an extension"

![osrefresh2opt](https://github.com/user-attachments/assets/03593e90-71f0-49c8-9518-bad5dcb5c280)

- Enable the required extensions and refresh osTicket site, turning the extensions to a green check representing they've been enabled.
  
**Step 11: Rename Configuration File**
![rename](https://github.com/user-attachments/assets/b78f4116-c88b-43a7-a000-dbd0a0ad2ae8)

- Go into the osTicket\include folder and rename ost-sampleconfig.php to ost-config.php

![security](https://github.com/user-attachments/assets/8ede07b8-60e0-4c1b-9c28-0944f278cb42)

- Right-click the file, open Properties and under Security open the Advanced options.
- Adjust permissions as needed for setup access. you can disable, add, or delete permissions regarding access

**Step 12: Set Up the Database with HeidiSQL**
![database connect](https://github.com/user-attachments/assets/e566b513-ef7d-4af9-94ea-ab9f18ac200f)

- lets not forget our final item in the osTicket install folder, HeidiSQL, it will allow us to make a connection to our database after setting one for osTicket

![image](https://github.com/user-attachments/assets/aa14edd7-f566-40d7-afd3-b886fb0f3948)

- Install and open HeidiSQL from the installation folder.
- Click “Add New” and enter the username and password used during SQL install

![new database](https://github.com/user-attachments/assets/289b8415-14e1-4b5a-b09b-0bb7f324341a)
- Lastly, Connect and right-click the left pane to create a new database named osTicket, the browser will make use of this

**Step 13: Complete osTicket Web Installer**
![install os](https://github.com/user-attachments/assets/3dddc165-d441-440a-87e4-24ee35d7f6e8)

 - Return to the browser and fill in the:
 - Helpdesk name
 - Admin user info
 - MySQL database credentials for osTicket
- refrence the image above

*Congratulations! Your osTicket installation is now complete. You’ll be redirected to the login page and provided with access to documentation, control panel, and user dashboard*

- Continue to: **[Post-Install Configuration](https://github.com/StanleyD3/post-install-config)**
