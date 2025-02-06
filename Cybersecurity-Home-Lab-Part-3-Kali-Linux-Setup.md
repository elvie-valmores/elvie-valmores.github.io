# Cybersecurity Home Lab Part 3: Kali-Linux-Setup

## Objectives
In this module, the objective was to install and configure Kali Linux in VirtualBox. Kali Linux will serve as the management and attack VM for the lab, allowing interaction with other systems like pfSense and vulnerable machines in later modules.

### Skills Learned
- Downloading and configuring Kali Linux in VirtualBox.
- Setting up and organizing virtual machines using the grouping feature in VirtualBox.
- Configuring virtual network adapters and assigning them to the appropriate internal network.
- Performing a Kali Linux installation via graphical installer, selecting desktop environments.
- Basic Linux system management: setting hostnames, users, and passwords.
- Updating and upgrading a Linux system using command-line tools.
- Network troubleshooting: Verifying IP assignments and network connectivity within the lab environment.


## Steps
### Download Kali Linux
Download the 64-bit Recommended Installer. The image is ~4GB in size so it will take some time to download.
As of writing the latest version of Kali Linux is 2023.4.

![image](https://github.com/user-attachments/assets/66bf7ad4-c4a3-4894-b829-7824fd8ed654)

Once it is downloaded we should have an .iso file.

![image](https://github.com/user-attachments/assets/d3b886f0-1497-4479-9a1d-5ab9be446a2a)

### Kali Linux VM Creation
Launch VirtualBox. Select Tools from the sidebar and then click on New from the toolbar.

![image](https://github.com/user-attachments/assets/20cd4fd0-691f-4a86-9bd9-9ade7b21c9d3)

Give the VM a Name. Set the Folder option to the location where the Home Lab VMs are going to be saved. Leave the ISO Image option empty. Select Type as Linux and Version as Debian (64-bit) then click on Next.

![image](https://github.com/user-attachments/assets/d01cdd15-79ae-49f7-b4a1-3129e2345559)

Leave everything on its default values. Click on Next.

![image](https://github.com/user-attachments/assets/f933f9ab-2a0c-46e0-9d77-8d6c93005727)

Increase the Disk Size to 80GB and click on Next.

![image](https://github.com/user-attachments/assets/62dc6480-38ca-4c5d-babc-ac9a93ea64fc)

Ensure that all the settings look right and click on Finish.

![image](https://github.com/user-attachments/assets/66dee19a-ee9b-48ba-8bbe-7876753d9fc3)

![image](https://github.com/user-attachments/assets/483694df-b2f9-4f0e-9c70-4d49628fd5d6)

### Adding VM to Group
Right-click on the Kali Linux VM from the sidebar, select Move to Group -> [New].

![image](https://github.com/user-attachments/assets/49b93e72-6520-45c7-b766-9275e49dea61)

The VM will now be added to a Group called New Group. Right-click on the group name and select Rename Group. Name the group Management.

![image](https://github.com/user-attachments/assets/da2e0b61-377b-4783-ade5-a155b4e57cfd)

Select the Firewall and Management group (Ctrl+Click). Right-click on the name of one of the groups. From the menu select Move to Group -> [New].

![image](https://github.com/user-attachments/assets/bb3bd098-2e0e-4467-86a4-98ccc66499d3)

Now both the groups should be nested inside a group called New Group. Right-click on the group and choose Rename Group. Give the group the name Home Lab.

![image](https://github.com/user-attachments/assets/938c1af2-ff52-431a-8ba0-2ee1f420393a)

In the end, we should have the following structure:

![image](https://github.com/user-attachments/assets/0dfe1815-83ba-49fa-97de-ec842e096eab)

### Kali Linux VM Configuration
Select the Kali Linux VM and then from the toolbar select Settings.

![image](https://github.com/user-attachments/assets/00619e33-3fa6-4cc1-92a0-cdc0040b8b0c)

### System Configuration
Go to System -> Motherboard. For the Boot Order option ensure that the Hard Disk is on the top followed by Optical. Uncheck Floppy.

![image](https://github.com/user-attachments/assets/e75193bf-f606-4c8d-b501-b37cda187e18)

Go to System -> Processor. From Extended Features list select Enable PAE/NX.

![image](https://github.com/user-attachments/assets/0329802a-c8ea-491a-9eda-cdb72151aff5)

Go to Display -> Screen and increase the Video Memory to 128 MB.

![image](https://github.com/user-attachments/assets/e7be8f39-6018-489d-adb5-25570b00b7f9)

### Boot Image Configuration
Go to the Storage tab. Select the Empty disk present below Controller: IDE then click on the small disk icon on the right side of the Optical Drive option.

![image](https://github.com/user-attachments/assets/1dd0e76a-54cc-4d50-b0f8-7e7931b82c20)

Select Choose a disk file and then select the downloaded .iso file for Kali Linux.

![image](https://github.com/user-attachments/assets/2d2231b8-73a3-4a75-845b-7c4c9f89566d)

The final result should look as follows:

![image](https://github.com/user-attachments/assets/4a4ca555-aa96-49a2-b3f7-b46a1cb564ae)

### Network Configuration
Go to Network -> Adapter 1. For the Attached to field select Internal Network. For Name select LAN 0. Expand the Advanced section. For Adapter Type select Paravirtualized Network (virtio-net).

![image](https://github.com/user-attachments/assets/b3033adc-8684-463f-b387-bf3436ef7189)

### Kali Linux Installation
Remember to boot the pfSense VM if it was shut down before starting the Kali Linux installation.

Select Kali Linux from the sidebar and click on Start on the toolbar.

![image](https://github.com/user-attachments/assets/bce42d0e-e2ef-45d3-b504-c999ad1c7825)

From the Installer menu select Graphical Install.

![image](https://github.com/user-attachments/assets/22f9a70c-596d-4e8c-8f25-c2ac0ebfd17c)

Select your Language, location and keyboard layout.

![image](https://github.com/user-attachments/assets/c0c08305-01e4-489e-bf41-6850775880af)

Enter a name for the VM. You can use any name here. The hostname is used to identify the system on the network. The hostname can also be changed after installation.

![image](https://github.com/user-attachments/assets/7b7dc40b-be5b-4f7c-bdbe-4704f299124d)

Leave the domain name input blank and click on Continue.

![image](https://github.com/user-attachments/assets/67410a8f-a65f-42be-9ffd-6e127c16c5e2)

Enter your name. This name will be shown on the login screen.

The username is used to create the home directory for the user. All the user-related configurations are stored in this folder.

Enter a strong password. Re-enter the password in the second field and click on Continue.

![image](https://github.com/user-attachments/assets/41df60d7-74d1-42d3-b08d-b62387817d34)

Select your clock and then click on Continue.

Select the drive (sda) and click on Continue.

![image](https://github.com/user-attachments/assets/5736c975-2edb-453d-b9ef-bbb069c09a4e)

Select Guided — use entire disk and then click on Continue.

![image](https://github.com/user-attachments/assets/d79a9952-f584-44f5-9a01-f738fdf3218f)

Select the option: All files in one partition and click on Continue.

![image](https://github.com/user-attachments/assets/c3352095-0097-4500-ac49-a2c3fa6e63df)

Select Finish partitioning and write changes to disk. Then click on Continue.

![image](https://github.com/user-attachments/assets/1149dc72-41b5-4d44-9a20-2a5b32354742)

Select Yes and click on Continue.

![image](https://github.com/user-attachments/assets/7423f5a4-9cfc-42ec-8dfe-906f26248e73)

After the base system installation is complete we need to choose the desktop environment that will be installed. I have selected GNOME for installation.

The default is XFCE it does not look as pretty as GNOME it is much lighter and should have better performance. KDE Plasma is the fanciest with a lot of bells and whistles. I would only recommend KDE if you can assign 2 cores and 4GB RAM for this VM. Once the desktop environment is selected click on Continue.

![image](https://github.com/user-attachments/assets/0403e0f1-1919-499d-82cf-00eb54910784)

The installation will take some time. Select Yes and click on Continue.

![image](https://github.com/user-attachments/assets/8efc2267-c068-4305-8dca-8567d5e01640)

![image](https://github.com/user-attachments/assets/c34c4f82-2277-43da-92db-62a0736d1079)

Click on Continue to Reboot the system.

![image](https://github.com/user-attachments/assets/4648446d-c36c-410e-aa88-01c62eeae764)

After reboot, we should see the Login screen. Click Enter to log in. Enter the password that was configured during the installation.

### Post-Installation Configuration
Kali Linux installer can detect when it is run from a VM because of this it automatically installs Guest Addons.

Press Right Ctrl+F to enter Fullscreen mode. The VM should scale to fill the entire screen. Press Right Ctrl+F again to exit Fullscreen mode. From the dock at the bottom of the screen. Select the Terminal.

![image](https://github.com/user-attachments/assets/a96b09ea-9491-428e-ad8f-8b03afe852e2)

Run the command: ip a. We can see that the Kali VM has been assigned an IP address from the LAN network range. The VM should be able to access the internet as well.

![image](https://github.com/user-attachments/assets/0e4b2cad-54f5-4012-90b7-12242c333188)

Use the following command to update the system:

sudo apt update && sudo apt full-upgrade

Enter password when prompted.

![image](https://github.com/user-attachments/assets/d055c633-3bcc-4954-b0a4-cf6ce387a3cc)

Once the sources have been fetched we will be asked if we want to continue. Enter Y and then press Enter to start the update.

![image](https://github.com/user-attachments/assets/7bc058de-a032-4fc8-a6fe-3ad995d9c62e)

After the update is complete run the following command to remove the unused packages:

sudo apt autoremove

![image](https://github.com/user-attachments/assets/bc00ee12-4025-40ef-86cf-b311e7670465)

The .iso file that was downloaded to create the VM can be deleted now if you do not plan to store it for future use.
