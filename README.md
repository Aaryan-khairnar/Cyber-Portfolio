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

-----

### **The Updated 24-Month Roadmap**

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

| Month      | Goal                                                               | Status (📝 In Progress / ✅ Done) | Repo Link |
| :--------- | :----------------------------------------------------------------- | :------------------------------ | :-------- |
| **Oct 2025** | Cover first 25% of CEH curriculum (Theory)                         |                                 |           |
| **Oct 2025** | Set up virtual lab (`virt-manager`, Windows Server, Kali Linux)    |                                 |           |
| **Oct 2025** | Create `ReconKit` toolkit: `header_fetch.py`                       |                                 |           |
| **Nov 2025** | Cover next 25% of CEH curriculum (Theory)                          |                                 |           |
| **Nov 2025** | Create `ReconKit` tool: `log_parser.py`                            |                                 |           |
| **Nov 2025** | Start "Threat of the Week" summary series                        |                                 |           |
| **Dec 2025** | Cover next 25% of CEH curriculum (Theory)                          |                                 |           |
| **Dec 2025** | Create `ReconKit` tool: `nmap_automator.py`                        |                                 |           |
| **Dec 2025** | Write Quarterly Reflection #1                                      |                                 |           |
| **Jan 2026** | Cover final 25% of CEH curriculum (Theory)                         |                                 |           |
| **Jan 2026** | Review all CEH notes and take practice exams                     |                                 |           |
| **Feb 2026** | Complete first 33% of official CEH labs                          |                                 |           |
| **Feb 2026** | Install and configure SIEM (Wazuh or Security Onion)             |                                 |           |
| **Mar 2026** | Complete second 33% of official CEH labs                         |                                 |           |
| **Mar 2026** | Install Wazuh agent on Windows & Linux VMs and verify logs         |                                 |           |
| **Mar 2026** | Write Quarterly Reflection #2                                      |                                 |           |
| **Apr 2026** | Complete final 33% of official CEH labs                          |                                 |           |
| **Apr 2026** | Finalize and document "Home Lab SIEM" project                    |                                 |           |
| **May 2026** | Take and pass the CEH exam                                       |                                 |           |
| **May 2026** | Start "Red Team Weekend": TryHackMe "Pre-Security" Path           |                                 |           |
| **Jun 2026** | Learn AWS networking concepts (VPC, Subnets, Security Groups)    |                                 |           |
| **Jun 2026** | Create a network diagram for a standard VPC                        |                                 |           |
| **Jun 2026** | Write Quarterly Reflection #3                                      |                                 |           |
| **Jul 2026** | Install Terraform and write first script (create S3 bucket)        |                                 |           |
| **Aug 2026** | Write Terraform script to deploy a secure VPC and EC2 instance   |                                 |           |
| **Aug 2026** | **Purple Team Goal:** Forward AWS CloudTrail logs to your SIEM     |                                 |           |
| **Sep 2026** | Write a custom SIEM rule to detect a specific CloudTrail event   |                                 |           |
| **Sep 2026** | Write Quarterly Reflection #4 (Year-End Review)                  |                                 |           |
| **Oct 2026** | Learn `boto3` basics and write script to list IAM users            |                                 |           |
| **Nov 2026** | Build AegisScan: an automated cloud security auditor             |                                 |           |
| **Dec 2026** | Complete TryHackMe "Web Fundamentals" path                       |                                 |           |
| **Dec 2026** | **Red Team Weekend:** Solve first "Easy" Hack The Box machine      |                                 |           |
| **Dec 2026** | Write Quarterly Reflection #5                                      |                                 |           |
| **Jan 2027** | Understand AI/ML theory (Classification vs. Anomaly Detection)   |                                 |           |
| **Feb 2027** | **AI Project 1:** Build a simple phishing email classifier         |                                 |           |
| **Mar 2027** | **AI Project 2:** Apply anomaly detection to your SIEM logs        |                                 |           |
| **Mar 2027** | Write Quarterly Reflection #6                                      |                                 |           |
| **Apr 2027** | **Bug Bounty:** Automate recon process (chain tools with Python)   |                                 |           |
| **May 2027** | Create a portfolio website using GitHub Pages                    |                                 |           |
| **May 2027** | Write the first draft of your professional resume                  |                                 |           |
| **Jun 2027** | Polish LinkedIn profile to professional standards                |                                 |           |
| **Jun 2027** | Write and publish a long-form article on LinkedIn                |                                 |           |
| **Jun 2027** | Write Quarterly Reflection #7                                      |                                 |           |
| **Jul 2027** | Practice Blue Team & Cloud interview questions                       |                                 |           |
| **Jul 2027** | Prepare a 5-minute presentation for each major project           |                                 |           |
| **Aug 2027** | Practice AI & Purple Team conceptual interview questions         |                                 |           |
| **Aug 2027** | Record yourself explaining your projects for practice            |                                 |           |
| **Sep 2027** | Begin applying for jobs and contacting recruiters                |                                 |           |
| **Sep 2027** | Add "Future Research" section to your portfolio website            |                                 |           |

