<h1>Windows Server 2019 Domain Controller - WIP</h1>

<h2>Description</h2>
<p>
Step-by-step process of installing and setting up Windows Server 2019 as a domain controller, including installing Active Directory Domain Services, network adapter configuration, manually adding users to Active Directory, adding users to domain groups, and configuring routing and DHCP.  Using Oracle VirtualBox for virtualization, including the extension pack for disk encryption.
<br />
</p>
<sub><b>**This repository assumes the reader is already familiar with virtualization software.</b></sub>
<br />
<br />
<p align="center">
<b>[Virtualizing and Installing Windows Server 2019]</b>
<br />
<br />
<img src="https://i.imgur.com/hWsPUog.png" width=50% height=50%>
<br />
<sub>From VirtualBox Manager, click New.</sub>
<br />
<br />
<img src="https://i.imgur.com/wjd3tlT.png" width=50% height=50%>
<br />
<sub>Name virtual machine and select Windows Server 2019 ISO file under "ISO Image"
<br />
Click Next.
<br />
<b>**"Skip Unattended Installation" is selected to manually install operating system.</b></sub>
<br />
<br />
<img src="https://i.imgur.com/fqxtPR6.png" width=50% height=50%>
<br />
<sub>Click Settings on newly created virtual machine</sub>
<br />
<br />
<img src="https://i.imgur.com/sLsTyCD.png" width=50% height=50%>
<br />
<sub>Select Disk Encryption tab under General and select encryption method
<br />
Enter and re-enter password to access the machine</sub>
<br />
<br />
<img src="https://i.imgur.com/PgBbKFD.png" width=50% height=50%>
<br>
<sub>Under Network, Adapter 1 is set to NAT to use home network to connect to internet</sub>
<br />
<br />
<img src="https://i.imgur.com/jc0m7eg.png" width=50% height=50%>
<br />
<sub>Adapter 2 is enabled and set to Internal Network, allowing clients to connect to domain server</sub>
<br />
<br />
<img src="https://i.imgur.com/URcOPG5.png" width=50% height=50%>
<br />
<sub>Start up virtual machine
<br />
Enter disk encryption password</sub>
<br />
<br />
<img src="https://i.imgur.com/9OJX3TP.png" width=50% height=50%>
<br />
<sub>Set language, time, currency, and keyboard method
<br />
Click Next</sub>
<br />
<br />
<img src="https://i.imgur.com/qNbU63H.png" width=50% height=50%>
<br />
<sub>Installing "Standard Edition (Desktop Experience) to use GUI to set up Active Directory</sub>
<br />
<br />
<img src="https://i.imgur.com/7PanCaq.png" width=50% height=50%>
<br />
<sub>Custom install as fresh install</sub>
<br />
<br />
<img src="https://i.imgur.com/aI9gZq4.png" width=50% height=50%>
<br />
<sub>Set password
<br />
Finish installation</sub>
<br />
<br />
<img src="https://i.imgur.com/6wjIHsr.png" width=50% height=50%>
<br />
<sub>After installation, click "Input" on VM toolbar
<br />
Select "Insert Ctrl-Alt-Del"</sub>
<br />
<br />
<b>[Installing VirtualBox Guest Additions on Windows Server 2019]</b>
<br />
<br />
<img src="https://i.imgur.com/J98944R.png" width=50% height=50%>
<br />
<sub>Upon login, click "Devices" on VM toolbar
<br />
Select "Insert Guest Additions CD Image"</sub>
<br />
<br />
<img src="https://i.imgur.com/gdMdncA.png" width=50% height=50%>
<br />
<sub>Open File Explorer, select "CD Drive (D:) VirtualBox Guest Additions"
<br />
Install "VBoxWindowsAdditions-amd64"</sub>
<br />
<br />
<img src="https://i.imgur.com/KkMqZmJ.png" width=50% height=50%>
<br />
<sub>After finishing installation, reboot operating system</sub>
<br />
<br />
<b>[Network Adapter Configuration]</b>
<br />
<br />
<img src="https://i.imgur.com/S599pHb.png" width=50% height=50%>
<br />
<sub>Right-click network icon in taskbar
<br />
Select "Open Network & Internet settings"</sub>
<br />
<br />
<img src="https://i.imgur.com/UZX6vrS.png" width=50% height=50%>
<br />
<sub>Click "Change Adapter Options" under Status</sub>
<br />
<br />
<img src="https://i.imgur.com/ovaoih8.png" width=50% height=50%>
<br />
<sub>Right-click an adapter and select "Status" in order to identify which adapter connects the machine to the internet</sub>
<br />
<br />
<img src="https://i.imgur.com/LiKmDrg.png" width=50% height=50%>
<br />
<sub>The IPv4 Address shows 10.0.2.15, indicating this adapter connects the machine to the internet</sub>
<br />
<br />
<img src="https://i.imgur.com/c2Ys094.png" width=50% height=50%>
<br />
<sub>Renaming the Internet adapter and identifying the internal network adapter</sub>
<br />
<br />
<img src="https://i.imgur.com/XNwgmm2.png" width=50% height=50%>
<br />
<sub>The Autoconfigured IPv4 address indicates this adapter is for connecting to an internal network</sub>
<br />
<br />
<img src="https://i.imgur.com/qJhsv1h.png" width=50% height=50%>
<br />
<sub>Identifying both network adapters, right-click on Intranet (internal network)
<br />
Select "Properties"</sub>
<br />
<br />
<img src="https://i.imgur.com/S5RO2Gl.png" width=50% height=50%>
<br />
<sub>Select "Internet Protocol Version 4 (TCP/IPv4)"
<br />
Click "Properties"</sub>
<br />
<br />
<img src="https://i.imgur.com/rTepQ1O.png" width=50% height=50%>
<br />
<sub>The IP address for this domain controller is set to 172.16.0.1</sub>
<br />
<sub>This will also be our default gateway for the Windows 10 domain client</sub>
<br />
<sub>The DNS server address is set to 127.0.0.1, a loopback address or localhost</sub>
<br />
<br />
<b>[Installing Active Directory Domain Services and Promoting to Domain Controller]</b>
<br />
<br />
<img src="https://i.imgur.com/NvF6Xbq.png" width=50% height=50%>
<br />
<sub>On Server Manager Dashboard
<br />
Click "Add roles and features"</sub>
<br />
<br />
<img src="https://i.imgur.com/ynqG6EZ.png" width=50% height=50%>
<br />
<sub>Select "Active Directory Domain Services"
<br />
Click "Add Features" on "Add Roles and Features Wizard" popup</sub>
<br />
<br />
<img src="https://i.imgur.com/VEDk14f.png" width=50% height=50%>
<br />
<sub>Click "Install"</sub>
<br />
<br />
<img src="https://i.imgur.com/TMrurUM.png" width=50% height=50%>
<br />
<sub>After installation completes, click flag notification at top of Server Manager
<br />
Select "Promote this server to a domain controller"</sub>
<br />
<br />
<img src="https://i.imgur.com/U1KruU2.png" width=50% height=50%>
<br />
<sub>Under "Deployment Configuration," select "Add a new forest"
<br />
Enter root domain name</sub>
<br />
<br />
<img src="https://i.imgur.com/mnAsMLl.png" width=50% height=50%>
<br />
<sub>Under "Domain Controller Options," enter and re-enter DSRM password
<br />
Click "Next" until installation</sub>
<br />
<br />
<b>[Adding Administrative Users to Active Directory]</b>
<br />
<br/>
<img src="https://i.imgur.com/DBSC5xh.png" width=50% height=50%>
<br />
<sub>Click "Tools" at top of Server Manager taskbar
<br />
Select "Active Directory Users and Computers"</sub>
<br />
<br />
<img src="https://i.imgur.com/h6dSdCN.png" width=50% height=50%>
<br />
<sub>Right-click domain in left panel
<br />
Highlight "New"
<br />
Select "Organizational Unit"</sub>
<br />
<br />
<img src="https://i.imgur.com/D3wjPh5.png" width=50% height=50%>
<br />
<sub>Name organizational unit, e.g. "Administrators"
<br />
Click "OK"</sub>
<br />
<br />
<img src="https://i.imgur.com/mw6d4m2.png" width=50% height=50%>
<br />
<sub>Under domain, right-click newly created organizational unit folder
<br />
Highlight "New"
<br />
Select "User"</sub>
<br />
<br />
<img src="https://i.imgur.com/qCrY9nj.png" width=50% height=50%>
<br />
<sub>Enter new user information and username
<br />
Click "Next"</sub>
<br />
<br />
<img src="https://i.imgur.com/rySp6ng.png" width=50% height=50%>
<br />
<sub>Enter new user password
<br />
Configured to "Password never expires" only, password management to come later</sub>
<br />
<br />
<img src="https://i.imgur.com/GxbV0UD.png" width=50% height=50%>
<br />
<sub>Right click new user
<br />
Select "Properties"
</sub>
<br />
<br />
<img src="https://i.imgur.com/oo7jW7S.png" width=50% height=50%>
<br />
<sub>Under new user properties, select "Members Of" tab
<br />
Click "Add"</sub>
<br />
<br />
<img src="https://i.imgur.com/9FKvCVF.png" width=50% height=50%>
<br />
<sub>Enter "Domain Admins" under "Enter the object names to select" section
<br />
Click "Check Names"
<br />
Verify the object name is valid and click "OK"
</sub>
<br />
<br />
<img src="https://i.imgur.com/mlFyYtt.png" width=50% height=50%>
<br />
<sub>Click "Apply" and "OK"</sub>
<br />
<br />
<img src="https://i.imgur.com/0bAWDAR.png" width=50% height=50%>
<br />
<sub>Sign out to sign back in as new adminstrative user</sub>
<br />
<br />
<img src="https://i.imgur.com/vjjuy1w.png" width=50% height=50%>
<br />
<sub>Select "Other User" in bottom left of screen
<br />
Enter new administrative user credentials to log in</sub>
<br />
<br />
<b>[Installing and Configuring Remote Access]</b>
<br />
<br />
<img src="https://i.imgur.com/hcM7dhX.png" width=50% height=50%>
<br />
<sub>Upon login, on Server Manager Dashboard, click "Add roles and features"</sub>
<br />
<br />
<img src="https://i.imgur.com/42IrmyG.png" width=50% height=50%>
<br />
<sub>Select "Routing"</sub>
<br />
<br />
<img src="https://i.imgur.com/wP76Bqy.png" width=50% height=50%>
<br />
<sub>Click "Add Features" on the Add Roles and Features Wizard popup</sub>
<br />
<br />
<img src="https://i.imgur.com/v4x6VFb.png" width=50% height=50%>
<br />
<sub>Click "Install"
<br />
Reboot virtual machine to finish installation of remote access</sub>
<br />
<br />
<img src="https://i.imgur.com/DWQ352h.png" width=50% height=50%>
<br />
<sub>
Click "Tools" on the top right of the Server Manager Dashboard
<br />
Click "Routing and Remote Access"</sub>
<br />
<br />
<img src="https://i.imgur.com/uXmQrA2.png" width=50% height=50%>
<br />
<sub>Right click domain server in left panel of Routing and Remote Access window
<br />
Click "Configure and Enable Routing and Remote Access"</sub>
<br />
<br />
<img src="https://i.imgur.com/9poMmcR.png" width=50% height=50%>
<br />
<sub>Under "NAT Internet Connection," select Internet adapter
<br />
Click "Next"</sub>
<br />
<br />
<img src="https://i.imgur.com/OG1ZUFG.png" width=50% height=50%>
<br />
<sub>Finish installing Routing and Remote Access services</sub>
<br />
<br />
<b>[Installing and Configuring DHCP]</b>
<br />
<br />
<img src="https://i.imgur.com/1bnqws2.png" width=50% height=50%>
<br />
<sub>On Server Manager Dashboard, click "Add roles and features"</sub>
<br />
<br />
<img src="https://i.imgur.com/k2Lvsez.png" width=50% height=50%>
<br />
<sub>Select "DHCP Server"
<br />
Click "Add Features" on Add Roles and Features Wizard popup</sub>
<br />
<br />
<img src="https://i.imgur.com/s9akjoY.png" width=50% height=50%>
<br />
<sub>Click "Next" until installation is prompted
<br />
Finish installation</sub>
<br />
<br />
<img src="https://i.imgur.com/tF37ypj.png" width=50% height=50%>
<br />
<sub>Click "Tools" in top right of Server Manager Dashboard
<br />
Select "DHCP"</sub>
<br />
<br />
<img src="https://i.imgur.com/SVqGvbt.png" width=50% height=50%>
<br />
<sub>Under domain server in left panel of DHCP window, right-click "IPv4"
<br />
Select "New Scope"</sub>
<br />
<br />
<img src="https://i.imgur.com/FVSwfoB.png" width=50% height=50%>
<br />
<sub>Enter scope name under New Scope Wizard window
<br />
Set description if helpful
<br />
Click "Next"</sub>
<br />
<br />
<img src="https://i.imgur.com/aZ8hQTv.png" width=50% height=50%>
<br />
<sub>Set beginning IP address of scope
<br />
Set ending IP address of scope
<br />
Set subnet length to 24
<br />
Click "Next"</sub>
<br />
<br />
<img src="https://i.imgur.com/y5EWUsB.png" width=50% height=50%>
<br />
<sub>Select "Yes, I want to configure these options now" under Configure DHCP Options
<br />
Click "Next"</sub>
<br />
<br />
<img src="https://i.imgur.com/IaStPGZ.png" width=50% height=50%>
<br />
<sub>Set default gateway address under Router (Default Gateway)
<br />**Default gateway address in my case is 172.16.0.1 as shown in Network Adapter Configuration</sub>
<br />
<br />
<img src="https://i.imgur.com/b4Ywpr0.png" width=50% height=50%>
<br />
<sub>Confirm parent domain
<br />
Enter client IP(s) to use DNS servers to use on your network
<br />
**I am entering one for the singular Windows 10 domain client
<br />
Click "Add"
<br />
Click "Next"</sub>
<br />
<br />
<img src="https://i.imgur.com/GhYu0uU.png" width=50% height=50%>
<br />
<sub>Select "Yes, I want to activate this scope now" when prompted under Active Scope
<br />
Click "Next"
<br />
Finish configuring scope</sub>
<br />
<br />
<img src="https://i.imgur.com/Hr8gUOf.png" width=50% height=50%>
<br />
<sub>Right-click domain server in left panel of DHCP window
<br />
Select "Authorize"</sub>
<br />
<br />
<img src="https://i.imgur.com/ZMZCuf8.png" width=50% height=50%>
<br />
<sub>Right-click domain server in left panel of DHCP window
<br />
Select "Refresh"</sub>
<br />
<br />
<img src="https://i.imgur.com/NjSezrH.png" width=50% height=50%>
<br />
<sub>Verify connection is live as shown by green checkmarks on icons</sub>
</p>
