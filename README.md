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

## 🚀 Deployment and Configuration Guide

### ⚙️ 1. Create Resource Group

<p align="center">
  <img src="https://i.imgur.com/UO7qOgo.png" alt="Resource Group Creation" width="800"/>
</p>

- Navigate to **Resource Groups** in the Azure portal.
- Click **Create** and name your resource group.
- Select your preferred region (ensure all future resources are in the same region).
- Click **Review + Create**, leaving other tabs at default settings.

---

### 🌐 2. Create Virtual Network

<p align="center">
  <img src="https://i.imgur.com/YgC0GuZ.png" alt="Virtual Network Setup" width="800"/>
</p>

- Go to **Virtual Networks** in the Azure portal.
- Select your resource group.
- Name your network and select the same region as before.
- Click **Review + Create**, using default settings for other tabs.

---

### 🏢 3. Deploy Domain Controller (DC-1)

<p align="center">
  <img src="https://i.imgur.com/O34GRur.png" alt="DC-1 Creation" width="800"/>
</p>

- Navigate to **Virtual Machines** to create your Domain Controller VM.
- Configuration:
  - OS: *Windows Server 2022*
  - Name: `DC-1`
  - Username: `labuser`
  - Password: `Cyberlab123!`
  - Region: Same as previous resources
- Ensure the image is set to **Windows Server**.
- Configure account credentials and accept licensing terms.

---

### 📡 4. Set Static Private IP for DC-1

<p align="center">
  <img src="https://i.imgur.com/ybwR7er.png" alt="Static IP Configuration" width="800"/>
</p>

- In the Azure portal, navigate to DC-1's **Networking** section.
- Select the network interface (NIC), then **IP Configurations**.
- Set the **Private IP address** to **Static**.
- Log into DC-1 via Remote Desktop.
- Temporarily disable the **Windows Firewall** for connectivity testing.

---

### 💻 5. Create Client-1 VM

<p align="center">
  <img src="https://i.imgur.com/PCTtIxH.png" alt="Client-1 Creation" width="800"/>
</p>

- Follow similar steps to create a second VM:
  - OS: *Windows 10*
  - Name: `Client-1`
  - Username: `labuser`
  - Password: `Cyberlab123!`
- Attach **Client-1** to the same **Virtual Network** and **region** as DC-1.

---

### 🛠️ 6. Configure DNS on Client-1

<p align="center">
  <img src="https://i.imgur.com/jteAWOT.png" alt="DNS Configuration on Client-1" width="800"/>
</p>

- Set **Client-1’s DNS settings** to the **Private IP Address of DC-1**.
- Restart Client-1 VM in the Azure portal to apply DNS settings.

---

### 🔍 7. Test Connectivity & Verify DNS

- Log into **Client-1**.
- Open **Command Prompt** or **PowerShell**.
- Run:
  ```powershell
  ping <DC-1 Private IP Address>

Ensure the ping succeeds.

Next, verify DNS configuration:
 ```powershell
ipconfig /all

