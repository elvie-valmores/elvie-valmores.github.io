# Cybersecurity Home Lab Part 2: pfSense Setup and Configuration

## Objective
In this module, the objective was to install and configure pfSense as the gateway and firewall for the home lab. This setup ensures proper network segmentation and security controls, allowing for safe and organized testing of different components in the lab environment.

### Skills Learned
- Installation and configuration of pfSense as a network firewall.
- Creation and management of multiple virtual network interfaces.
- Setup of static IP addressing for lab subnets.
- Configuring DHCP services on specific network interfaces.
- Network troubleshooting and system initialization in VirtualBox.
- Understanding of basic network security principles and gateway management.


## Steps
### Download pfSense
Download pfSense and select the following settings:
Architecture: AMD64 (64-bit)
Installer: DVD Image (ISO) Installer
Mirror: Location closest to you

![image](https://github.com/user-attachments/assets/b03d5f02-8804-471f-bc88-2950de6daacc)

The downloaded file will have the extension .iso.gz. Use a decompression software like 7-Zip to extract the image.

![image](https://github.com/user-attachments/assets/a92ddaf2-6239-44f5-9a97-7b57a8cea1ff)

After extraction, we will have a file that has the .iso extension.

![image](https://github.com/user-attachments/assets/3c9303ce-42dd-4406-b6e5-959cb44f621f)

### pfSense VM Creation
Launch VirtualBox. Check on Tools from the sidebar and then Select New from the Toolbar.

![image](https://github.com/user-attachments/assets/3f18331b-6514-43eb-bbf4-1f433d038a52)

For Name, you can enter anything that makes sense. The Folder option defines the location where the VM will be saved. From the ISO Image dropdown select Others and select the .iso file that we just downloaded. Select Type as BSD and Version as FreeBSD (64-bit) and then click on Next.

Here we select the amount of RAM and CPU that the VM can use. No need to change anything. Click on Next to continue.

![image](https://github.com/user-attachments/assets/a66ae942-f4fe-43bf-8a4c-5c58b6c5128e)

On this page, we choose the amount of storage space to reserve for the VM. Enter 20GB in the input field.

![image](https://github.com/user-attachments/assets/8115d1dd-5db9-43d8-a751-e176b68c618b)

Confirm that everything looks right and then click on Finish. Once done we should see the newly created VM in the sidebar.

### Adding VM to Group
I like to keep my VMs organized by using the Groups feature of VirtualBox. This makes it easy to store related VMs together.

![image](https://github.com/user-attachments/assets/06faa707-564e-431b-9e7c-1ef3af06014b)

Right-click on the pfSense VM from the sidebar, select Move to Group -> [New]. The VM will now be added to a Group called New Group.

![image](https://github.com/user-attachments/assets/c6573083-15dc-421a-96d1-8d48a8a88e07)

Right-click on the Group, and select Rename Group. Name the Group Firewall.

![image](https://github.com/user-attachments/assets/160eb497-ae28-410b-b851-7b9ffcd32cf5)

The final result should match the following:

![image](https://github.com/user-attachments/assets/5abe6c35-25a3-41ae-94cb-4bd28cc20084)

Before we boot the VM we need to configure some settings related to VirtualBox. Select the pfSense VM from the sidebar and then click on Settings.

### pfSense VM Configuration
Before we boot the VM we need to configure some settings related to VirtualBox. Select the pfSense VM from the sidebar and then click on Settings.

![image](https://github.com/user-attachments/assets/b2f54311-6a4b-4c28-a8d4-fc1adc0b80be)

### System Configuration
Select System -> Motherboard in the Boot Order section use the arrows to move the Hard Disk to the top, Optical should be next. Ensure that Floppy is unchecked.

![image](https://github.com/user-attachments/assets/f7bd4614-f697-46d6-98cf-6a2c0f5b685d)

### Audio & USB Configuration
Go to the Audio tab and uncheck the Enable Audio option. Since the VM we are configuring is a router we do not need audio.

![image](https://github.com/user-attachments/assets/5c282898-2dd7-4c0f-9655-93ffbcdf3eaa)

Go to the USB tab and uncheck the Enable USB Controller option. Since the VM we are configuring is a router we do not need USB support.

![image](https://github.com/user-attachments/assets/4e495e22-4c2f-4483-9b95-43cd7a29d87a)

### Network Configuration
Go to Network -> Adapter 1. For the Attached to field select NAT. Expand the Advanced section and for Adaptor Type select Paravirtualized Network (virtio-net).

![image](https://github.com/user-attachments/assets/b9d6a3cf-884c-4d13-ba15-9734658befd2)

Select Adapter 2. Tick the Enable Network Adapter option. For the Attached to option select Internal Network. For Name enter LAN 0. Expand the Advanced section. For Adapter Type select Paravirtualized Network (virtio-net).

![image](https://github.com/user-attachments/assets/65835e18-9e2e-4b56-9b6e-ea4a17a4f88d)

Select Adapter 3. Tick the Enable Network Adapter option. For the Attached to option select Internal Network. For Name enter LAN 1. Expand the Advanced section. For Adapter Type select Paravirtualized Network (virtio-net).

![image](https://github.com/user-attachments/assets/39f59c28-192c-46b5-b84a-f708306c9e66)

Select Adapter 4. Tick the Enable Network Adapter option. For the Attached to option select Internal Network. For Name enter LAN 2. Expand the Advanced section. For Adapter Type select Paravirtualized Network (virtio-net).

Once done click on OK to save the changes and close the configuration menu.

![image](https://github.com/user-attachments/assets/8865ba3a-666e-40ba-8e7a-3df63a880c14)

### pfSense Installation
Select the pfSense VM from the sidebar and click on Start from the toolbar.

![image](https://github.com/user-attachments/assets/8261fd45-48dd-462b-8702-7f7b094d3908)

On boot, a banner will be shown followed by a lot of text. Wait for the below screen to appear. Press Enter to Accept the agreement.

![image](https://github.com/user-attachments/assets/21445a9a-38d6-4345-91ca-5b4f1d9aa53a)

Press Enter to start the Installation.

![image](https://github.com/user-attachments/assets/ffcfd6f7-41c2-48d0-955c-c3366290e3ff)

Press Enter to select the Auto (ZFS) partition option.

![image](https://github.com/user-attachments/assets/5e0a6a2f-6841-4fbf-8ef3-739d8c4dde2b)

Press Enter to select Proceed with Installation.

![image](https://github.com/user-attachments/assets/2af334ca-7b4e-4f3d-a653-89463c62349f)

Press Enter to select Stripe - No Redundancy.

![image](https://github.com/user-attachments/assets/175bfcd5-df3a-4f83-a43a-008592ea9d0a)

Use the Spacebar key to select the Hard Drive (ada0) then press Enter to continue.

![image](https://github.com/user-attachments/assets/9c5d5ed1-4b43-4e16-8505-e89f524a08f6)

Use the Left Arrow to select YES and then press Enter to continue.

![image](https://github.com/user-attachments/assets/dc94457d-ec6d-4792-9f71-82abcd87c7a5)

Press Enter to Reboot the VM.

![image](https://github.com/user-attachments/assets/d20aaa00-390f-45b6-8e8b-4138ed9f8d42)

### pfSense Configuration
Once pfSense reboots the first order of business is to onboard the adapters we configured in the VM settings.

Should VLANs be set up now? n
In the next step, we will configure the interfaces manually.

![image](https://github.com/user-attachments/assets/b09c203e-29e7-4783-a743-b731d1a0ce0a)

Enter the WAN interface name: vtnet0
Enter the LAN interface name: vtnet1
Enter the Optional 1 interface name: vtnet2
Enter the Optional 2 interface name: vtnet3

Do you want to proceed?: y

![image](https://github.com/user-attachments/assets/76ec3dda-4563-4174-aead-46b58b2809d0)

Since the WAN interface of pfSense is managed by VirtualBox it has been assigned an IPv4 address by the VirtualBox DHCP server. pfSense has also assigned an IPv4 address to the LAN interface using its DHCP service. The OPT1 and OPT2 interfaces have not been assigned any IP address. We do not want the IP addresses of the interfaces to change on boot so we will assign static IPv4 addresses to the LAN, OPT1 and OPT2 interfaces.

![image](https://github.com/user-attachments/assets/be37a721-a8c9-434c-90d7-89586169dac9)

### Configuring LAN (vtnet1)
Enter 2 to select “Set interface(s) IP address”. Enter 2 to select the LAN interface.

Configure IPv4 address LAN interface via DHCP?: n
Enter the new LAN IPv4 address: 10.0.0.1
Enter the new LAN IPv4 subnet bit count: 24

![image](https://github.com/user-attachments/assets/4f8e63cf-95e6-45a3-a1b8-3cf5e22e6f82)

For the next question directly press Enter. Since this is a LAN interface we do not have to worry about configuring the upstream gateway.

Configure IPv6 address LAN interface via DHCP6: n
For the new LAN IPv6 address question press Enter
Do you want to enable the DHCP server on LAN?: y
Enter the start address of the IPv4 client address range: 10.0.0.11
Enter the end address of the IPv4 client address range: 10.0.0.243
Do you want to revert to HTTP as the webConfigurator protocol?: n

![image](https://github.com/user-attachments/assets/1959c21c-50a5-43de-a3d3-ddbb5229a791)

pfSense will use the inputs we provided and configure the interface.
Press Enter to complete the LAN interface configuration.

![image](https://github.com/user-attachments/assets/84f43ea1-6b00-4829-8356-1e4307eb4955)

Once the changes apply we see that the IP address of the LAN interface has changed to the IP address that we provided.

![image](https://github.com/user-attachments/assets/b8fb47f2-d147-4b92-a265-c9418f38bc74)

### Configuring OPT1 (vtnet2)
Enter 2 to select “Set interface(s) IP address”. Enter 3 to select the OPT1 interface.

Configure IPv4 address OPT1 interface via DHCP?: n
Enter the new OPT1 IPv4 address: 10.6.6.1
Enter the new OPT1 IPv4 subnet bit count: 24

![image](https://github.com/user-attachments/assets/820aca7e-fdc0-47a4-a81e-7a08bf9823bd)

For the next question directly press Enter. Since OPT1 is a LAN interface we do not have to worry about configuring the upstream gateway.

Configure IPv6 address OPT1 interface via DHCP6: n
For the new OPT1 IPv6 address question press Enter
Do you want to enable the DHCP server on OPT1?: y
Enter the start address of the IPv4 client address range: 10.6.6.11
Enter the end address of the IPv4 client address range: 10.6.6.243
Do you want to revert to HTTP as the webConfigurator protocol?: n

![image](https://github.com/user-attachments/assets/89b2925d-569f-4a81-acdc-823eaef3013d)

Press Enter to save the changes and return to the main menu.

### Configuring OPT2 (vtnet3)
Enter 2 to select “Set interface(s) IP address”. Enter 4 to select the OPT2 interface.

Configure IPv4 address OPT2 interface via DHCP?: n
Enter the new OPT2 IPv4 address: 10.80.80.1
Enter the new OPT2 IPv4 subnet bit count: 24

![image](https://github.com/user-attachments/assets/2094eadc-3ae7-4671-8d81-f34804c42b04)

For the next question directly press Enter. Since OPT2 is a LAN interface we do not have to worry about configuring the upstream gateway.

Configure IPv6 address OPT2 interface via DHCP6: n
For the new OPT2 IPv6 address question press Enter
Do you want to enable the DHCP server on OPT2?: n
Do you want to revert to HTTP as the webConfigurator protocol?: n

![image](https://github.com/user-attachments/assets/8cc5d8df-508e-45cc-adb1-f2095bdfad86)

Press Enter to save the changes and return to the main menu.

The IP addresses for the LAN, OPT1 and OPT2 interfaces should be as follows:

![image](https://github.com/user-attachments/assets/624d028f-8232-4e98-bd22-42804ab74288)

With this, we have completed the onboarding of the interfaces in pfSense. There are additional settings that need to be configured. We will change these settings once we set up Kali Linux in the next module. From Kali Linux, we will access the pfSense Web Interface and proceed with the setup.

### Shutdown pfSense
When we start the lab pfSense is the first VM that has to be booted. When we shut down the lab pfSense will be the last VM that is stopped.

Enter a option: 6 (Halt system) Do you want to process?: y

This will initiate the shutdown sequence.

![image](https://github.com/user-attachments/assets/a17a1cf7-cb7f-4e1c-80c2-f6017a021610)

### Post-Installation Cleanup
After the VM is shut down. Click on Settings from the toolbar.

![image](https://github.com/user-attachments/assets/6283905c-756c-4d46-8185-619e6785924e)

Go to the Storage tab. In the Storage Devices section click on the pfSense .iso image then click on the small disk image on the right side of the Optical Drive option.

From the dropdown select Remove Disk from Virtual Drive. Click on OK to save the changes and close the configuration menu.

[Previous](https://github.com/elvie-valmores/Cybersecurity-Home-Lab-Part-1-Network-Topology)

[Next](https://github.com/elvie-valmores/Cybersecurity-Home-Lab-Part-3-Kali-Linux-Setup)
