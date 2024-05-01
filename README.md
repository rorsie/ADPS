<h1>Active Directory Domain Creation with User-Adding Powershell Script</h1>

<h2>Description</h2>
This project is simply setting up an Active Directory Domain in a Windows Server VM and then adding hundreds of test users by way of a Powershell Script. The goal is to familiarize myself with many of Active Directory's functions and apply some automation to the process.
<br />


<h2>Languages and Utilities Used</h2>

- <b>Microsoft Active Directory</b> 
- <b>Powershell</b>
- <b>Windows Server 2019l</b>
- <b>VirtualBox</b>

<h2>Project Walkthrough:</h2>

<p>
<h3 align="center">Initial Setup</h3> <br/>
To get prepared for this setup I needed to download the Windows Server 2019 ISO off of their website. For this reason, and me switching to Linux personally, I decided to create the small Powershell script that generates the hashes for selected files. I also had to download VirtualBox, which was very a very simple task straight from their sight. This project also comes from <a href="https://www.youtube.com/@JoshMadakor">Josh Madakor</a>, but is slightly modified.
<br />
<br />
<h3 align="center">Creating the Windows 2019 Server VM</h3> <br/>
After downloading Windows Server 2019, it is time to create the VM. I simply named it "DC" for domain controller and gave it 2 cores with 2 Gigabytes of RAM. I also clicked the "advanced" option of bidirectional clipboard/copy and paste support. After mounting the ISO to this VM, I simply launched it and went through the setup process quickly.
<img src="https://i.ibb.co/3zfMK7J/createDC.png" alt="createDC" border="0">
<img src="https://i.ibb.co/YBRtbqx/installserver.png" alt="installserver" border="0">
<br />
<br />
 <h3 align="center"> "Install Active Directory Domain Services and Create a Domain</h3>
Now that the server is set up, I opened up "Server Manager". From the home page I added went through the process of adding the "roles and features", which was ADDS in this case. I selected ADDS and clicked on my server when it prompted me. Now I had to go to the top right of the screen to promote it to a new domain. I chose the option of adding a new forest and named it "thedomain.com". No additional options were necessary and I clicked through the rest of the installation process which ending in a system restart.
<img src="https://i.ibb.co/80ySMbZ/installing-AD.png" alt="installing-AD" border="0">
<img src="https://i.ibb.co/zGRDX8k/deploy-ADdomain.png" alt="deploy-ADdomain" border="0">
 <br />
 <br />
<h3 align="center"> Creating My Own Administrator Account </h3>
After booting back up, I created my own administrator account under Active Directory -> Users and Computers. I also created a new organizational unit called "_ADMINS" to put my new user under. To finish it off, I made sure to add this new user to the "Domain Admins" group. I then logged back in to the domain with this new admin account.
<img src="https://i.ibb.co/jyRP7Pd/createnew-ADMIN.png" alt="createnew-ADMIN" border="0">
<br />
<br />
<h3 align="center">Adding Users via Powershell</h3>
Here I will be using a Powershell script courtesy of <a href="https://www.youtube.com/@JoshMadakor">Josh Madakor</a>. Thankfully he actually walks through the whole script so I understand how it works and can modify it if needed. I copied the script and test user file (containing randomly generated first and last names) to the server VM and ran it from there, after adjusting the execution policy and changing the Powershell directory to where the text file was located. This will create a new organizational unit called "_USERS" and proceed to add new users based on the names provided. The password for the accounts can also be adjusted.
<img src="https://i.ibb.co/XS1czdp/user-CREATIONscript.png" alt="user-CREATIONscript" border="0">
<br />
<br />
<h3 align="center">Final Thoughts</h3>
I really wanted to get some hands-on experience with Active Directory and work on my automation skills, and I believe I accomplished both of those things during this project. During and after the project I was always poking around the server manager and ADDS to get more of a feel for it as a whole.The reason for deviating from Josh's original lab was because I ran into even more problems than he did with the VMWare Network. The server internal and external NIC was set up and was able to get a connection, but the client was never able to connect to the server's internal NIC to make use of the DHCP and DNS services I set up on it. I tried a few things like manually adding the route via command line, but various errors said "no". I still believe I got good value after learning the inner workings and setup of Active Directory along with more knowledge about how to automate processes with Powershell. 

 
</p>

