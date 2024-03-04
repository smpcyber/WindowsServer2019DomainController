<h1>Windows Server 2019 Domain Controller - WIP</h1>

<h2>Description</h2>
<p>
Step-by-step process of installing and setting up Windows Server 2019 as a domain controller.  Using Oracle VirtualBox for virtualization, including the extension pack for disk encryption.
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
<sub>Name virtual machine and select Windows Server 2019 ISO file under "ISO Image" and click Next.
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
<sub>Select Disk Encryption tab under General and select encryption method, enter and re-enter password</sub>
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
<sub>Start up virtual machine, enter disk encryption password</sub>
<br />
<br />
<img src="https://i.imgur.com/9OJX3TP.png" width=50% height=50%>
<br />
<sub>Set language, time, currency, and keyboard method, click Next</sub>
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
<sub>Set password, finish installation</sub>
<br />
<br />
<img src="https://i.imgur.com/6wjIHsr.png" width=50% height=50%>
<br />
<sub>After installation, click "Input" on VM toolbar and select "Insert Ctrl-Alt-Del"</sub>
<br />
<br />
<b>[Installing VirtualBox Guest Additions on Windows Server 2019]</b>
<br />
<br />
<img src="https://i.imgur.com/J98944R.png" width=50% height=50%>
<br />
<sub>Upon login, click "Devices" on VM toolbar and select "Insert Guest Additions CD Image"</sub>
<br />
<br />
<img src="https://i.imgur.com/gdMdncA.png" width=50% height=50%>
<br />
<sub>Open File Explorer, select "CD Drive (D:) VirtualBox Guest Additions", install "VBoxWindowsAdditions-amd64"</sub>
<br />
<br />
<b>[Network Adapter Configuration]</b>
<br />
<br />
<img src="https://i.imgur.com/KkMqZmJ.png" width=50% height=50%>
<br />
<sub>After finishing installation, reboot operating system</sub>
<br />
<br />
<img src="https://i.imgur.com/S599pHb.png" width=50% height=50%>
<br />
<sub>Right-click network icon in taskbar, select "Open Network & Internet settings"</sub>
<br />
<br />
<img src="https://i.imgur.com/UZX6vrS.png" width=50% height=50%>
<br />
<sub></sub>
<br />
<br />
<img src="" width=50% height=50%>
<br />
<sub></sub>
<br />
<br />
<img src="" width=50% height=50%>
<br />
<sub></sub>
<br />
<br />

</p>

<img src="" width=50% height=50%>
<br />
<sub></sub>
<br />
<br />
