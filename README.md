# Cyber-Portfolio
This repository documents my journey of becoming a cybersecurity professional. My philosophy is to Build, Break, Defend, Automate, and Evolve.
**Motto: Build. Break. Defend. Automate. Evolve.**

-----

## Core Projects & Skills

* **[SentinelWorks: Hybrid Threat Observatory](./sentinel-works/)**: A hybrid on-prem + AWS SIEM that ingests real-world telemetry, runs custom detection rules, and automates triage workflows.
* **[Terraform Fortress: Secure IaC Framework](./terraform-fortress/)**: A modular IaC framework that deploys a secure cloud environment with policy-as-code enforcement and automated remediation.
* **[Neural Sentinel: AI for Security (AI4Sec)](./ai-security-projects/)**: Experiments in using Machine Learning for threat detection, including a deployed phishing classifier and log anomaly detection pipeline.
* **[AegisScan: Cloud Security Auditor](./aegis-scan/)**: An automated multi-account cloud risk auditor that generates prioritized remediation playbooks.
* **[ReconKit: Operator Suite](./toolkit-reconkit/)**: A collection of Python scripts I built for automation in both offensive and defensive tasks.


* **[Quarterly Reflections](./reflections/)**: My thoughts and learnings at the end of each quarter.
* **[Lab Environments](./lab-setup/)**: Documentation for my on-premise and cloud lab setups.

-----

## **Project Blueprints**

#### **Project 1: ReconKit (Operator Suite)**

  * **Resume Blurb:** "Built ReconKit, a hybrid C/Python operator suite that automates reconnaissance, aggregates findings into a standardized evidence pipeline, and integrates directly with my hybrid SIEM for automated hunting and reporting."
  * **Core Objective:** Create a personal, evolving toolkit that demonstrates your scripting and automation skills. This is not a single project but a continuous one.
  * **What You Need To Do:**
    1.  **Start Simple:** Begin with basic Python scripts for individual tasks (header fetching, log parsing, nmap automation).
    2.  **Evolve into a Toolkit:** As you learn, refactor these standalone scripts into a single, modular command-line tool.
    3.  **Integrate and Automate:** Have the toolkit's output (e.g., scan results) automatically feed into your SentinelWorks SIEM to trigger alerts.
    4.  **Add a Performance Edge (The Twist):** For a specific, performance-critical module (like a port scanner), try rewriting it in a lower-level language like C or Rust and have your main Python tool call it. This shows deep systems-level understanding.

#### **Project 2: SentinelWorks (Hybrid Threat Observatory)**

  * **Resume Blurb:** "Designed and implemented SentinelWorks, a hybrid on-prem + AWS SIEM that ingests honeypot-captured adversary telemetry, runs automated triage workflows, and reduced simulated Mean Time to Detection (MTTD) by 60% in controlled experiments."
  * **Core Objective:** Build a SIEM that not only collects logs but also uses real-world attack data to create high-fidelity detections and automates the initial stages of incident response.
  * **What You Need To Do:**
    1.  **Build the Base:** Deploy Wazuh/Security Onion in your virtual lab.
    2.  **Integrate All Sources:** Configure log shipping from your Windows, Linux, and AWS (CloudTrail) environments.
    3.  **Add Real-World Data (The Twist):** Deploy a simple, publicly accessible honeypot (e.g., a vulnerable web server) for 1-2 weeks. Capture the logs of real attackers.
    4.  **Detection Engineering:** Analyze the honeypot logs to identify attacker TTPs. Write specific Sigma or Wazuh rules to detect this exact activity.
    5.  **Automate Triage:** When one of your custom rules triggers an alert, have it automatically execute a script that gathers more information from the "compromised" host (e.g., run `osquery`) and post a summary to a Discord/Slack webhook.
    6.  **Measure and Document:** Simulate the attacks from your honeypot in your lab. Measure the time it takes for your system to detect and alert (MTTD). Document the entire process in a detailed case study.

