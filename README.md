# 🧰 ServiceNow IT Helpdesk Ticketing System

A beginner-level **ServiceNow ITSM project** built to simulate a real-world Helpdesk environment.  
This system allows users to submit IT issues through the Service Catalog, automatically routes them to the correct team, tracks SLAs, and provides management dashboards for visibility.

---

## 🎯 Project Overview

This project was developed as part of a personal learning and capstone initiative to deepen my understanding of **ServiceNow fundamentals** — focusing on request management, automation, and reporting.

**Objective:**  
To create a simple yet functional IT Helpdesk system that demonstrates how ServiceNow’s key modules (Catalog, Flow Designer, SLAs, and Reporting) can work together to automate IT support.

---

## 🧾 Features & Functionalities

✅ **Submit IT Issue Catalog Item** — Users can submit issues specifying category, urgency, and description.  
✅ **Automated Assignment Flow** — Tickets are automatically assigned based on the selected category.  
✅ **SLA Rule (4 Hours)** — High-priority tickets escalate if unresolved within 4 hours.  
✅ **Email Notification** — Automatic email alert sent automatically to assigned based on the selected category and to the Escalation Team upon SLA breach.  
✅ **Dashboard Reporting** — Visual insights for open vs resolved tickets and SLA metrics.  
✅ **Work Notes Automation** — Logs key system updates automatically for transparency.

---

## ⚙️ System Components

| Component | Description |
|------------|-------------|
| **Service Catalog Item** | “Submit IT Issue” – Collects user input for category, urgency, and description. |
| **Record Producer** | Converts catalog submissions into Incident records. |
| **Flow Designer** | Automates ticket assignment and sends SLA breach notifications. |
| **SLA Definition** | Monitors time-to-resolution and triggers escalation if exceeded. |
| **Dashboard** | Displays ticket trends and SLA performance metrics. |

---

## 🧱 Architecture / Data Flow

1. **User Submission:**  
   End user submits an IT issue through the Service Catalog.

2. **Record Creation:**  
   Record Producer creates a new Incident in the `incident` table.

3. **Flow Execution:**  
   Flow Designer detects the category and assigns the ticket to the corresponding group.

4. **SLA Tracking:**  
   The SLA Definition applies time tracking and triggers escalation after 4 hours if breached.

5. **Notifications & Dashboard:**  
   Email alerts and real-time dashboards keep IT teams and managers informed.

---

## 🧩 Step-by-Step Configuration Summary

### 1️⃣ Create the “Submit IT Issue” Catalog Item
- Navigate to **Service Catalog > Maintain Items**.
- Create a new item named **Submit IT Issue**.
- Add variables:
  - Category (Choice)
  - Urgency (Choice)
  - Description (Multi-line text)
- Link to a **Record Producer** → target table: *Incident*.

### 2️⃣ Build the Auto-Assignment Flow
- Go to **Flow Designer > New Flow**.
- Trigger: *When Incident is created*.
- Add conditions for `Category`.
- Actions:
  - Set *Assignment Group* based on Category.
  - Send notification or log work notes.

### 3️⃣ Configure the SLA
- Go to **Service Level Management > SLA Definitions**.
- Name: *High Priority SLA (4 Hours)*.
- Condition: `Urgency = High`.
- Duration: 4 hours.
- Escalation Action: Notify *Escalation Team* and log breach in work notes.

### 4️⃣ Build Dashboard & Reports
- Go to **Performance Analytics / Dashboards**.
- Create:
  - “Open vs Resolved Tickets” bar chart.
  - “SLA Met %” KPI.
  - Optional: “Tickets by Category” breakdown.

---

## ⏱️ SLA Logic (Detailed)

| SLA Condition | Action |
|----------------|--------|
| `Urgency = High` | Apply SLA timer (4 hours). |
| `Resolved before 4h` | SLA marked as *Met*. |
| `Unresolved after 4h` | SLA marked as *Breached* → Triggers Flow → Sends email & adds note. |

---

## 📊 Dashboard Reporting

The dashboard provides:
- Real-time status of open vs resolved incidents.
- SLA metrics showing which tickets met or breached the time goal.
- Visual summary for IT managers to assess workload and performance.

---

## 🧪 Test Plan / Validation

| Test Case | Expected Result |
|------------|----------------|
| Submit a ticket (Normal urgency) | Creates a new Incident, assigned to proper group. |
| Submit a ticket (High urgency) | SLA starts (4-hour timer begins). |
| Let SLA breach | Escalation email sent, work note updated. |
| Resolve ticket | SLA stops, dashboard updates counts. |
| View Dashboard | Charts display correct data. |

---

## 🧠 Key Learnings

- How Service Catalog and Record Producers connect to backend tables.  
- How Flow Designer enables no-code automation for assignments and notifications.  
- How SLAs integrate into incident management for time-based tracking.  
- How to visualize KPIs and metrics through dashboards.  
- Importance of structuring ServiceNow objects logically to mirror ITSM workflows.

---

## 🚀 Future Enhancements
- Add **Knowledge Base linking** for common issues.  
- Expand **SLA tiers** (e.g., Medium = 8h, Low = 24h).  
- Implement **approval workflow** for change-type requests.  

**[Edgar Quindao Jr. ]** — Aspiring ServiceNow Developer | ITSM Enthusiast  
📧 Contact: [quindaoedgar122217@gmail.com]  
🔗 LinkedIn: [https://www.linkedin.com/in/edgar-quindao-jr-31a934301/]  
🔗 GitHub: [https://github.com/EdQuinJr] 


