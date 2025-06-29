# Lab 02: Create a Virtual Machine in Azure

## Objective
To deploy a Windows Server 2019 Virtual Machine in Azure using the Azure Portal.

## Prerequisites
- Active Free Trial Subscription
- Resource Group: `rg-azurelabs`

## Steps Followed

1. Navigated to **Virtual Machines** → Clicked **+ Create > Azure virtual machine**
2. Chose the following settings:

   - **Subscription**: Free Trial  
   - **Resource Group**: rg-azurelabs  
   - **VM Name**: AZSVM1 
   - **Region**: Central India  
   - **Image**: Windows Server 2019 Datacenter - Gen1  
   - **Size**: Standard B1s  
   - **Username**: DCMADMIN  
   - **Password**: Azure!nfra22  
   - **Inbound ports**: RDP (3389)

3. Clicked **Review + Create** → then clicked **Create**
4. Deployment completed in a few minutes
5. Viewed VM in **Running** state under "Virtual Machines"

## Screenshot(s)

- `vm-created.png`: Virtual Machine overview page
- `vm-status.png`: VM running with IP and RDP access

## What I Learned

- How to deploy a VM from Azure Portal
- The importance of selecting the correct VM size and image
- How Resource Groups help organize Azure services
- How to expose a VM to the internet securely using RDP (port 3389)

## Next Step

➡️ Proceed to [Lab 03: Create a Virtual Network](../03-VNet/README.md)
