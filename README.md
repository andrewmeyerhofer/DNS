<p align="center">
<img width="250" height="250" alt="image" src="https://github.com/user-attachments/assets/08b4eda2-473f-4cc3-a35e-44f13257e740" />


</p>

<h1>On-premises Active Directory Deployed in the Cloud (Azure)</h1>
This tutorial outlines the implementation of on-premises Active Directory within Azure Virtual Machines.<br />



<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- PowerShell

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 11 (24H2)

<h2>High-Level Deployment and Configuration Steps</h2>

- Step 1
- Step 2
- Step 3
- Step 4

<h2>Deployment and Configuration Steps</h2>

<p>
<img width="1095" height="636" alt="image" src="https://github.com/user-attachments/assets/5c35eda0-45f9-4d7e-8d8a-c064fdc1d6cb" />


</p>
<p>
First, I logged into dc-1 and client-1 as jane_admin. On dc-1 I opened Powershell and pinged "Mainframe" (just a random word). Nothing will come up because the word mainframe is not cached in the DNS of the computer. I checked this by typing ipconfig /displaydns.
</p>
<br />

<p>
<img width="927" height="572" alt="image" src="https://github.com/user-attachments/assets/81a416fc-cfc0-4353-bd42-7e7c83dc9bc2" />


</p>
<p>
I then opened notepad and clicked open in the files menu. I went to the system32-drivers-etc folder and found the hosts file. 
</p>
<br />

<p>
<img width="1415" height="737" alt="image" src="https://github.com/user-attachments/assets/98dae576-11c9-4e51-8ef1-e09767c8aa72" />


</p>
<p>
I then opened the host file in notepad.
</p>
<br />

<p>
<img width="1256" height="695" alt="image" src="https://github.com/user-attachments/assets/f14ad02a-8d78-4fa2-9f65-77448ccbca31" />


</p>
<p>
After adding the IP address and name "Mainframe" to the hosts file (and saving it), I was successfully able to ping it from Powershell.
</p>
<br />

<p>
<img width="787" height="697" alt="image" src="https://github.com/user-attachments/assets/a345e53b-073e-437e-b469-5e7435cf5c2f" />


</p>
<p>
I found the dns option under Windows administrative tools.
</p>
<br />

<p>
<img width="850" height="301" alt="image" src="https://github.com/user-attachments/assets/0d3b6cb4-ab9e-4353-8bfd-5473ba3b80ee" />


</p>
<p>
I used ipconfig to get the IPv4 adress.
</p>
<br />

<p>
<img width="947" height="715" alt="image" src="https://github.com/user-attachments/assets/bb3c5777-3a51-4971-943b-898d08e86715" />


</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img width="936" height="650" alt="image" src="https://github.com/user-attachments/assets/3cff2b2c-5a58-40c0-964c-7c6a9bb41e41" />


</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img width="927" height="647" alt="image" src="https://github.com/user-attachments/assets/07c79018-5080-45f6-8934-ad9e5dfd6e78" />


</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img width="610" height="276" alt="image" src="https://github.com/user-attachments/assets/de807da5-b2ad-4fea-815d-5462e4f2daee" />


</p>
<p>
In Powershell I pinged mainframe2. The computer actually had to reach out to the DNS server, as apposed to using local DNS cache or Local Host file.
</p>
<br />

<p>
<img width="962" height="635" alt="image" src="https://github.com/user-attachments/assets/939d6bdb-2670-473b-a6b9-d2a78f1b0e98" />


</p>
<p>
Changed the IP address to Google's IP address. 
</p>
<br />

<p>
<img width="813" height="557" alt="image" src="https://github.com/user-attachments/assets/03e24cb4-6893-4afe-b903-69e6e7ccb730" />


</p>
<p>
I opened client-1 and waited a couple minutes after changing the IP address on dc-1. I then pinged mainframe2 and the IP address came up as 8.8.8.8 as intended. I went back to dc-1 and quickly changed the IP address back to 10.0.0.4, then pinged it again on client-1. It still came up as 8.8.8.8, meaning the computer was relying on the local DNS cache rather than the true IP address. (reword)
</p>
<br />

<p>
<img width="1090" height="627" alt="image" src="https://github.com/user-attachments/assets/de24b817-0a54-44b5-aa4d-2719bca44871" />


</p>
<p>
I then opened Powershell again on client-1 as an admin. I used flushdns to clear the local DNS cache. I pinged mainframe2 after the flush and the IP address displayed correctly as 10.0.0.4.
</p>
<br />

<p>
<img width="977" height="657" alt="image" src="https://github.com/user-attachments/assets/ed74b9ba-a980-427a-ad76-42b5c33834a4" />


</p>
<p>
Created a new CNAME file in DNS manager for Google and named it search.
</p>
<br />

<p>
<img width="557" height="452" alt="image" src="https://github.com/user-attachments/assets/cd8fb64b-5582-4ce4-a1f8-1eb108826d41" />


</p>
<p>
I then pinged search on client-1 and found the IP address 142.250.68.36 (IP address for google.com). I also ran nslookup which displayed the 10.0.0.4 IP address as well as 172.217.14.100 (another IP address for Google). I finished by using the ipconfig /flushdns command. This concludes the DNS project.
</p>
<br />


