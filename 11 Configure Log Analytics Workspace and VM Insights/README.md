# Lab 11: Configure Log Analytics Workspace and Enable VM Insights

## 🎯 Objective
This lab demonstrates how to create a **Log Analytics Workspace** and configure **VM Insights** for a virtual machine in Azure. The goal is to enable centralized monitoring, diagnostics, and performance analysis for virtual machines.

---

## 📘 Prerequisites
- Azure subscription (with permissions to create resources)
- At least one running Virtual Machine (Windows/Linux)
- Basic understanding of Azure Monitor and virtual machine structure

---

## 🧪 Lab Steps

### 🔹 Step 1: Create a Log Analytics Workspace
1. Go to the **Azure Portal**
2. Search for and select **"Log Analytics Workspaces"**
3. Click **+ Create**
4. Enter the following details:
   - **Subscription**: Select your active subscription
   - **Resource Group**: Create a new RG or select an existing one (e.g., `Monitoring-RG`)
   - **Name**: `MyLogAnalyticsWorkspace`
   - **Region**: Choose the same region as your VM (for performance)
5. Click **Review + Create** → then **Create**

---

### 🔹 Step 2: Enable VM Insights for a Virtual Machine
1. Navigate to **Virtual Machines** → Select your VM
2. Under the **Monitoring** section, click **Insights**
3. Click **Enable**
4. Choose the **Log Analytics Workspace** created earlier
5. Click **Enable** to start the configuration

⏳ This will install the **Log Analytics agent** (MMA/OMS) and optionally the **Dependency Agent**

---

### 🔹 Step 3: Verify Monitoring
After a few minutes:
- Go to the **Insights** blade of the VM
- View the following:
  - **Performance**: CPU, memory, disk, network metrics
  - **Map**: Real-time dependency map of connected processes/services

> 🔍 If the Map tab doesn't load, manually install the **Dependency Agent** from the Extensions section.

---

### 🔹 Step 4: Run Queries in Log Analytics
1. Go to the **Log Analytics Workspace** → Click **Logs**
2. Run sample queries like:

#### CPU Utilization Query:
```kusto
Perf 
| where ObjectName == "Processor" and CounterName == "% Processor Time"
| summarize AvgCPU = avg(CounterValue) by bin(TimeGenerated, 5m), Computer
| order by TimeGenerated desc
