# FLARE-VM Lab Setup for Malware Analysis

This repository documents the step-by-step process of setting up a FLARE-VM environment for reverse engineering and malware analysis. The lab involves configuring a Windows 10 virtual machine, disabling security features, and installing FLARE-VM using PowerShell scripts. The goal is to create an isolated environment for advanced cybersecurity operations.

## Table of Contents
1. [Lab Objectives](#lab-objectives)
2. [Tools and Resources](#tools-and-resources)
3. [Methodology](#methodology)
4. [Analysis and Findings](#analysis-and-findings)
5. [Challenges and Solutions](#challenges-and-solutions)
6. [Conclusion](#conclusion)
7. [Recommendations](#recommendations)
8. [References](#references)

---

## Lab Objectives
The primary objectives of this lab are:
1. Set up a Windows 10 virtual machine using VirtualBox.
2. Disable Windows Update and Windows Defender to ensure a smooth installation process.
3. Install FLARE-VM using PowerShell scripts.
4. Configure the virtual machine for isolated malware analysis.
5. Document the installation process, including challenges and solutions.

---

## Tools and Resources
- **VirtualBox**: A free and open-source virtualization tool used to create and manage virtual machines.  
  Download: [VirtualBox](https://www.virtualbox.org/wiki/Downloads)

- **Windows 10 ISO**: The operating system installed on the virtual machine.  
  Download: [Windows 10 ISO](https://www.microsoft.com/en-us/software-download/windows10)

- **FLARE-VM**: A collection of software installation scripts for setting up a reverse engineering environment.  
  GitHub Repository: [FLARE-VM](https://github.com/mandiant/flare-vm)

- **PowerShell**: A command-line tool used to execute the FLARE-VM installation script.

- **Guest Additions**: VirtualBox tools that enhance VM functionality, such as shared folders and full-screen mode.

---

## Methodology

### Step 1: Installation of Windows 10 in VirtualBox
1. **Download and Install VirtualBox**:  
   Download VirtualBox from the official website: [VirtualBox Download](https://www.virtualbox.org/wiki/Downloads).  
   Install it on your host machine.

2. **Download Windows 10 ISO**:  
   Download the Windows 10 ISO from the official Microsoft website: [Windows 10 ISO Download](https://www.microsoft.com/en-us/software-download/windows10).

3. **Create a New Virtual Machine**:  
   - Open VirtualBox and click on **New**.  
   - Set the name, select the folder, and choose the Windows 10 ISO file.  
   - Allocate at least **2 GB of RAM** and **60 GB of disk space**.  
   - Follow the setup wizard to install Windows 10 on the virtual machine.

   For detailed steps, refer to the uploaded document: [Lab Setup Document](#).

4. **Install Windows 10**:  
   - Boot the virtual machine and follow the Windows 10 installation prompts.  
   - Skip the product key step and select **Windows 10 Pro**.  
   - Complete the installation by setting up a user account and PIN.

---

### Step 2: Install Guest Additions
1. Insert the Guest Additions CD image from the VirtualBox menu:  
   - Click on **Devices > Insert Guest Additions CD Image**.

2. Install Guest Additions:  
   - Open the CD drive from File Explorer and run the installer.  
   - Follow the setup wizard to enable features like shared folders and full-screen mode.

---

### Step 3: Configure the VM
1. **Disable Windows Update**:  
   - Open the Local Group Policy Editor (`gpedit.msc`).  
   - Navigate to:  
     `Computer Configuration > Administrative Templates > Windows Components > Windows Update`.  
   - Double-click on **Configure Automatic Updates** and set it to **Disabled**.

2. **Disable Windows Defender**:  
   - Open Windows Security and turn off **Tamper Protection**.  
   - Use the Local Group Policy Editor to disable **Real-time Protection**:  
     `Computer Configuration > Administrative Templates > Windows Components > Microsoft Defender Antivirus > Real-time Protection`.  
   - Alternatively, use a third-party tool like **Defender Control** to disable Windows Defender permanently.

3. **Show Hidden Files and Extensions**:  
   - Open File Explorer (`Win + E`).  
   - Go to **View > Options > View tab**.  
   - Uncheck **Hide extensions for known file types** and select **Show hidden files, folders, and drives**.

4. **Reboot the Machine**:  
   - Restart the virtual machine to apply the changes.

5. **Take a Snapshot**:  
   - In VirtualBox, take a snapshot of the VM to save the current state.

---

### Step 4: Install FLARE-VM
1. **Open PowerShell as Administrator**:  
   - Search for PowerShell in the Start menu, right-click, and select **Run as Administrator**.

2. **Download the FLARE-VM Installation Script**:  
   Run the following command to download the script:  
   ```powershell
   (New-Object net.webclient).DownloadFile("https://raw.githubusercontent.com/mandiant/flare-vm/main/install.ps1", "$(Environment.GetFolderPath('Desktop'))\install.ps1")

3. **Unblock the Script**:
Run the following command to unblock the script:
Unblock-File .\install.ps1
Enable Script Execution:
Run the following command to enable script execution:

Set-ExecutionPolicy Unrestricted -Force
Run the Installation Script:
Execute the script:

.\install.ps1
Follow the Prompts:

##The installation process may take several hours depending on your network speed.

The VM will restart multiple times during the installation.

#Step 5: Post-Installation Configuration
Switch to Host-Only Networking:

Open VirtualBox and configure the VM's network adapter to Host-Only Networking to isolate it from the internet.

Take Another Snapshot:

Save the configured state by taking another snapshot in VirtualBox.

#Analysis and Findings
The installation of FLARE-VM was successful, and all tools were installed without errors. The virtual machine is now ready for reverse engineering and malware analysis. The isolation of the VM ensures that any malware analyzed will not affect the host system or external networks.

**Challenges and Solutions**
Challenge 1: Windows Defender blocked the installation script.

Solution: Disabled Windows Defender using a third-party tool (Defender Control).

Challenge 2: Network delays during the installation process.

Solution: Monitored the network and switched between networks as needed. Increased data allocation to accommodate the downloads.

#Conclusion
This lab provided a hands-on experience in setting up a FLARE-VM environment for malware analysis. The process highlighted the importance of isolating the analysis environment and disabling security features that could interfere with the installation. The skills gained in this lab are essential for advanced cybersecurity operations and threat intelligence.

#Recommendations
Regularly update the FLARE-VM tools to ensure compatibility with the latest malware samples.

Always use host-only networking to prevent accidental malware execution outside the lab environment.

Document any changes made to the VM for future reference.

#References
FLARE-VM GitHub Repository

VirtualBox Download

Windows 10 ISO Download

Lab Setup Document (Refer to the uploaded document for detailed steps and screenshots).

Copy

This updated `README.md` includes the command-line instructions, download links, and references to the uploaded document. You can now use this for your GitHub repository.
New chat


**Thank You so much for**
*Victoria Simon*
