![Uploading Screenshot 2026-09-18 at 01.09.45.png…]()
<img width="1463" height="924" alt="Screenshot 2026-09-18 at 02 40 54" src="https://github.com/user-attachments/assets/998c2e26-cf53-462f-b05e-66169cb4314e" />
<img width="1463" height="924" alt="Screenshot 2026-09-18 at 01 47 43" src="https://github.com/user-attachments/assets/1b99295d-a293-455c-9051-1716fc10085e" />
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

![UTM Config](Screenshot%202026-09-18%20at%2001.09.45.jpg)

### Phase 2: Cloud SIEM Provisioning & Agent Enrollment
An enterprise-grade Elastic SIEM cluster was spun up in the cloud to manage log ingestion, parsing, and data visualization. 
* Generated a secure Elastic Agent bootstrap script.
* Opened the administrative Terminal inside the UTM macOS environment.
* Successfully executed the background daemon installation and established a secure TLS connection back to the Cloud Fleet.

![Elastic Agent](Screenshot%202026-09-18%20at%2001.47.43.jpg)

### Phase 3: Telemetry Validation & Security Event Simulation
To verify data pipeline integrity, a mock administrative privilege manipulation was executed inside the virtual endpoint:
bash
sudo dscl . -create /Users/testattacker

The endpoint agent captured the command line event, structured the telemetry metadata, and streamed it to the SIEM database.

### Phase 4: Analytical Log Analysis
Using Kibana's *Discover* pane, a Lucene/KQL query was built to isolate the malicious telemetry payload. The audit record successfully confirmed the timestamp, host variables, and executing string data.

![Kibana Log](Screenshot%202026-09-18%20at%2002.40.54.jpg)


## Key Skills Demonstrated
* *Security Operations (SecOps):* Log ingestion, data pipeline engineering, SIEM dashboard auditing.
* *Systems Architecture:* Virtualization optimization, multi-node resource allocation.
* *Technical Writing:* Comprehensive system auditing and deployment documentation.
