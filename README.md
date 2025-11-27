# Process Automation Task Tracker Project

## 📌 Overview
This project simulates a real-world environment where daily tasks, SLAs, staff workload, and automation rules need to be tracked.  
The dashboard is designed to help operations managers, executives, and coordinators monitor:

- Task status & priority distribution  
- Employee workload & productivity  
- SLA compliance and breaches  
- Process automation rules and escalation logic  
- Bottlenecks, delays, and overdue activities  

The entire solution is built in Power BI using a structured dataset of Tasks, Employees, and Automation Rules.

---

## 🎯 Objectives
- Provide daily operational insights for task tracking  
- Identify overdue and high-priority tasks  
- Track SLA vs. Actual time performance  
- Analyze workload distribution across staff  
- Monitor automation rules, SLA hours, and escalations  
- Improve productivity and flow of daily office operations  

---

## 📂 Dataset Structure

### **1. Tasks (220 rows)**
Includes all operational tasks:
- Task_ID  
- Task_Name  
- Category (Admin, Finance, HR, Customer Ops, General)  
- Priority (Low, Medium, High, Critical)  
- Assigned_To (Employee_ID)  
- Created_Date  
- Due_Date  
- Completed_Date  
- Status (Not Started, In Progress, Completed, Overdue)  
- Processing_Time_Hours (SLA/planned)  
- Actual_Time_Hours  

---

### **2. Employees (25 employees)**
Employee master data:
- Employee_ID  
- Employee_Name  
- Department  
- Role  
- Capacity_Per_Day  

---

### **3. Automation_Rules**
Simulated process automation logic:
- Rule_ID  
- Rule_Name  
- Applied_To_Category  
- SLA_Hours  
- Auto_Assign_To (Employee_ID)  
- Escalation_Level (None, Team Lead, Manager)  

---

## 🛠️ Tools Used
- **Power BI Desktop**
- **Power Query** (for cleaning and shaping data)
- **DAX Measures** for SLA % compliance, workload, and performance
- **Excel** dataset (manually designed + simulated rules)
- **Data Modeling** (Tasks ↔ Employees relationship)

---

## 🖥️ Dashboard Pages

### ⭐ **Page 1 — Operations Task Overview**
Provides a complete snapshot of daily task flow:
- Total Tasks, Completed, Pending, In Progress, Overdue  
- Tasks by Status (Donut Chart)  
- Tasks by Priority  
- Category distribution  
- Task Aging (Days overdue)  
- Full task detail table  

---

### ⭐ **Page 2 — Employee Workload & Productivity**
Focuses on team and individual efficiency:
- Total Employees  
- Tasks Assigned vs Completed  
- Avg Completion Rate  
- Overdue tasks by employee  
- Tasks per employee  
- Completion rates per employee  
- Employee performance table (KPI-rich)

---

### ⭐ **Page 3 — SLA & Automation Monitoring**
Highlights SLA compliance and automation behavior:
- SLA Compliance %  
- SLA Breaches  
- SLA Met  
- Avg SLA Overrun Hours  
- SLA breaches by Category & Priority  
- Automation Rules Overview  
- SLA Breach Detail Table  
- Optional trend line: SLA breaches over time  

---

## 🧮 Example DAX Measures
A few key DAX measures used:

'''DAX
Total Tasks = COUNTROWS(Tasks)

Completed Tasks =
CALCULATE(
    COUNTROWS(Tasks),
    Tasks[Status] = "Completed"
)

Overdue Tasks =
CALCULATE(
    COUNTROWS(Tasks),
    Tasks[Status] = "Overdue"
)

SLA Breaches =
CALCULATE(
    COUNTROWS(Tasks),
    Tasks[Actual_Time_Hours] > Tasks[Processing_Time_Hours]
)

SLA Compliance % =
DIVIDE([SLA Met], [Completed Tasks], 0)

Tasks Assigned =
CALCULATE(
    COUNTROWS(Tasks),
    ALLEXCEPT(Employees, Employees[Employee_ID])
)

Completion Rate =
DIVIDE([Tasks Completed], [Tasks Assigned], 0)

Avg Completion Rate =
AVERAGEX(
    VALUES(Employees[Employee_ID]),
    [Completion Rate]
)'''

------

**✨ What This Project Demonstrates**

Strong understanding of operational workflows

Ability to design multi-page analytical dashboards

SLA & productivity-based analytics

Process automation awareness

Real-world office/operations reporting capability
