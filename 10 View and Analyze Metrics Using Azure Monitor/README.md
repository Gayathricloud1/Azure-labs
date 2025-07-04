# Lab 10: View and Analyze Metrics Using Azure Monitor

## 🎯 Objective

This lab demonstrates how to view, analyze, and export real-time performance metrics (like CPU usage, disk I/O, and network traffic) for a Virtual Machine using Azure Monitor's Metrics Explorer. This is crucial for identifying system bottlenecks, proactive troubleshooting, and capacity planning.

---

## 🧠 Key Concepts

| Concept              | Description |
|----------------------|-------------|
| **Metric**           | Numerical data measured over time (e.g., CPU %, Disk IO). |
| **Metrics Explorer** | A visual tool in Azure Monitor to chart and analyze metrics. |
| **Scope**            | The Azure resource you’re monitoring (e.g., a VM). |
| **Aggregation**      | Summarization function (Average, Max, Min, Count). |
| **Chart Type**       | Format of data display – Line, Area, Bar. |

---

## 🧪 Prerequisites

- A running Virtual Machine in Azure (e.g., `azvm01`)
- Some usage history (CPU or disk/network activity) to visualize
- Azure Monitor (enabled by default for most services)

---

## 🪜 Steps Performed

### 🔹 Step 1: Access Metrics Explorer

1. Go to [Azure Portal](https://portal.azure.com)
2. Navigate to **Monitor** in the left pane
3. Select **Metrics** from the Monitor overview page

---

### 🔹 Step 2: Select the VM (Scope)

1. Click on **Select a scope**
2. Choose your target **Virtual Machine**
3. Click **Apply**

---

### 🔹 Step 3: Choose Metric and Aggregation

1. Under **Metric Namespace**, select `Virtual Machine Host`
2. Under **Metric**, choose `Percentage CPU`
3. Set Aggregation to `Average`
4. Choose a time range (e.g., **Last 24 hours**)

✅ This shows the CPU usage trend of the VM over time.

---

### 🔹 Step 4: Add More Metrics (Optional)

Click **+ Add metric** to compare:

| Metric                     | Use Case                          |
|----------------------------|-----------------------------------|
| Disk Read Bytes/sec        | Monitor disk read speed           |
| Disk Write Operations/sec  | Write performance issue tracking  |
| Network In Total           | Incoming network traffic          |
| Network Out Total          | Outgoing traffic & usage trends   |

---

### 🔹 Step 5: Customize the Chart

- Choose **chart type**: Line, Area, or Bar
- Use **Split by** for detailed breakdown (e.g., by NIC or core)
- Filter by **dimension** if multiple VMs/NICs are involved
- Change **time granularity** (1m, 5m, 1h, etc.)

---

### 🔹 Step 6: Export or Share

#### 🖼 Export as Image:
- Click **Download chart** (📥 icon) to export as `.png`

#### 📊 Pin to Dashboard:
- Click **Pin to dashboard** to view it persistently

#### 📁 View in Workbook (Optional):
- Click **“View in workbook”** for enhanced reporting and layout

---

## ✅ Output

- Charts of VM CPU, disk, and network usage over time
- Insight into usage trends and system behavior
- Option to share visuals with team or management

---

## 🔁 Use Case Scenarios

| Scenario                          | Metric to Use              |
|-----------------------------------|----------------------------|
| High CPU complaints               | `Percentage CPU`           |
| Disk performance troubleshooting  | `Disk Read/Write Bytes/sec`|
| Network issues                    | `Network In/Out Total`     |
| Memory monitoring (Linux VMs)     | `Available Memory Bytes`   |

---

## 📘 Interview Q&A

### 🔹 Q1: What is Azure Metrics Explorer?
> A tool in Azure Monitor that helps visualize and analyze metrics of Azure resources such as virtual machines, databases, and networks.

---

### 🔹 Q2: What is the difference between Metrics and Logs in Azure Monitor?

| Metrics (Numeric)              | Logs (Structured Text)                |
|-------------------------------|----------------------------------------|
| Near real-time (1-minute delay) | Delay of several minutes               |
| Short retention (93 days)      | Custom retention possible (up to 2 yrs)|
| Fast, lightweight              | Detailed, rich querying (KQL)          |

---

### 🔹 Q3: How would you monitor VM health in Azure?
> Use Azure Monitor to view CPU %, disk IO, and memory. Set alerts for thresholds. Pin charts to dashboards and enable diagnostic settings for logs.

---

## 🖼 Screenshots to Include (Optional)


---

## 📚 References

- [Azure Monitor Metrics Documentation](https://learn.microsoft.com/en-us/azure/azure-monitor/essentials/metrics)
- [Create and Analyze Metrics in Azure](https://learn.microsoft.com/en-us/azure/azure-monitor/visualize/tutorial-metrics-explorer)

---

## 📌 Summary Table

| Task                                  | Status |
|---------------------------------------|--------|
| Metrics visualized (CPU/Disk/Network) | ✅     |
| Chart customized and exported         | ✅     |
| Dashboard pinning                     | ✅     |
| Interview-ready                       | ✅     |

