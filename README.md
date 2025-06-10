Here’s your complete `README.md` for **Azure Project 1: Compute and Identity Management**, formatted and ready for GitHub. I've added placeholders where you can paste your lab screenshots.

---

````markdown
# 💻 Azure Project 1: Compute and Identity Management

## 🔍 Overview

This project demonstrates how to deploy and manage a Windows Virtual Machine (VM) in Azure, implement secure access with SSH, apply Role-Based Access Control (RBAC), enforce tagging via Azure Policy, and analyze costs using Azure's billing features.

---

## 🧩 Step 1: Deploy a Windows Virtual Machine

- **Resource Group:** `Vetolabs`
- **VM Name:** `vetoadmin-vm`
- **Region:** East US
- **Size:** `Standard_DS1_v2`
- **Image:** Windows 11 Pro
- **Username:** `userveto`
- **Password:** `Userkato11$$`
- **Ports Allowed:** 3389 (RDP)

✅ **Action:** Create the VM through Azure Portal.

📸 _Screenshot Placeholder: VM Deployment Confirmation_

---

## 🔐 Step 2: Enable SSH Access on the VM

We enabled OpenSSH on a Windows VM to support secure remote access.

### Azure CLI Commands:

```bash
az vm extension set \
  --resource-group Vetolabs \
  --vm-name vetoadmin-vm \
  --name WindowsOpenSSH \
  --publisher Microsoft.Azure.OpenSSH \
  --version 3.0

az network nsg rule create \
  --resource-group Vetolabs \
  --nsg-name vetoadmin-vm-nsg \
  --name allow-SSH \
  --priority 1000 \
  --source-address-prefixes 74.249.24.2/32 \
  --destination-port-ranges 22 \
  --protocol TCP \
  --access Allow \
  --direction Inbound
````

📸 *Screenshot Placeholder: SSH Enabled + NSG Rule*

---

## 👥 Step 3: Create and Assign a Custom RBAC Role

We created a custom RBAC role to define fine-grained permissions and assigned it to a user.

### Key Tasks:

* Defined JSON for custom role
* Created role with `az role definition create`
* Assigned role with `az role assignment create`

📸 *Screenshot Placeholder: Custom Role Creation and Assignment*

---

## 🏷️ Step 4: Enforce Tags Using Azure Policy Initiative

Used built-in Azure Policy: **Inherit a tag from the resource group**

* **Tag Name:** `Environment`
* **Value:** `Project1`
* Assigned to Resource Group: `Vetolabs`

📸 *Screenshot Placeholder: Azure Policy Assignment*

---

## 💰 Step 5: Analyze Costs

Used Azure Cost Management to:

* Filter costs by resource group `Vetolabs`
* Visualize cost trends
* Take action based on insights

📸 *Screenshot Placeholder: Cost Analysis Breakdown*

---

## ✅ Summary

| Capability        | Demonstrated ✅ |
| ----------------- | -------------- |
| VM Deployment     | ✔️             |
| SSH Configuration | ✔️             |
| NSG Rules         | ✔️             |
| Custom RBAC       | ✔️             |
| Azure Policy      | ✔️             |
| Cost Monitoring   | ✔️             |

---

## 📂 Project Structure

```
project-1-azure-compute-identity/
│
├── README.md
├── customRole.json
├── screenshots/
│   ├── vm-deployment.png
│   ├── ssh-setup.png
│   ├── rbac-role.png
│   ├── policy-tags.png
│   └── cost-analysis.png
```

---

## 📌 Author

**Yveto Meus**
Master’s in Cybersecurity | Azure & Identity Security Enthusiast

