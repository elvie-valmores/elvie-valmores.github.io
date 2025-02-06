# Cybersecurity Home Lab Part 1: Network Topology

## Objective
The objective of Part 1 in the Cybersecurity Home Lab is to design and implement a robust network topology using VirtualBox. This serves as the foundation for the entire lab, which includes setting up VMs.

### Home Lab Overview
- **pfSense** (Gateway & Firewall): Acts as the main firewall and router for the lab network, ensuring that all VMs are securely managed.
- **Kali Linux** (Management VM): Used for administration and testing.
- **Active Directory Lab** (Domain Controller & 2 Clients): Provides the environment for managing and testing Windows services.
- **Malware Analysis Lab** (Windows & Linux): A separate environment for analyzing malware without risking the rest of the network.
- **Security VMs** (DFIR & SIEM): Dedicated virtual machines for Digital Forensics and Incident Response (DFIR) and Security Information and Event Management (SIEM).
- **Cyber Range** (Vulnerable VMs for CTF practice): Vulnerable virtual machines designed for Capture The Flag (CTF) practice and testing.

![image](https://github.com/user-attachments/assets/b209063b-f198-4095-b795-90747eb26962)


## Steps

### Downloading VirtualBox and Visual Studio
Download VirtualBox and VirtualBox Extension Pack.

![image](https://github.com/user-attachments/assets/aa76e46e-8df0-4830-bc51-660ec871197c)

After downloading VirtualBox, close the installer and download VC++ 2019 Redistributable.

![image](https://github.com/user-attachments/assets/877d528c-dcc5-4d15-be97-d3cb44272a48)

### Installing Visual Studio
The download will give us an .exe file. Double-click on it to launch the installer.

![image](https://github.com/user-attachments/assets/a1b08877-7533-4829-8cdf-aaa1d212e787)

Accept the agreement and click on Install.

![image](https://github.com/user-attachments/assets/28c7c8f0-ea7e-4661-af9a-be2f15378486)

### Installing VirtualBox
Click on the VirtualBox executable to start the setup. Click on Next to continue.

![image](https://github.com/user-attachments/assets/0af8fdc5-4c6e-41b1-89b8-5a5f3f935efd)

Leave all the settings on their default value and click on Next.

![image](https://github.com/user-attachments/assets/be45248e-3c5c-44e5-8331-3099b753962e)

Click on Yes.

![image](https://github.com/user-attachments/assets/bcdbc227-fd26-4a3d-b4c5-da1e4289e763)

Click on Yes.

![image](https://github.com/user-attachments/assets/7886a9ee-5e27-4762-82cb-d2af31ce08ed)

Click on Install.

![image](https://github.com/user-attachments/assets/c943a552-c115-413a-b554-26214bef2505)

Click on Finish to close the installer and start VirtualBox.

![image](https://github.com/user-attachments/assets/0104b68e-aae6-4e48-b458-261bc6cd3a76)

### Installing Guest Additions
From the File Menu bar select: File -> Tools -> Extension Pack Manager

![image](https://github.com/user-attachments/assets/43966f7c-dfb7-4e45-a52f-43f6be38afba)

On the Extension Manager page click on Install.

![image](https://github.com/user-attachments/assets/a1ed9d3d-e8b4-49b8-b4da-c7ac5960c73c)

Select the .vbox-extpack file that we downloaded. Click on Open.

![image](https://github.com/user-attachments/assets/79d9407f-ed7c-4dd3-8c1d-5fcc099f4070)

Click on Install to confirm the selection.

![image](https://github.com/user-attachments/assets/c86a1b03-bfed-4e5a-8924-cfeadadc2594)

Scroll to the bottom of the License and click on I Agree.

![image](https://github.com/user-attachments/assets/497efdb2-517b-4ac0-a1e5-6d6efcc12f00)

Once the installation is complete click on the Hamburger icon on the right-side of Tools and select Welcome.

![image](https://github.com/user-attachments/assets/5f56b143-25a4-4f09-8c5e-75f9f2756e8d)

From The File Menu bar select: File -> Preferences.

![image](https://github.com/user-attachments/assets/31eb3e4d-5bea-423c-9828-9648d5e6f90a)

### Changing VM Storage Location
From The File Menu bar select: File -> Preferences.

![image](https://github.com/user-attachments/assets/f52240e0-fd62-4315-9118-75d26ae46fb6)

From the General tab change the value of Default Machine Folder to change the default storage location of the VMs.

![image](https://github.com/user-attachments/assets/dec6a068-f615-4bff-a8ca-6744b4dbd7d2)