#### **Project 3: Terraform Fortress (Secure IaC Framework)**

  * **Resume Blurb:** "Developed Terraform Fortress, a modular IaC framework that deploys a secure AWS environment and enforces runtime security policies via policy-as-code (Open Policy Agent) and automated remediation hooks."
  * **Core Objective:** Go beyond just building infrastructure. Create a framework that *enforces* security and can automatically fix certain misconfigurations.
  * **What You Need To Do:**
    1.  **Build the Secure Baseline:** Write Terraform modules to deploy a secure VPC, logging stack, and EC2 instances.
    2.  **Add Policy-as-Code (The Twist):** Integrate Open Policy Agent (OPA). Write policies that prevent insecure configurations *before* they are deployed (e.g., a policy that blocks security groups from allowing port 22 open to the world).
    3.  **Automated Remediation:** Create an AWS Lambda function that is triggered by an event (e.g., AWS Config detects a public S3 bucket). This Lambda should automatically change the bucket's policy back to private.
    4.  **Test and Validate:** Use a testing framework like `terratest` to write automated tests for your Terraform modules.
    5.  **Document with Diagrams:** Create a high-quality architecture diagram showing how all the components interact.

#### **Project 4: Neural Sentinel (AI for Security)**

  * **Resume Blurb:** "Built Neural Sentinel, a deployed phishing-classifier microservice (AUC 0.98) and a log anomaly detection pipeline trained on lab SIEM logs; includes explainability dashboards (SHAP) and adversarial robustness tests."
  * **Core Objective:** Demonstrate a deep, practical understanding of applying ML to security, including model evaluation, deployment, and an understanding of its limitations.
  * **What You Need To Do:**
    1.  **Build the Phishing Classifier:**
          * Train two models: a simple baseline and a more advanced one (e.g., a small transformer).
          * **Add Explainability (The Twist):** Use SHAP or LIME to create visualizations that show *why* your model flagged an email as phishing.
          * **Deploy it:** Wrap your model in a simple Flask/FastAPI microservice.
    2.  **Build the Log Anomaly Detector:**
          * Use the logs from your SentinelWorks project.
          * Apply an anomaly detection algorithm to find unusual events.
          * Validate it by showing that your model successfully flags a simulated attack.
    3.  **Test for Robustness:** Craft simple adversarial examples and document how they affect your model's performance.
    4.  **Document in Jupyter Notebooks:** Present both experiments in clean, well-documented Jupyter Notebooks.

#### **Project 5: AegisScan (Cloud Security Auditor)**

  * **Resume Blurb:** "Created AegisScan, an automated multi-account cloud risk auditor that generates prioritized remediation playbooks and integrates findings into an enterprise SIEM pipeline."
  * **Core Objective:** Build a tool that demonstrates your ability to scale security auditing across an enterprise-level cloud environment.
  * **What You Need To Do:**
    1.  **Build the Core Scanner:** Write a Python script using `boto3` that scans for a variety of common misconfigurations (public S3 buckets, overly permissive IAM policies, unencrypted EBS volumes, etc.).
    2.  **Implement Multi-Account Scanning (The Twist):** Architect the tool to use AWS IAM Roles to scan multiple AWS accounts from a central security account, mimicking a real enterprise setup.
    3.  **Generate Actionable Reports:** Have the tool output a prioritized report (e.g., a PDF or HTML file) that not only lists the findings but also provides code snippets for remediation (e.g., the correct IAM policy JSON).
    4.  **Integrate with SIEM:** Configure the scanner to run on a schedule (e.g., as a daily Lambda function) and send its findings as alerts to your SentinelWorks SIEM.

---

## 🚀 Core Projects & Skills

Each project below explores a different layer of the security stack — from automation and AI to detection engineering and secure infrastructure design.

