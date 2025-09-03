# Infoblox Threat Defense with DDI SOAR Integration Playbooks

This directory contains playbooks designed to **automate security operations with Infoblox** on Splunk SOAR.  
These playbooks help security teams efficiently **block/unblock indicators**, perform **threat and asset lookups**, manage vulnerabilities, and **streamline incident response** workflows.

---

## Playbooks Overview

### 1. **Block Indicators**
- Automates adding domains or IPs to Infoblox default **block lists**.
- Ensures policy consistency by removing them from **allow lists**.

### 2. **Unblock Indicators**
- Automates adding domains or IPs to Infoblox default **allow lists**.
- Ensures policy consistency by removing them from **block lists**.

### 3. **IP Lookup**
- Enriches IP addresses with **Infoblox threat intelligence** and **asset data** for rapid security analysis.

### 4. **Host Lookup**
- Provides detailed host enrichment using Infoblox threat intelligence and asset information.

### 5. **URL Lookup**
- Performs deep context gathering and **threat assessment** for URLs using Infoblox **Dossier** and **TIDE APIs**.

### 6. **MAC Lease Lookup**
- Retrieves **MAC lease information** from Infoblox to add network context to security incidents.

### 7. **Vulnerability Management Scan**
- Triggers vulnerability scans based on security events enriched with Infoblox data.
- Adds a **note** in the event if the **threat level > 80**.

### 8. **Incident Response**
- Automates SOC workflows with **severity-based notifications** and **ServiceNow ticket creation**.
- If threat level is low, updates the event severity in SOAR accordingly.

---

## Basic Playbook Configuration in Splunk SOAR

The following configuration steps apply to **all playbooks**, with additional notes for specific ones.

---

### 1. **Importing and Selecting the Asset**
- After importing the `.tgz` playbook:
  - Open the **Playbook Editor**.
  - Locate the relevant **action block** (e.g., *Fetch Allow List*, *Fetch Block List*).
  - Under **Asset**, select the asset configured for **Infoblox Threat Defense with DDI**.

---

### 2. **Configuring Labels for SOC Insights Events**
- In the top-right corner of the Playbook Editor, click **Settings**.
- Locate **Operates On**.
- Select the label assigned to **SOC Insights** events to ensure the playbook runs only on relevant events.

---

### 3. **Vulnerability Management Scan (Automated Playbook)**
- Configure the **data path** from the artifact that will provide input.
- The playbook triggers automatically when a **new artifact** is created.
- To configure:
  - Open the **"Collect Indicator"** code block.
  - Update the parameter path to match the desired artifact field.
  - Save the playbook.

---

### 4. **Mark Playbook as Active**
- In Playbook **Settings**, toggle the **Active** switch to enable automated triggering.

---

### 5. **Input Playbooks (IP, Host, MAC, URL Lookups)**
- In the **Data Preview** panel (right side of Playbook Editor):
  - Select a manually created event in SOAR for testing.
  - Open the **Debugger** panel.
  - In **Test Inputs**, enter the indicator IP/MAC/URL/Host.
  - Click **Test**.
  - Check the selected event for playbook results.

---

### 6. **Block/Unblock Playbooks**
- In the **Data Preview** panel:
  - Select an existing or manually created SOAR event.
  - Click **Save and Run**.
  - When prompted on the event page, provide the indicator to be blocked/unblocked.
  - The playbook will execute on that event.

---

## Notes
- For **automated playbooks**, verify the **trigger conditions** (e.g., artifact creation).
- For **manual execution**, ensure the playbook is associated with the correct **event label**.
- Use **SOAR debug logs** for troubleshooting failed runs.

---
