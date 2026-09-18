# Cloud-Assisted SOC & Endpoint Monitoring Lab

## Project Overview
This project demonstrates the deployment of a hybrid Security Operations Center (SOC) lab optimized for resource-constrained hardware (8GB RAM host). The architecture separates the heavy data processing layers into a cloud environment while utilizing localized virtualization to generate and ship authentic endpoint telemetry.

## Topology & Components
* *Host Hardware:* Apple Silicon Mac (8GB RAM)
* *Endpoint Target:* macOS Virtual Machine isolated via *UTM Virtualization* (Allocated: 3GB RAM / 64GB Storage)
* *SIEM Core:* Cloud-hosted *Elastic Stack (Elasticsearch & Kibana)* 
* *Data Pipeline:* *Elastic Fleet Agent* deployed via native command-line interface

---

## Deployment & Implementation Phases

### Phase 1: Endpoint Virtualization & Resource Optimization
To prevent physical hardware exhaustion, an isolated virtual endpoint was deployed natively. 
* VMware Fusion was excluded due to x86/Arm CPU architecture conflicts on Apple Silicon.
* UTM was utilized to interface directly with Apple's native Virtualization Framework.
* The system was systematically optimized down to 3GB RAM to safeguard host OS stability.

👉 *[INSERT SCREENSHOT 1 HERE: Drag and drop your UTM dashboard screenshot]*

### Phase 2: Cloud SIEM Provisioning & Agent Enrollment
An enterprise-grade Elastic SIEM cluster was spun up in the cloud to manage log ingestion, parsing, and data visualization. 
* Generated a secure Elastic Agent bootstrap script.
* Opened the administrative Terminal inside the UTM macOS environment.
* Successfully executed the background daemon installation and established a secure TLS connection back to the Cloud Fleet.

👉 *[INSERT SCREENSHOT 2 HERE: Drag and drop your Elastic Agent Enrolled screenshot]*

### Phase 3: Telemetry Validation & Security Event Simulation
To verify data pipeline integrity, a mock administrative privilege manipulation was executed inside the virtual endpoint:
bash
sudo dscl . -create /Users/testattacker

The endpoint agent captured the command line event, structured the telemetry metadata, and streamed it to the SIEM database.

### Phase 4: Analytical Log Analysis
Using Kibana's *Discover* pane, a Lucene/KQL query was built to isolate the malicious telemetry payload. The audit record successfully confirmed the timestamp, host variables, and executing string data.

👉 *[INSERT SCREENSHOT 3 HERE: Drag and drop your Elastic Discover search screenshot]*

---

## Key Skills Demonstrated
* *Security Operations (SecOps):* Log ingestion, data pipeline engineering, SIEM dashboard auditing.
* *Systems Architecture:* Virtualization optimization, multi-node resource allocation.
* *Technical Writing:* Comprehensive system auditing and deployment documentation.
*<img width="1463" height="924" alt="Screenshot 2026-09-18 at 02 40 54" src="https://github.com/user-attachments/assets/2826d181-b0a5-43fe-9ad6-c6b0fba7e0f2" />
<img width="1463" height="924" alt="Screenshot 2026-09-18 at 01 47 43" src="https://github.com/user-attachments/assets/fcf571eb-6d16-4b53-9a38-904a35381de5" />
<img width="1463" height="924" alt="Screenshot 2026-09-18 at 01 09 45" src="https://github.com/user-attachments/assets/9236f412-25d0-4be6-9215-e34aba24408c" />
