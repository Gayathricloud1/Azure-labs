# Lab 08: Configure Azure Backup for a Virtual Machine

## 🧠 Objective
To enable backup protection for an Azure virtual machine using **Azure Backup** via a **Recovery Services Vault**, and understand how backup, retention, and restore processes work.

---

## 🛠️ Prerequisites

- A running Azure Virtual Machine (e.g., `azsvm2968_z1`)
- The VM should be in an accessible **resource group**
- The VM must be in a supported Azure region

---

## 🔹 Step 1: Create a Recovery Services Vault

1. Go to Azure Portal
2. Search for **Recovery Services vaults**
3. Click **+ Create**
4. Fill in the details:
   - **Name**: `manualbackupvalut`
   - **Subscription**: (same as VM)
   - **Resource Group**: `rg-azurelabs`
   - **Region**: Must match the VM's region (e.g., Central India)
5. Click **Review + Create**, then **Create**

> 📝 Screenshot Suggestion: Vault creation form filled

---

## 🔹 Step 2: Enable Backup for the Virtual Machine

1. Once the vault is deployed, open it
2. In the left menu, click **Backup**
3. Under "Where is your workload running?" → Select `Azure`
4. Under "What do you want to back up?" → Select `Virtual machine`
5. Click **Continue**
6. Click **+ Add** → Select your VM (e.g., `azsvm2968_z1`)
7. Click **Enable Backup**

> 📝 Screenshot Suggestion: VM selected in "Enable backup" wizard

---

## 🔹 Step 3: Configure the Backup Policy (Optional)

By default, Azure creates a daily backup policy:
- Time: 12:00 AM UTC
- Retention: 30 days

You can:
- Modify this policy later from the vault settings
- Create a **new policy** for different time/retention rules

---

## 🔹 Step 4: Trigger an On-Demand Backup (Manual Run)

1. Go to the vault → Click **Backup Items**
2. Click on **Azure Virtual Machine** → Select your VM
3. Click **Backup now**
4. Choose retention period (e.g., 30 days) → Click **OK**

> 📝 Screenshot Suggestion: Backup now window with retention picker

---

## 🔹 Step 5: Verify Backup Success

1. Go to the vault → Select **Backup Jobs**
2. Check the status:
   - **In progress** / **Completed**
3. You can also check:
   - Backup status = Healthy
   - Last Backup Time
   - Recovery points listed

> 📝 Screenshot Suggestion: Successful job completion and backup item health status

---

## 🔄 Restore Option (Optional Exploration)

- Go to the vault → Backup Items → Click VM → Click **Restore VM**
- Choose:
  - **Create new VM** from recovery point
  - Or **Replace existing VM**

---

## ✅ Outcome

- VM is now protected via scheduled backups.
- Manual backup was triggered and verified.
- Restore options are available in case of deletion or data loss.

---

## 📘 Interview Concepts Covered

| Topic | Covered in this Lab |
|-------|---------------------|
| Recovery Services Vault | ✅ |
| VM Backup Enablement | ✅ |
| Backup Policy & Retention | ✅ |
| On-demand Backup | ✅ |
| Backup Monitoring | ✅ |
| Recovery Point Restore | ✅ (optional test) |

---

## 🧪 Notes

- Azure Backup is incremental by default — only changes after first backup are stored.
- Soft-delete is enabled by default for VMs — backups are retained for 14 days even after deletion.
- You can also backup on-premises servers using MARS agent or MABS.

