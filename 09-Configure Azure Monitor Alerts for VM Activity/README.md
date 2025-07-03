# Lab 09: Configure Azure Monitor Alerts for VM Activity

## 🎯 Objective

Set up Azure Monitor to track virtual machine performance and availability, and configure **alerts** to notify when thresholds (e.g., high CPU usage, VM shutdown) are breached.

This enables Azure Administrators to detect and respond to issues proactively.

---

## 🧠 Key Concepts

- **Azure Monitor**: Platform for monitoring and collecting telemetry data from Azure and on-prem resources.
- **Metrics**: Numeric values (e.g., CPU, memory, network) collected at intervals.
- **Alerts**: Notifications or actions triggered by metric or log conditions.
- **Action Groups**: Notification system (email, SMS, webhook, etc.) associated with alert rules.

---

## 🪜 Step-by-Step Guide

### 🔹 Step 1: Open Azure Monitor

1. Sign in to [Azure Portal](https://portal.azure.com/)
2. Navigate to your **Virtual Machine** (e.g., 'AZSVM1`)
3. In the left pane, select **Monitoring → Alerts**
4. Click **+ Create Alert Rule**

---

### 🔹 Step 2: Define the Scope

- The **VM** you're working with will be selected automatically as the **scope**.
- You can monitor other resources too by changing the scope.

---

### 🔹 Step 3: Add a Condition

1. Click **Add Condition**
2. In the **Signal** list, search for: `Percentage CPU`
3. Set condition:
   - Operator: `Greater than`
   - Threshold: `80`
   - Aggregation: `Average`
   - Period: `5 minutes`
4. Click **Done**

✅ This will trigger the alert if CPU usage exceeds 80% for more than 5 minutes.

---

### 🔹 Step 4: Create an Action Group

1. Under **Actions**, click **+ Create action group**
2. Provide:
   - Action group name: `vm-alert-group`
   - Short name: `alertgrp`
3. Under **Notifications** tab:
   - Select **Email/SMS/Push/Voice**
   - Choose **Email** and enter your address
4. Click **Review + Create** → Then **Create**

---

### 🔹 Step 5: Configure Alert Details

1. **Alert rule name**: `High CPU Alert - azsvm2968_z1`
2. **Description**: Notify when CPU exceeds 80%
3. **Severity**: 2 (Critical), 3 (Warning), etc.
4. Check **Enable alert rule upon creation**
5. Click **Create**

---

## ✅ Result

- Alert is now **active**
- You'll receive an **email** when CPU exceeds 80% for 5+ minutes
- You can check **fired alerts** under Azure Monitor → Alerts → Alert History

---

## 🔁 Optional: Create Other Alert Rules

| Alert Type             | Signal / Metric        | Example Threshold         |
|------------------------|------------------------|---------------------------|
| VM Stopped             | Activity Log           | When `Status = Deallocated` |
| Disk Usage             | Logical Disk % Free    | Less than 15%             |
| Network Traffic        | Network In/Out Bytes   | More than 1 GB            |

---

## 📘 Interview Notes

### Q1: What is Azure Monitor?
> Azure Monitor is a built-in service for collecting, analyzing, and acting on telemetry from Azure resources and on-premises infrastructure.

---

### Q2: What are Action Groups?
> Action Groups are reusable notification objects that define what happens when an alert is triggered—like sending emails, SMS, or calling a Logic App or webhook.

---

### Q3: Difference Between Metrics and Logs?

| Metrics             | Logs                        |
|---------------------|-----------------------------|
| Numeric values       | Structured records           |
| Near real-time       | May take a few minutes       |
| Aggregated and fast  | Queryable via KQL            |
| Short retention (93d)| Long-term storage available  |

---

### Q4: When would you create an Alert on a VM?

- CPU > 90% for more than 5 minutes
- VM stopped unexpectedly
- Network spikes (possible DDoS or heavy traffic)
- Application not responding (via custom logs)

---

## 🧪 Verification

- Simulate CPU stress using a script (for test)
- Or manually Stop the VM and watch for deallocation alert (if created)
- Observe if the alert is triggered and email is received

---

## 📂 Screenshots to Include (Optional for GitHub)


---

## ✅ Summary

| Item                      | Status     |
|---------------------------|------------|
| Azure Monitor Alert Rule  | ✅ Created |
| Action Group              | ✅ Configured |
| Email Notification        | ✅ Received (test/real) |
| VM Scope + CPU Metric     | ✅ Monitored |


