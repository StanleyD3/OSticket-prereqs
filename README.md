<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
This tutorial outlines the prerequisites and installation of the open-source help desk ticketing system osTicket.<br />


<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Internet Information Services (IIS)

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)

<h2>List of Prerequisites</h2>

- Microsoft Azure account
- ### [Consolidated osTicket-Installation files](https://drive.google.com/uc?export=download&id=1b3RBkXTLNGXbibeMuAynkfzdBC1NnqaD)

<h2>Installation Steps</h2>

![RDC](https://github.com/user-attachments/assets/f439ca3e-aad4-49ed-8db7-65ebc21c79c1)

- In microsoft Azure create a windows 10 virtual machine with at least 2Vcpus as shown above
- Next, log into the VM you created via RDP using the public Ip address assigned, your username, and password set when creating the VM

![extract all](https://github.com/user-attachments/assets/d13ddc47-48cf-4519-ba2f-5fbb1228aac6)

- Once logged into the VM use the link under the list of pre-requisites "Consolidated osTicket-Installation files" for the osTicket install files consolidated to a single folder
- Download the folder, drag it to desktop for easy access
- after it has downloaded right click the folder and extract all files onto your computer
- 
![control panel](https://github.com/user-attachments/assets/8cbff76f-a3a0-46cc-acbd-268336023512)

- Open the control panel and click "uninstall a program"
- Instead of choosing a program to uninstall we will turning CGI on

![CGInIIS](https://github.com/user-attachments/assets/4f81468a-ab0d-48f6-a7c2-b23eb35f2668)

- On the left hand side there is a "turn windows features on or off" option, click it
- a windows feature pop up will show
- Find Internet Information services, check the folder and expand it
- once expanded click world web services and expand that file
- under world web services check and expand the "Application Development Features" file
- And finally check CGI and hit okay

![image](https://github.com/user-attachments/assets/d20126a5-5d5c-4078-9fa3-7f6136bfa2f9)
![image](https://github.com/user-attachments/assets/9e2f9c21-1464-43a9-8664-82f62fa3c7c4)

- Open the osTicket install file and begin installing the contents, the first 2 files will be PHPManager and rewrite

![NEW FOLDR](https://github.com/user-attachments/assets/6cdb918f-7736-4634-ae2e-3bfd853d43a0)
![image](https://github.com/user-attachments/assets/8ddaf5ba-2503-413a-8eb3-17ef195df182)

- Go to your C drive and create a folder named "PHP"
- Going back into the osTicket install folder extract all the zipped php file, when extracting make the destination file the PHP file just created on the C drive

![image](https://github.com/user-attachments/assets/e1c51271-5d7b-457b-b49f-ebda1dfa748c)
![image](https://github.com/user-attachments/assets/b71688e9-cb84-4215-a73c-8f1cededf2a6)

- Now continue installing the remaining files starting with "VC_redist" and continue to SQL, when installing make sure to elect for "typical" setup type
- The 2 pictures below will display further configuration
![image](https://github.com/user-attachments/assets/eb919599-6d0a-46a0-942c-2a3573fe766a)
- Select standard configuration
![PW](https://github.com/user-attachments/assets/557d9cf1-589e-4967-886e-e34567c2de45)
set a password you'll remember

![iisadmin](https://github.com/user-attachments/assets/7c6d32e9-c220-49d0-9168-08defa75e2c7)

- Open IIS as an administrator
![php manager](https://github.com/user-attachments/assets/60a7d90c-723e-4443-b151-b67f849cade5)
![cgi](https://github.com/user-attachments/assets/bb1a7495-dff8-4181-ac51-dda16ca0d195)

- in ISS click the osTicket connection and open PHP Manager
- Then open "register new PHP version" 
- the pop up will ask you to provide a file in which we will be using CGI
- on the C drive open up the PHP foler we created and select the "php-cgi" file

![osticket1](https://github.com/user-attachments/assets/c77655be-53ef-4aae-85c4-5dea51f2d689)
![osticket2](https://github.com/user-attachments/assets/49938d34-e9a9-4d54-bba7-efe8b1d01e65)

- Now reopen the osTicket install folder to "extract all" the other zip file labeled "osTicket-v1.15.8"
- once you extract all open the folder and it should present 2 folders, 1 that says uploan and another that says scripts as shown in the image
- move the upload folder from that file to the root folder which can be found via the c drive to "inetpub" folder to "wwwroot" folder
- once transfered rename it to osTicket
- 
![browse](https://github.com/user-attachments/assets/d358ee5a-5330-4e7f-a109-023e2310b9a6)

- now going back into IIS expand the folders until you see the osTicket file
- Once you click it you will have the option to open our osTicket site, click "browse*80(http)" as displayed in the image above
 
![image](https://github.com/user-attachments/assets/675a5509-36a4-4c2e-af2c-3e349155ac97)

- In order to proceed we have to enable the extentions displayed on the site(the required ones)
- Open PHP Manager again and this time under PHP extenions open enable or disabe an extension

![osrefresh2opt](https://github.com/user-attachments/assets/03593e90-71f0-49c8-9518-bad5dcb5c280)

- Enable the required extensions and refresh osTicket site, it should turn the extensions to a green check

![rename](https://github.com/user-attachments/assets/b78f4116-c88b-43a7-a000-dbd0a0ad2ae8)

- As shown in the image above go to the osTicket folder, open include and rename ost-sampleconfig.php to ost-config.php
- now right click it and open properties

![security](https://github.com/user-attachments/assets/8ede07b8-60e0-4c1b-9c28-0944f278cb42)

- Go to security and click advanced and here you can disable, add, or delete permissions for site

![database connect](https://github.com/user-attachments/assets/e566b513-ef7d-4af9-94ea-ab9f18ac200f)

- lets not forget our final item in the osTicket install folder, HeidiSQL, it will allow us to make a connection to our database after setting one for osTicket

![image](https://github.com/user-attachments/assets/aa14edd7-f566-40d7-afd3-b886fb0f3948)

- open Heidi and click add new and it will display the image above
- fill in the username and password created when setting up the SQL server
- and open

![new database](https://github.com/user-attachments/assets/289b8415-14e1-4b5a-b09b-0bb7f324341a)

- Now we can create a new database by right clicking the highlighted row and proceeding to create the new database
- name the database osTicket durng creation, the install happening in the browser will make use of this

![install os](https://github.com/user-attachments/assets/3dddc165-d441-440a-87e4-24ee35d7f6e8)
 
-  Now we fill in the database settings in the browser as shown in the image above and click install now
- And congratulations your installation is complete you will be redirected to a page confirming and giving you your osTicket URL, forums, control panels, and documentation
