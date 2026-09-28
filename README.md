# 🚀 GitTrack

GitTrack is a webhook-triggered GitHub activity tracker that monitors the GitHub activity of people you follow and notifies you about **new push events** through Gmail.

Instead of manually checking GitHub or repeatedly executing an n8n workflow, GitTrack allows the workflow to be triggered using a **Fetch Updates** button.

---

## 🎯 Problem Statement

When following multiple developers on GitHub, it can be difficult to keep track of their latest activity.

GitTrack automates this process by:

- Fetching the users you follow on GitHub
- Retrieving their recent GitHub activity
- Identifying push events
- Comparing events with the previous check
- Sending only new updates through Gmail
- Updating the last checked time after successful processing

---

## 🏗️ Architecture

```text
                 🔄 Fetch Updates
                       │
                       ▼
                🌐 Webhook
                       │
                       ▼
              👥 Get Following
                       │
                       ▼
             📡 Get GitHub Activity
                       │
                       ▼
              🔍 Filter PushEvents
                       │
                       ▼
               🕐 Get lastChecked
                       │
                       ▼
              🆕 Filter New Events
                       │
                       ▼
                 📧 Create Email
                       │
                       ▼
                    Gmail
                       │
                       ▼
                💾 Update State
