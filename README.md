# Cloud Infrastructure Automation: Patch & Compliance Management via AWS SSM

## 📌 Project Overview
As an experienced Infrastructure Support Engineer transitioning to Cloud Operations, I built this hands-on laboratory to demonstrate how traditional enterprise systems patching workflows (such as WSUS, SCCM, and manual update management) translate directly into scalable cloud environments.

This project showcases the automated auditing of operating system compliance across a fleet of simulated enterprise virtual servers using **AWS Systems Manager (SSM) Patch Manager** and core **AWS EC2 Identity & Access Management (IAM)** security policies.

---

## 🛠️ Core Infrastructure Skills Demonstrated
* **Cloud Security (IAM):** Configured execution policies using `AmazonSSMManagedInstanceCore` roles to securely grant administrative access to target server nodes without distributing long-lived root keys.
* **Compute Provisioning (EC2):** Deployed multiple enterprise Windows Server 2022 nodes under free-tier resource boundaries.
* **Systems Administration & Operations:** Utilized cloud agent daemons (AWS SSM Agent) to manage state, networking, and platform endpoints.
* **Compliance Management:** Initiated immediate infrastructure-wide scanning tasks via `AWS-RunPatchBaseline` documents to flag missing patches and evaluate system health.

---

## 📐 Architecture & Execution Steps

### 1. Security & Identity Management (IAM)
Before launching infrastructure components, a secure identity profile named `EC2-SSM-Patching-Role` was initialized. This role grants the internal AWS Systems Manager daemon the precise privileges needed to interact with the virtual servers.

### 2. Node Provisioning & Fleet Registration
Two enterprise nodes (`Prod-Windows-Server-01` and `Prod-Windows-Server-02`) were launched as a mock production infrastructure cluster. By attaching our custom IAM role, both systems automatically checked into the centralized operational console.

<img width="975" height="444" alt="image" src="https://github.com/user-attachments/assets/994c7214-2ccd-43a8-9aa5-25cbe184bf01" />

<img width="975" height="442" alt="image" src="https://github.com/user-attachments/assets/54ce8c55-8cfb-40f2-aef7-2f355562a635" />

### 3. Automated Compliance Auditing
Using the AWS Patch Manager dashboard, an immediate, global scan operation was deployed across all running targets to check for missing operating system security updates. 

During the initial run execution, the command framework registered an execution log—demonstrating real-world cloud troubleshooting visibility when nodes interact with update paths.

<img width="975" height="264" alt="image" src="https://github.com/user-attachments/assets/0dabce52-ac39-4fca-87b1-859d036c0232" />

---

## 💡 Real-World Infrastructure Insights & Troubleshooting Takeaways
1. **Treating Infrastructure as Cattle:** During initial setup, one node faced an operating system communication delay registering with the SSM console. Instead of burning billable corporate hours performing traditional debugging on a clean launch, I leveraged standard cloud elasticity best practices: terminated the unresponsive node and spun up a fresh replacement instance which registered immediately.
2. **Operations Visibility:** Encountering an execution log check in a test laboratory is incredibly valuable. It simulates real-world infrastructure operations where network gateways or routing policies must be actively monitored to allow update packages to pass smoothly.
3. **Enterprise Transferability:** This cloud setup completely replaces manual patching schedules, replacing them with centralized compliance metrics and automated execution summaries.