* **[SentinelWorks: Hybrid Threat Observatory](./sentinel-works/)**
  A hybrid on-prem + AWS **SIEM** environment that ingests real-world telemetry, runs custom **detection rules**, and automates triage workflows.

* **[Terraform Fortress: Secure IaC Framework](./terraform-fortress/)**
  A modular **Infrastructure-as-Code** framework that enforces security through **policy-as-code** and **automated remediation**.

* **[Neural Sentinel: AI for Security (AI4Sec)](./ai-security-projects/)**
  Experiments in **Machine Learning for threat detection** — including a deployed **phishing classifier** and **log anomaly detector**.

* **[AegisScan: Cloud Security Auditor](./aegis-scan/)**
  A **multi-account AWS risk auditor** that automates cloud misconfiguration scanning and generates prioritized remediation playbooks.

* **[ReconKit: Operator Suite](./toolkit-reconkit/)**
  My personal toolkit of **Python scripts** and **C modules** for automating both offensive and defensive security workflows.

* **[Quarterly Reflections](./reflections/)**
  Long-form writeups where I document lessons learned, mistakes made, and insights gained each quarter.

* **[Lab Environments](./lab-setup/)**
  Documentation for my virtual and cloud-based lab setups used throughout these projects.

---

## 🧩 Project Blueprints

### 🛠️ ReconKit (Operator Suite)

A continuously evolving operator toolkit built from scratch to automate reconnaissance, parsing, and evidence collection.

**Goal:** Develop a hybrid C/Python automation suite that demonstrates scripting, modularity, and system-level understanding.

**Next Milestones:**

* Start with simple Python scripts (`header_fetch`, `log_parser`, `nmap_automator`)
* Refactor into a single CLI tool
* Integrate outputs into the SentinelWorks SIEM
* Rewrite one performance-critical module (e.g. port scanner) in C or Rust

---

### 🛰️ SentinelWorks (Hybrid Threat Observatory)

A real-world **SIEM and detection lab** that uses honeypot data to engineer high-fidelity detection rules.

**Goal:** Build a hybrid SOC environment, collect real adversary telemetry, and measure your detection pipeline performance.

**Core Steps:**

* Deploy **Wazuh/Security Onion**
* Integrate logs from Windows, Linux, and AWS
* Deploy a **honeypot** and capture real attacker traffic
* Write **Sigma/Wazuh** rules for attacker TTPs
* Automate triage with Discord/Slack alerting
* Measure **Mean Time to Detection (MTTD)** and document

---

### 🧱 Terraform Fortress (Secure IaC Framework)

A cloud automation system that builds security *into* the infrastructure.

**Goal:** Create modular, secure Terraform templates with real-time enforcement and self-healing policies.

**Core Steps:**

* Deploy secure AWS baseline (VPC, EC2, logging stack)
* Enforce **Open Policy Agent (OPA)** rules before deployment
* Automate misconfiguration fixes with **AWS Lambda**
* Test infrastructure using **Terratest**
* Create diagrams and documentation

---

### 🧠 Neural Sentinel (AI for Security)

A showcase of **AI applied to cybersecurity**, blending ML experimentation with explainability and deployment.

**Goal:** Use ML to identify phishing and anomalies within SIEM data — with transparency and robustness testing.

**Core Steps:**

* Train and compare phishing classifiers
* Add **SHAP/LIME** explainability
* Deploy with **Flask/FastAPI**
* Build log anomaly detector using real SIEM data
* Test adversarial robustness and document results

---

### ☁️ AegisScan (Cloud Security Auditor)

An automated **multi-account AWS security scanner** that mirrors enterprise-scale auditing.

**Goal:** Demonstrate scalable cloud security automation and continuous compliance monitoring.

**Core Steps:**

* Build a `boto3`-based scanner for AWS misconfigurations
* Implement **multi-account scanning** using IAM roles
* Generate detailed, actionable HTML/PDF reports
* Integrate with SIEM for scheduled alerts

-----

