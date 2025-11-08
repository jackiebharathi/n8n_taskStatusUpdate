# 📋 TaskStatusUpdate Automation (n8n Workflow)

This n8n workflow automates the **daily task collection and reporting** process using **Slack**, **Google Sheets**, **HTML-to-Image API**, and **Telegram**.

It performs the following steps automatically:
1. Sends **Slack reminders** to each team member to update their daily tasks.  
2. Collects their latest two Slack messages — *Planned Task* and *Task Status*.  
3. Updates the data into a **Google Sheet**.  
4. Generates a **professional HTML report**, converts it into an image, and  
5. Sends the report image to a **Telegram group or chat**.
<img width="702" height="193" alt="image" src="https://github.com/user-attachments/assets/f9c51e71-0e27-42d2-b7d3-3eaa565b3d11" />
<img width="1223" height="124" alt="image" src="https://github.com/user-attachments/assets/0f190f6c-1f65-46ff-9db7-9f353cbf218c" />

---

## 🚀 Features

- 🕒 Scheduled automation for weekdays (Mon–Fri)
- 💬 Slack reminders sent automatically
- 📥 Collects team task updates from Slack DMs
- 📊 Logs task data in Google Sheets
- 🖼️ Builds and converts a styled HTML report to an image
- 📤 Sends the report directly to Telegram

---

## 🧭 Workflow Overview

| Time (IST) | Action | Description |
|-------------|---------|-------------|
| 6:30 PM | 📨 Slack Reminder | Sends DM asking for planned and status updates |
| 8:00 PM | 🧩 Data Collection | Pulls latest two messages from each user’s DM |
| 8:05 PM | 📊 Report Generation | Updates Google Sheets and creates HTML |
| 8:10 PM | 📤 Telegram Delivery | Sends image report to Telegram chat |

---

## ⚙️ Tech Stack

| Tool | Purpose |
|------|----------|
| **n8n** | Workflow automation |
| **Slack API** | Task reminders and message retrieval |
| **Google Sheets API** | Data storage and reporting |
| **HCTI.io API** | HTML to Image conversion |
| **Telegram Bot API** | Final report sharing |

---

## 🧩 Node Summary

| Node | Purpose |
|------|----------|
| **Schedule Trigger1** | Starts reminder workflow at 6:30 PM |
| **Code (User List)** | Defines Slack user IDs and names |
| **Open Channel + Send Message** | Sends DM reminders |
| **Schedule Trigger** | Starts report workflow at 8:00 PM |
| **Code (Channel IDs)** | Defines Slack DM channels |
| **HTTP Request (Slack)** | Fetches the last two messages from each channel |
| **Code (Extract Messages)** | Extracts planned task and task status |
| **Slack (User Info)** | Fetches real names of users |
| **Merge** | Combines user details with messages |
| **Google Sheets (Clear + Update)** | Updates task data daily |
| **Code (HTML Report)** | Builds a formatted HTML task summary |
| **HTTP Request (HCTI.io)** | Converts HTML to an image |
| **HTTP Request (Download)** | Fetches the generated image |
| **Telegram (Send Photo)** | Sends image report with caption |

---

## 🧾 Google Sheet Format

| Column | Description |
|--------|--------------|
| **Date** | Current date (MM/DD/YYYY) |
| **Name** | User’s real name from Slack |
| **Planned Task** | The user’s planned activity |
| **Task Status** | The user’s latest progress or update |

The Google Sheet is refreshed daily with the latest task data.

---

## 🛠️ Setup Instructions

### 1️⃣ Requirements
- An **n8n instance** (self-hosted or cloud)
- **Slack Bot Token** with `conversations:history`, `users:read`, and `chat:write` scopes
- **Google Sheets API** credentials (OAuth2)
- **HCTI.io** account credentials
- **Telegram Bot Token**

---

### 2️⃣ Import Workflow
1. Download the `TaskStatusUpdate.json` file.  
2. In **n8n**, click **Import Workflow** → upload the file.  
3. Ensure all nodes are connected and visible in the editor.

---

### 3️⃣ Configure Credentials

| Credential | Used In | Details |
|-------------|----------|---------|
| **Slack API** | Slack nodes | Connect your Slack workspace |
| **Google Sheets OAuth2** | Sheets nodes | Link your Google account |
| **HTTP Basic Auth (HCTI)** | HCTI.io node | Use your HCTI user ID and API key |
| **Telegram API** | Telegram node | Use token from [@BotFather](https://t.me/BotFather) |

---

### 4️⃣ Update Key Values
- **Slack User IDs:** Update in “Code (User List)” node.  
- **Google Sheet ID:** Update in all Google Sheets nodes.  
- **Telegram Chat ID:** Update in “Send a photo message” node.

---

### 5️⃣ Activate Workflow
Enable both schedules:
- `Schedule Trigger1` → Runs at **18:30 IST** for Slack reminders.  
- `Schedule Trigger` → Runs at **20:00 IST** for data collection and reporting.

---

## 📸 Telegram Output Example

**Telegram Message Example:**
> 📊 *Daily Task Status Report*  
> *(Auto-generated at 8:10 PM)*  

![Example Report](https://via.placeholder.com/800x400?text=TaskStatus+Report+Preview)

---
### 🧩 Impact Story: Automated Daily Task Reporting System

**Context:**  
The team’s daily task updates were being manually collected from Slack and shared over messages, causing delays, inconsistent reporting, and limited visibility for leadership.

**Action:**  
Designed and implemented an **end-to-end automated task reporting system** using **n8n**, integrating **Slack**, **Google Sheets**, **HCTI.io**, and **Telegram**.  
The workflow automatically sends Slack reminders, collects each team member’s task updates, generates a structured HTML report, converts it into an image, and delivers it to Telegram — completely removing manual intervention.

**Impact:**  
- ⏱️ **100% reduction in manual reporting time** (from ~30 mins/day to 0).  
- 📊 **Real-time visibility** for managers with automated daily summaries.  
- ✅ **Improved task submission compliance** (from ~60% to 95%).  
- 🔁 **Consistent daily data records** maintained in Google Sheets.  
- 🧠 Enabled **data-driven tracking** of team productivity and accountability.

**Result:**  
The automation eliminated repetitive follow-ups and manual collation, improving delivery coordination and saving approximately **2.5 hours per week** for both analysts and reporting managers.
