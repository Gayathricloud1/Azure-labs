# Lab 05: Create and Attach a Network Security Group (NSG)

## 🎯 Objective

The objective of this lab is to learn how to secure a virtual machine in Azure using a Network Security Group (NSG). The NSG will be used to control inbound traffic, specifically allowing RDP (Remote Desktop Protocol) to the VM from the internet.

---

## 🔧 Prerequisites

- A running virtual machine (VM) already created in Lab 4
- A custom virtual network and subnet available (created in Lab 3)
- Azure free account with active subscription
- VM is located in the same region as the NSG and subnet

---

## 🛠️ Step-by-Step Guide

### ✅ Step 1: Create a Network Security Group (NSG)

1. Log in to the Azure Portal: [https://portal.azure.com](https://portal.azure.com)
2. In the search bar at the top, search for **Network security groups**
3. Click **+ Create**
4. Fill in the following details:

| Field              | Value                   |
|-------------------|-------------------------|
| **Subscription**   | Free Trial              |
| **Resource Group** | `rg-azurelabs`          |
| **Name**           | `nsg-lab05`             |
| **Region**         | Same region as VM (e.g., Central India) |

5. Click **Review + Create**, then click **Create**

---

### ✅ Step 2: Add Inbound Rule to Allow RDP

1. Once the NSG is created, open it from the **"Network Security Groups"** blade
2. On the left panel, click **Inbound security rules**
3. Click **+ Add** and enter the rule details:

| Field                   | Value                   |
|-------------------------|-------------------------|
| **Source**              | Any                     |
| **Source port ranges**  | *                       |
| **Destination**         | Any                     |
| **Destination port**    | 3389                    |
| **Protocol**            | TCP                     |
| **Action**              | Allow                   |
| **Priority**            | 100                     |
| **Name**                | `Allow-RDP`             |

4. Click **Add** to save the rule

---


### ✅ Step 3: Associate the NSG with the Virtual Machine

> ℹ️ Note: You do **not need to stop the VM** to associate an NSG to an existing NIC. However, for **attaching or detaching a NIC**, the VM must be in a deallocated (stopped) state.

#### 🔗 3.1 Associate NSG to VM’s NIC

1. Go to **Virtual Machines** → Select your VM (e.g., `Lab4-VM`)
2. Click on the **Networking** tab
3. Click the name of the **Network Interface (NIC)** (e.g., `lab4-vm123-nic`)
4. In the left panel, select **"Network security group"**
5. Click **Associate**
6. In the popup:
   - Select your NSG (`nsg-lab05`)
   - Click **Save**

7. The NSG is now successfully associated while the VM is still running.

---

## 📸 Screenshot Suggestions

Save these images in your GitHub folder for Lab 05:
![NSG creation](./nsg-creation.png)
![inbouond rules creation](./inbound-rules.png)
![NSG association with vm throuhj NIC network interface](./nsg-associated-withvm.png)
- `nsg-created.png` → NSG Overview
- `nsg-rule.png` → Inbound rule created for port 3389
- `nsg-attached-to-nic.png` → Screenshot after associating with NIC

---

## 🧠 What I Learned

- What a Network Security Group (NSG) is and how it works
- Difference between inbound and outbound rules
- Why VM must be stopped before NIC-level association
- How to allow secure remote access (RDP) via NSG

---

## 📁 Folder Structure in GitHub