### **24-Month Roadmap**

**Year 1: The Purple Team Apprentice**

  * **Month 1 (Oct 2025):** CEH Theory, Lab Foundation & **Project 1 (ReconKit)** Kick-off
  * **Month 2 (Nov 2025):** CEH Theory & ReconKit Evolution
  * **Month 3 (Dec 2025):** CEH Theory, Practical Tools & Reflection
  * **Month 4 (Jan 2026):** CEH Final Theory & Prep
  * **Month 5 (Feb 2026):** CEH Labs & **Project 2 (SentinelWorks)** Kick-off
  * **Month 6 (Mar 2026):** CEH Labs, Log Collection & Reflection
  * **Month 7 (Apr 2026):** CEH Final Labs & SentinelWorks Integration
  * **Month 8 (May 2026):** Exam Month & First Red Team Weekend
  * **Month 9 (Jun 2026):** Cloud Networking & **Project 3 (Terraform Fortress)** Kick-off
  * **Month 10 (Jul 2026):** Build Secure Cloud Network with Terraform
  * **Month 11 (Aug 2026):** Deploy Server & Connect Cloud to SIEM
  * **Month 12 (Sep 2026):** Detection Engineering & Year-End Review

**Year 2: The AI-Powered Security Specialist**

  * **Month 13 (Oct 2026):** Python for Cloud & **Project 5 (AegisScan)** Kick-off
  * **Month 14 (Nov 2026):** Building the AegisScan Core
  * **Month 15 (Dec 2026):** Practical Hacking & Reflection
  * **Month 16 (Jan 2027):** AI/ML Theory for Security
  * **Month 17 (Feb 2027):** **Project 4 (Neural Sentinel)** - Phishing Classifier
  * **Month 18 (Mar 2027):** **Project 4 (Neural Sentinel)** - Log Anomaly Detection
  * **Month 19 (Apr 2027):** Bug Bounty Automation (Evolving ReconKit)
  * **Month 20 (May 2027):** Portfolio & Resume
  * **Month 21 (Jun 2027):** LinkedIn & Professional Branding
  * **Month 22 (Jul 2027):** Interview Prep - Blue Team & Cloud
  * **Month 23 (Aug 2027):** Interview Prep - AI & Purple Team
  * **Month 24 (Sep 2027):** The Job Hunt & Future Vision

-----

## **Progress and Achievement Tracker:**
- **Markdown table to visualize my progress and keep myself accountable.**

## **Year 1**

| Month        | Focus / Goals                                                                    | Deliverables / Projects                                                                                                                            | Progress       |
| ------------ | -------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------- | -------------- |
| **Oct 2025** | CEH Theory (Intro, Footprinting, Scanning), Lab Foundation, ReconKit Kickoff     | - Create GitHub repo<br>- `/lab-setup` directory with VM screenshots<br>- `/toolkit-reconkit/header_fetch.py`                                      | 📝 In Progress |
| **Nov 2025** | CEH Theory (Enumeration, System Hacking), ReconKit Evolution, Threat of the Week | - `/toolkit-reconkit/log_parser.py` (counts 404s)<br>- First "Threat of the Week" summary in `/threat-intel`                                       | 📝 In Progress |
| **Dec 2025** | CEH Theory (Malware, Sniffing), Practical Tools, Toolkit Automation              | - `/toolkit-reconkit/nmap_automator.py`<br>- Quarterly Reflection #1 (`/reflections`)<br>- One-page PDF portfolio                                  | 📝 In Progress |
| **Jan 2026** | CEH Final Theory & Exam Prep                                                     | - Markdown summary of practice exams<br>- Final study plan                                                                                         | 📝 In Progress |
| **Feb 2026** | CEH Labs (1/3), SIEM Installation                                                | - Markdown documenting first 33% labs<br>- Running Wazuh/Security Onion VM                                                                         | 📝 In Progress |
| **Mar 2026** | CEH Labs (2/3), Log Collection, Reflection #2                                    | - Install Wazuh agents (Windows/Linux)<br>- Verify logs<br>- Quarterly Reflection #2<br>- Updated portfolio PDF                                    | 📝 In Progress |
| **Apr 2026** | CEH Labs (3/3), SIEM Documentation                                               | - Complete project write-up for Home Lab SIEM                                                                                                      | 📝 In Progress |
| **May 2026** | CEH Exam & First Red Team Weekend                                                | - CEH certificate<br>- TryHackMe profile link on GitHub README                                                                                     | 📝 In Progress |
| **Jun 2026** | Cloud Networking & Terraform Intro                                               | - Network diagram of standard VPC<br>- `/terraform-projects` with first script (S3 bucket)<br>- Quarterly Reflection #3<br>- Updated portfolio PDF | 📝 In Progress |
| **Jul 2026** | Build Secure Cloud Network                                                       | - Full Terraform script to deploy secure VPC                                                                                                       | 📝 In Progress |
| **Aug 2026** | Deploy Server & Connect to SIEM                                                  | - Update Terraform to deploy EC2<br>- Screenshot of CloudTrail logs in SIEM                                                                        | 📝 In Progress |
| **Sep 2026** | Detection Engineering & Year-End Review                                          | - Custom SIEM rule for CloudTrail events<br>- Quarterly Reflection #4<br>- Updated portfolio PDF                                                   | 📝 In Progress |

