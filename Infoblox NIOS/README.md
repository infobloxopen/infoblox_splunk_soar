# Infoblox NIOS SOAR Integration Playbooks

This directory contains playbooks designed to automate **security operations** with Infoblox NIOS on Splunk SOAR.  
These playbooks enable SOC teams to efficiently **block/unblock indicators, enrich IOCs, perform asset lookups, and automate response workflows** with Infoblox DNS and DHCP data.  

---

## Playbooks Overview

### 1. Block Indicators
- Automates blocking of malicious domains and IPs in Infoblox **Response Policy Zones (RPZ)**.  
- Creates or updates RPZ rules to enforce blocking.  
- Ensures immediate containment during **threat hunting** or **incident response**.  

### 2. Unblock Indicators
- Automates removal of domains or IPs from Infoblox RPZ.  
- Cleans up previously blocked indicators after remediation or false positives.  

### 3. IP Lookup
- Enriches IP addresses with **IPAM and network context** from Infoblox.  
- Provides visibility into IP ownership, lease details, and related assets.  

### 4. Host Lookup
- Provides detailed **host enrichment** using Infoblox DNS and IPAM data.  
- Retrieves host records, associated IPs, DNS views, and attributes.  

### 5. MAC Lease Lookup
- Retrieves **DHCP lease information** from Infoblox based on MAC addresses.  

### 6. Bring Asset Data Back to Infoblox
- Automates creation of **host records** in Infoblox.  

---

## Basic Playbook Configuration in Splunk SOAR  

The following configuration steps apply to all playbooks, with notes for specific ones.  

### 1. **Importing and Selecting the Asset**
- After importing the `.tgz` playbook:
  - Open the **Playbook Editor**.
  - Locate the relevant **action block** (e.g., *Create Response Policy Zone*, *IP Lookup*).
  - Under **Asset**, select the asset configured for **Infoblox NIOS**.

### 2. **Mark Playbook as Active**
- In Playbook **Settings**, toggle the **Active** switch to enable automated triggering.

---

### 3. **Block / Unblock Playbooks**
- In the **Data Preview** panel:
  - Select an existing or manually created SOAR event.
  - Click **Save and Run**.
  - When prompted on the event page, provide the indicator to be blocked/unblocked.
  - The playbook will execute on that event.

### 4. **Input Playbooks (IP, Host, MAC, Asset Data)**
- In the **Data Preview** panel (right side of Playbook Editor):
  - Select a manually created event in SOAR for testing.
  - Open the **Debugger** panel.
  - In **Test Inputs**, enter the indicator IP/MAC/Host.
  - Click **Test**.
  - Check the selected event for playbook results.

---

## Notes  
- For **automated playbooks**, confirm trigger conditions (e.g., artifact creation).  
- For **manual execution**, ensure correct event label assignment.  
- Use **SOAR debug logs** for troubleshooting failures.  

---
