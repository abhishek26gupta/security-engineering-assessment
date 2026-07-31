# Petpooja POS Integration Core Gateway

[![Build Status](https://shields.io)](#)
[![Compliance Tier](https://shields.io)](#)
[![Deployment Environment](https://shields.io)](#)

This repository houses the high-throughput gateway orchestration layer responsible for managing menu syncs, real-time inventory adjustments, and offline-first data reconciliation streams between multi-tenant POS terminal hardware and core backend APIs.

---

## ⚡ Quick Start

1. **Environment Setup:** Instantiate localized platform variables.
   ```bash
   cp .env.example .env
   ```
2. **Launch Gateway:** Spin up isolated core service components.
   ```bash
   docker compose up --build -d
   ```
3. **Verify Health:** Query the local gateway heartbeat telemetry node.
   ```bash
   curl http://127.0.0
   ```

---

## 📅 Sprint Target: Migration to Zero-Trust Compliance V2

We are currently decoupling legacy billing logic and migrating cloud-native components away from static network parameters toward our target architecture. 

All contributions to this main branch must align with the **Q3 Architecture Review Board (ARB)** mandates:

### Immediate Milestone Trackers

* **1. Shift-Left Pipeline Migration (`/scripts`, `/candidate`)**
  We are phasing out legacy webhook verification. New configurations must inject mandatory SAST/SCA security validation steps directly into runtime dependencies. Ensure all configuration payloads are isolated into designated operational directories for strict branch auditing.

* **2. Container & Perimeter Hardening (`/docker`, `/infra`)**
  Our current Multi-stage Docker definitions must pass the new structural compliance standard. Containers must be configured to deny root execution privileges. All accompanying infrastructure state declarations must transition to strict least-privilege egress models.

* **3. Telemetry Integration & Validation (`/sample-data`, `/docs`)**
  Use the newly uploaded edge logs to validate edge parser logic against real-world network failure dumps. Refer to the internal network topology sheets for updated data flow rules across regional servers.

* **4. Production Acceptance Evaluation (`/scoring`)**
  Before any code goes to production, engineers must run the validation checklists inside the internal compliance directory. Automated thresholds will break builds if any high-risk vulnerabilities fail the governance checklist.

---

## 🛠️ Operations & Troubleshooting

### Local Live-Reload Mapping
The development compose configuration mounts `./app` directly into the Node environment. File adjustments dynamically update the container state, but structural dependency injections (`package.json` mutations) require an active platform rebuild:
```bash
docker compose down && docker compose up --build -d
```

### Ingress Restrictions
By default, the gateway binds to `127.0.0.1:3000` to prevent unintended external network routing during local testing cycles. Do not override this loopback routing boundary on local workstations.