---

## **Year 2**

| Month        | Focus / Goals                        | Deliverables / Projects                                                                                                                           | Progress       |
| ------------ | ------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------- | -------------- |
| **Oct 2026** | Python for Cloud Automation          | - `/cloud-automation/list_iam_users.py` using `boto3`                                                                                             | 📝 In Progress |
| **Nov 2026** | Build Cloud Security Tool            | - Python script to check S3 buckets' public status                                                                                                | 📝 In Progress |
| **Dec 2026** | Practical Hacking & Reflection       | - TryHackMe "Web Fundamentals"<br>- Hack The Box Easy machine write-up<br>- Quarterly Reflection #5<br>- Updated portfolio                        | 📝 In Progress |
| **Jan 2027** | AI/ML Theory for Security            | - Markdown explaining Classification vs. Anomaly Detection                                                                                        | 📝 In Progress |
| **Feb 2027** | AI Project 1 – Phishing Classifier   | - `/AI4Sec/phishing_classifier.ipynb` Jupyter Notebook                                                                                            | 📝 In Progress |
| **Mar 2027** | AI Project 2 – Log Anomaly Detection | - `/AI4Sec/log_anomaly_detection.ipynb`<br>- Quarterly Reflection #6<br>- LinkedIn post & portfolio update                                        | 📝 In Progress |
| **Apr 2027** | Bug Bounty Automation                | - Python script in ReconKit chaining `subfinder` + `httpx`                                                                                        | 📝 In Progress |
| **May 2027** | Portfolio & Resume                   | - Live GitHub Pages portfolio<br>- PDF resume draft                                                                                               | 📝 In Progress |
| **Jun 2027** | LinkedIn & Professional Branding     | - Polished LinkedIn profile<br>- Featured article<br>- Quarterly Reflection #7<br>- Portfolio PDF update                                          | 📝 In Progress |
| **Jul 2027** | Interview Prep – Blue Team & Cloud   | - Markdown file with answers to 10 common questions<br>- 5-minute project presentations                                                           | 📝 In Progress |
| **Aug 2027** | Interview Prep – AI & Purple Team    | - Markdown file with 5 conceptual questions<br>- Recorded project explanations                                                                    | 📝 In Progress |
| **Sep 2027** | Job Hunt & Future Vision             | - Begin applying for jobs<br>- Portfolio "Future Research" section (Quantum Computing, AI-driven defense)<br>- Final Reflection (private journal) | 📝 In Progress |

---



