<p align="center">
  <img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo" width="300"/>
</p>

# Active Directory Deployed in the Cloud (Azure)

This tutorial outlines the implementation of **Active Directory within Azure Virtual Machines**.

---

## 🛠️ Environments and Technologies Used

- Microsoft Azure (Virtual Machines / Compute)
- Remote Desktop
- Active Directory Domain Services (AD DS)
- PowerShell

---

## 💻 Operating Systems Used

- Windows Server 2022
- Windows 10 (21H2)

---


## 🚀 Deployment and Configuration Steps

### 🏢 Setup Domain Controller in Azure

1. **Create a Resource Group**  
2. **Create a Virtual Network and Subnet**  
3. **Create the Domain Controller VM**  
   - OS: *Windows Server 2022*  
   - Name: `DC-1`  
   - Username: `labuser`  
   - Password: `Cyberlab123!`
4. **Set Static Private IP Address**
   - After VM creation, go to DC-1's Network Interface Card (NIC) settings.
   - Set its Private IP address to **Static**.
5. **Disable Windows Firewall (For Testing)**
   - Log into DC-1 via Remote Desktop.
   - Open **Windows Firewall** and disable it to simplify connectivity testing.

---

### 💻 Setup Client-1 in Azure

1. **Create the Client VM**  
   - OS: *Windows 10*  
   - Name: `Client-1`  
   - Username: `labuser`  
   - Password: `Cyberlab123!`
2. **Attach to Same Region & Virtual Network**
   - Ensure Client-1 is in the **same Virtual Network and region** as DC-1.
3. **Configure DNS**
   - Set **Client-1’s DNS settings** to **DC-1's Private IP Address**.
4. **Restart Client-1 VM** via Azure Portal.
5. **Test Connectivity**
   - Log into Client-1.
   - Open Command Prompt or PowerShell.
   - Run:  
     ```powershell
     ping <DC-1 Private IP Address>
     ```
   - Ensure that the ping succeeds.
6. **Verify DNS Configuration**
   - In PowerShell, run:
     ```powershell
     ipconfig /all
     ```
   - Confirm that **DNS Server** shows **DC-1’s Private IP Address**.

---


### 📸 Screenshot Example

<p align="center">
  <img src="https://i.imgur.com/UO7qOgo.png" alt="Deployment Screenshot" width="800"/>
</p>

To start setting up your Active Directory, first create a Resource Group. Navigate to the Resource Groups section in the Azure portal and name your resource group. Next, select your region (it’s important that all your networks and machines remain in the same region). Once done, review and create the resource group, leaving the rest of the tabs at their default settings.

---

<p align="center">
  <img src="https://i.imgur.com/YgC0GuZ.png" alt="Deployment Screenshot" width="800"/>
</p>

We now need to set up a virtual network. Navigate to the 'Virtual Network' section in the Azure portal and choose the resource group you just created. Next, name your network and select the same region you chose earlier. Once done, review and create the network, leaving the rest of the tabs at their default settings.

---

<p align="center">
  <img src="https://i.imgur.com/O34GRur.png" alt="Deployment Screenshot" width="800"/>
</p>

Navigate to Virtual Machines to create your Domain Controller VM (Windows Server 2022). Select your existing Resource Group and name your server. Choose the same region you've been using previously. Ensure your image is set to Windows Server. Next, set up your account with a username and password, and review the licensing agreements.

---

<p align="center">
  <img src="https://i.imgur.com/ybwR7er.png" alt="Deployment Screenshot" width="800"/>
</p>

Navigate to your server’s network settings in the Azure portal. Select the network interface card (NIC), then select IP configurations. Here, set the private IP address to static. This will prevent conflicts if the IP address changes after a restart or update. Then, log into the Virtual Machine and temporarily disable the Windows Firewall while testing connectivity.

---

<p align="center">
  <img src="https://i.imgur.com/PCTtIxH.png" alt="Deployment Screenshot" width="800"/>
</p>

Follow the same Virtual Machine creation steps to create another virtual machine. Choose a different machine name, and use a standard Windows 10 image.

---

<p align="center">
  <img src="https://i.imgur.com/jteAWOT.png" alt="Deployment Screenshot" width="800"/>
</p>

Update this virtual machine’s (Client-1) DNS settings to use the private IP address of the server (DC-1). This will allow it to locate and connect to the Domain Controller. Restart the machine in the Azure portal to apply the changes.

---

**Test Connectivity**
   - Log into Client-1.
   - Open Command Prompt or PowerShell.
   - Run:  
     ```powershell
     ping <DC-1 Private IP Address>
     ```
   - Ensure that the ping succeeds.
**Verify DNS Configuration**
   - In PowerShell, run:
     ```powershell
     ipconfig /all
     ```
   - Confirm that **DNS Server** shows **DC-1’s Private IP Address**.

