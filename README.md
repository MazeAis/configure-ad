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
  <img src="https://i.imgur.com/DJmEXEB.png" alt="Deployment Screenshot" width="800"/>
</p>

Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua...

---

<p align="center">
  <img src="https://i.imgur.com/DJmEXEB.png" alt="Deployment Screenshot" width="800"/>
</p>

Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua...

---

