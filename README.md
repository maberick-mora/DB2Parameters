# UpdateDB2parameters.yaml
Updating parameters for a DB2

# 🔧 DB2 Configuration Update Playbook

This Ansible playbook automates the process of updating DB2 configuration parameters across all namespaces containing `db2u` deployments in a Kubernetes cluster.

---

## 📘 Description

The playbook:
- Authenticates to the target cluster (using the `ibmcloud_auth` role if needed).
- Iterates through all namespaces that match `db2u*`.
- Executes DB2 parameter updates inside the `db2u-0` pods.
- Ensures consistency of key DB2 settings across all environments.

---

## ⚙️ DB2 Parameters Applied

The playbook applies the following changes inside each DB2 instance:
```bash
db2set DB2_USE_ALTERNATE_PAGE_CLEANING=ON
db2 update dbm cfg using AGENT_STACK_SZ 1024
db2 update db cfg for BLUDB using AUTO_REORG OFF
