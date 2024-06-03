# Active Directory Lab

## Objective

The primary objective of this lab was to gain hands-on experience in setting up and configuring Active Directory, thereby enhancing my understanding of its fundamental concepts and best practices for implementation

### Skills Learned

- Successfully deploying Active Directory, including setting up domain controllers, domains, and organizational units.
- Learning to create, modify, and manage user accounts and groups within Active Directory.
- Configuring Domain Name System (DNS) services within Active Directory to ensure proper name resolution and domain functionality.
- Developing skills in diagnosing and resolving common Active Directory issues, such as replication problems, DNS misconfigurations, and authentication failures.

### Tools Used

- Oracle Virtual Machine 
- Powershell
- windows server
- Windows 10
- Windows Command line 

## Steps
Here is an overview of the entire lab 
![Screenshot 2024-03-17 215820](https://github.com/Jpouncil23/Active-Directory-Lab/assets/163768012/bd3dca70-41e0-4201-b037-818f7ce94c5c)
In this screenshot, you can see that I have created 2 NICs. One is dedicated to the internet and the other to the internal network.
![VirtualBox_DC_02_06_2024_17_58_48](https://github.com/Jpouncil23/Active-Directory-Lab/assets/163768012/3f00606c-2c4c-4822-9346-7a2e993ad5a5)
Details on the changes made to the internal network
![VirtualBox_DC_02_06_2024_18_42_13](https://github.com/Jpouncil23/Active-Directory-Lab/assets/163768012/814886fc-82d9-4cb7-8d24-3f95ffc8974b)
Here I am installing the software for active directory domain services 
![VirtualBox_DC_02_06_2024_18_48_44](https://github.com/Jpouncil23/Active-Directory-Lab/assets/163768012/acd95b21-f3a6-4110-ae22-37f20ad4525d)
Here I have finished creating the domain and am ready to install
![VirtualBox_DC_02_06_2024_19_02_35](https://github.com/Jpouncil23/Active-Directory-Lab/assets/163768012/d28b79e7-4b01-4b27-810a-c992e43c6bfb)
once finished I then create an admin user 
![VirtualBox_DC_02_06_2024_19_27_13](https://github.com/Jpouncil23/Active-Directory-Lab/assets/163768012/77c24c89-a926-4391-a02d-aa698d1059cd)
Here I am configuring my RAS\NAT
![VirtualBox_DC_02_06_2024_19_35_34](https://github.com/Jpouncil23/Active-Directory-Lab/assets/163768012/ea842309-940c-4998-a723-090f0e365372)
![VirtualBox_DC_02_06_2024_20_02_31](https://github.com/Jpouncil23/Active-Directory-Lab/assets/163768012/44a2a0b0-adb6-484e-b3f2-29d9ba4a7eb6)
Here I am configuring my DHCP server 
![VirtualBox_DC_02_06_2024_20_09_06](https://github.com/Jpouncil23/Active-Directory-Lab/assets/163768012/ca1bd18f-0af3-4096-9a22-8d6189858f65)
![VirtualBox_DC_02_06_2024_20_14_26](https://github.com/Jpouncil23/Active-Directory-Lab/assets/163768012/8e7a0d46-5194-470b-88b6-68fa51cceba3)
using a PowerShell script I created I can use it to create a list of users on the directory 
![VirtualBox_DC_02_06_2024_20_40_59](https://github.com/Jpouncil23/Active-Directory-Lab/assets/163768012/a0479666-8acf-4df9-9e2d-a2876a3e6eef)
The results of running the script with a list of random users in the directory
![VirtualBox_DC_02_06_2024_20_45_49](https://github.com/Jpouncil23/Active-Directory-Lab/assets/163768012/9a5e32f7-87cb-446b-a80b-ea0b0415479f)
I am now on the Client1 VM and you can see that I am connected to the internal network and able to access the internet 
![VirtualBox_CLIENT1_02_06_2024_21_23_18](https://github.com/Jpouncil23/Active-Directory-Lab/assets/163768012/ba8b2b08-30e7-456b-9f90-542313173b17)





