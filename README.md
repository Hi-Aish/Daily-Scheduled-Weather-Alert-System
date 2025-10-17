# Daily-Scheduled-Weather-Alert-System
Daily Scheduled Weather Alert System (n8n &amp; Docker). A containerized automation workflow that fetches real-time weather data and applies conditional logic to send a targeted Telegram alert every morning.
# 🚀 Level 1 Automation Project: Daily Scheduled Weather Alert System

This project demonstrates proficiency in setting up a self-hosted, event-driven workflow using n8n and Docker. The primary goal is to automate the delivery of essential weather information, applying conditional logic to only send an urgent alert when action (like carrying an umbrella) is required.

## 📌 Project Overview

| Component | Detail |
| :--- | :--- |
| **System Goal** | Deliver a daily, automated weather report to Telegram. |
| **Trigger** | Scheduled to run every morning. |
| **Target City** | Agartala, India |
| **Notification Channel** | Telegram Bot (`my_n8n_weather_alerts_bot`) |
| **Status** | Successfully deployed and running on a persistent Docker volume. |

## 🛠️ Skills and Concepts Demonstrated

This project showcases core foundational skills essential for any automation or DevOps role:

1.  **Containerization (Docker):** Demonstrated ability to deploy and manage the n8n application in an isolated environment using Docker and named volumes for data persistence (`n8n_data`).
2.  **Workflow Orchestration:** Implemented the **Schedule Node** to initiate the workflow at a fixed time (`08:00 AM` IST), ensuring reliable, time-based execution.
3.  **API Integration:** Successfully utilized the **HTTP Request Node** to connect with the external OpenWeatherMap API and fetch real-time, structured JSON data.
4.  **Conditional Logic:** Applied the **If Node** to create intelligent routing, checking the weather status (`$json.weather[0].main`) and executing two distinct paths:
    * **TRUE:** Execute an urgent "Rain Alert" message.
    * **FALSE:** Execute a "Normal Day" information message.
5.  **Data Transformation (Code Node):** Used custom **JavaScript** within the Code Node to clean, extract, and format raw JSON data into a clean, human-readable notification (`final_report`).
6.  **Secure Integration:** Established and used secure **Credentials** (Telegram Bot Token) to integrate the workflow with a private messaging service.

## ⚙️ Deployment Details

| Component | Value/Method |
| :--- | :--- |
| **Core Software** | n8n (Open-Source) |
| **Deployment Method**| Docker Container (Self-Hosted) |
| **Start Command** | `docker run -it --name n8n -p 5678:5678 -v n8n_data:/home/node/.n8n n8nio/n8n` |
| **API Used** | OpenWeatherMap |
| **Telegram Bot** | `@my_n8n_weather_alerts_bot` |
## 🖼️ Workflow Visualization

This visualization confirms the end-to-end flow from the initial time-based **Trigger** through the **API Integration** and final **Conditional Logic** pathing.

![n8n Workflow Canvas showing the scheduled weather alert process for Agartala.](![workflow_canvas_screenshot] https://github.com/user-attachments/assets/cd22cfe7-1020-490c-8716-9d1fcfbd8ee3
)

***Flow Legend:***
* **Green Path (True):** Executes the full "Rain Alert" message.
* **Blue Path (False):** Executes the standard "All Clear" message.
