### Explore Microsoft Defender XDR — SOC Analyst Fundamentals\

**Step 1 — Open Microsoft Defender XDR**

 I Open a **new browser tab**, and enter: [<u>https://security.microsoft.com</u>](https://security.microsoft.com) . I Sign in with my administrator account defenderadmin@... I successfully opened the **Microsoft Defender portal**. The message **“Your unified SIEM and XDR is ready”** confirms that my Microsoft Sentinel environment is integrated into the unified Defender experience. (Image 1)

**Step 2 — Expand the navigation menu**

I Click Show navigation.The complete Defender XDR navigation is now visible. This confirms that my tenant includes the unified Microsoft Sentinel and Defender experience.

The important SOC areas are:

**Exposure management:** Security posture, vulnerabilities, weaknesses, and recommendations.\
**Investigation & response:** Incidents, alerts, and investigation workflows.\
**Threat intelligence:** Information about threat actors, campaigns, indicators, and infrastructure.\
**Assets:** Devices, users, identities, applications, and other protected entities.\
**Microsoft Sentinel:** SIEM data, analytics, automation, workbooks, and configuration.\
**Email & collaboration:** Email threats and Microsoft Defender for Office 365.\
**Cloud security:** Cloud resources and workloads.\
**Advanced hunting:** KQL-based investigation across security data. (Image 2)


**Step 3 — Examine the incident workspace**

I Click the arrow beside Investigation & response to expand it. Investigation & response contains four groups:

### **Incidents & alerts:** SOC alert queue and correlated investigations.
**Hunting:** Proactive threat hunting using KQL.\
**Actions & submissions:** Response actions, automated investigations, and submitted files/URLs.\
**Partner catalog:** Integrated security products and services. (Image 3)\

**Step 4 — Open the incident options**

I Click the arrow beside **Incidents & alerts** to expand it. I will distinguish an **alert** from an **incident** before opening the queue.

**There are two primary SOC queues:**

**Alert:** One detection indicating potentially suspicious or malicious activity—for example, suspicious PowerShell execution or repeated failed sign-ins.\
**Incident:** A larger investigation case that correlates one or more related alerts, affected assets, users, evidence, and activity into a single attack story. A Tier 1 analyst usually begins with the Incidents queue, reviews its severity and evidence, determines whether it is a true or false positive, and then documents, escalates, or resolves it. (Image 4)\

**Step 5 — Open the incidents queue**

I Click **Incidents**. This is read-only exploration for now. The incident queue is working correctly. It currently shows 0 incidents, but that does not mean the portal is malfunctioning.\

The active view is limited by:

**Last update time:** 1 week\
**Status:** New and In progress\
**Severity:** High, Medium, and Low\
Informational or resolved incidents are excluded. The horizontally scrollable columns show the information analysts use for triage, including:

### Incident name and ID
Severity and priority\
Investigation state\
Categories and impacted assets\
Active alerts\
Detection/service source\
Assigned analyst\
Classification and determination\
Creation and update times\
Sentinel workspace (images 5, 6, 7, 8, and 9)\

**Step 6 — Examine the alerts queue**

I Click **Alerts**.The Alerts page is also functioning correctly and currently shows **0 alerts**.

That result is expected because:

No endpoint has been onboarded to Microsoft Defender for Endpoint yet.\
The current filter only includes **New** and **In progress** alerts.\
My tenant has not yet produced Defender XDR detections for endpoint, email, identity, or cloud activity.\
The columns demonstrate how alerts are triaged:

### **Alert name**
**Category**\
**Severity**\
**Status and investigation state**\
**Detection source and product**\
**Impacted assets**\
**First and last activity**\
**Classification and determination**\
**Assigned analyst**\
**Sentinel workspace** (Images 10, 11, and 12)\

**Step 7 — Explore protected assets**

I Click the arrow beside **Assets**.

**Assets** only contains:

**Cloud:** Inventory of discovered or connected cloud assets.
**AI agents:** Inventory and security visibility for AI agents.
There is currently no Devices option. This is expected because Microsoft Defender for Endpoint has not yet been provisioned and no endpoint has been onboarded. After the MDE setup and onboarding lab, the device inventory should become available, allowing analysts to inspect device risk, exposure level, health, logged-on users, alerts, and timelines. (Image 13)

**Step 8 — Explore the hunting workspace**

Under **Investigation & response**, I click the arrow beside **Hunting** to expand it. I will only inspect the hunting interface—no query is required yet.

The Hunting section contains:

**Advanced hunting:** Allows SOC analysts to run KQL queries across available Defender XDR and Microsoft Sentinel security data.\
**Custom detection rules:** Converts a tested hunting query into a recurring detection that can generate alerts automatically.

This is the important relationship:

**Advanced hunting query → suspicious results validated → custom detection rule → alert → incident** (Image 14)

**Step 9 — Open Advanced hunting**

I Click **Advanced hunting**. This is the unified **Advanced hunting** workspace.

The screen contains:

**Schema panel:** Lists searchable tables and their fields.\
**Query editor:** Where KQL hunting queries are written.\
**Run query:** Executes the query against selected security data.\
**Time range:** Currently set to the last seven days.\
**Result limit:** Currently set to 100,000.\
**Results:** Displays events returned by the query.\
**Query history:** Records previously executed queries.

The visible schema already includes tables for:

**Alerts & behaviors**
**Exposure Management**

After MDE onboarding, endpoint tables such as DeviceInfo, DeviceProcessEvents, DeviceNetworkEvents, DeviceFileEvents, and DeviceLogonEvents should become available. Those tables will support the later suspicious-process, PowerShell, malware, and device-timeline labs. (Image 15)

**Step 10 — Examine the Sentinel integration**

I Click the arrow beside **Microsoft Sentinel**. This confirms that Microsoft Sentinel is available directly inside the Defender portal. Its functions are grouped as:

**Search:** Search security data and entities.\
**Threat management:** Manage investigations, threat intelligence, analytics, hunting, and automation.\
**Content management:** Install and manage Sentinel solutions and security content.\
**Configuration:** Manage workspaces, data connections, retention, settings, and other SIEM components.

**Defender XDR** correlates detections across endpoints, identities, email, applications, and cloud services.\
**Microsoft Sentinel** adds SIEM capabilities, including broader log ingestion, analytics rules, automation, workbooks, and long-term investigation. The unified portal allows their alerts and incidents to be investigated from a common SOC queue. (Image 16)

**Step 11 — Inspect Sentinel threat-management tools**

I Click the arrow beside **Threat management** under Microsoft Sentinel.

The Sentinel **Threat management** section provides:

**Workbooks:** Interactive dashboards and visual reports.\
**Hunting:** Microsoft Sentinel hunting queries and investigation bookmarks.\
**Notebooks:** Advanced investigation using Jupyter-style notebooks.\
**Threat intelligence:** Manage indicators such as malicious IPs, domains, URLs, and file hashes.\
**MITRE ATT&CK:** View coverage of attacker tactics and techniques.

The Sentinel Hunting and Defender Advanced Hunting both use KQL, but they focus on different data:

**Defender Advanced Hunting:** XDR telemetry, such as endpoint processes, logons, files, networks, identities, and email.\
**Sentinel Hunting:** SIEM data ingested into the Log Analytics workspace from Microsoft and third-party sources.\
**Unified Advanced Hunting:** Can expose both types of data together when the required services, connectors, and permissions are available. (Image 17)

**Step 12 — Examine Sentinel content**

I Click the arrow beside **Content management**.\
Sentinel **Content management** contains:

**Content hub:** Install Microsoft and partner solutions containing data connectors, analytics rules, hunting queries, workbooks, and parsers. This is where the Microsoft Entra ID solution was installed earlier.\
**Repositories:** Connect source-control repositories to deploy and manage Sentinel content as code.\
**Community:** Access community-developed Sentinel detection and investigation content.

This is mainly a platform-engineering and SOC-content area rather than the daily Tier 1 alert queue, but analysts should understand where detections and workbooks originate. (Image 18)

**Step 13 — Examine Sentinel configuration**

I Click the arrow beside **Configuration**.

This is the main Microsoft Sentinel engineering and detection configuration area:

**Tables:** View collected data tables, retention, and storage settings.\
**Data connectors:** Connect Microsoft or third-party data sources to Sentinel.\
**Analytics:** Create scheduled or near-real-time rules that detect suspicious activity and generate alerts/incidents.\
**Summary rules:** Aggregate large datasets into smaller summarized tables.\
**Watchlist:** Import reference data such as high-risk users, privileged accounts, or suspicious IP addresses.\
**Automation:** Create automation rules and connect playbooks for response actions.

The complete flow is:

**Data connector → Sentinel table → analytics rule → alert → correlated incident → analyst investigation → automation/playbook response** (Image 19)

**Step 14 — Explore security posture**

I click **Exposure management** to expand it.

**Exposure management** is the proactive side of Defender security operations:

**Overview:** Organization-wide exposure and posture summary.\
**Secure now:** Prioritized actions that can reduce immediate risk.\
**Initiatives:** Tracks security objectives and improvement progress.\
**Recommendations:** Suggested configuration and remediation actions.\
**Attack surface:** Shows exposed assets, attack paths, and risk relationships.\
**Secure score:** Measures completion of recommended security controls.\
**Data connectors:** Connect sources used for exposure assessment.

The distinction is important:

- **Exposure management asks:** Where are we vulnerable before an attack?

**Incidents and alerts ask:** What suspicious or malicious activity is happening or has already happened? (Image 20)

**Step 15 — View the posture overview**

I Click **Overview** under Exposure management. This is safe, read-only navigation.

The Exposure Management page loaded partially. This is not a lab failure.

My tenant currently shows:

**Identity initiative:** 37%\
**SaaS initiative:** 42%\
**Endpoint, Cloud, and Code:** 0%\
**Patch and Mitigate cards:** Could not load\
**Fix:** No critical issues currently displayed

The missing Endpoint score is consistent with having no MDE-onboarded device. Some cards may also require additional licensing, connected data sources, or more time to calculate. (Image 21 and 22)\

This lab successfully covered:

Defender XDR portal access and navigation\
Security posture and Exposure Management\
Incidents versus alerts\
Incident and alert queues\
Asset inventory availability\
Advanced Hunting and its KQL workspace\
Sentinel threat management\
Sentinel content and configuration\
How Defender XDR and Sentinel operate together
