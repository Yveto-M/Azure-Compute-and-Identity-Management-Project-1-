
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
- **Password:** `XXXXXXXXX`
- **Ports Allowed:** 3389 (RDP)

✅ **Action:** Create the VM through Azure Portal.

<img width="961" alt="pt1 creating vm" src="https://github.com/user-attachments/assets/453a7224-0c29-4d89-a500-889ecc72b43f" />

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
  --source-address-prefixes 74.XXX.XX.2/32 \
  --destination-port-ranges 22 \
  --protocol TCP \
  --access Allow \
  --direction Inbound
````

---

## 👥 Step 3: Create and Assign a Custom RBAC Role

We created a custom RBAC role to define fine-grained permissions and assigned it to a user.

### Key Tasks:

* Defined JSON for custom role
* Created role with `az role definition create`
* Assigned role with `az role assignment create`

<img width="959" alt="Configured (RBAC)" src="https://github.com/user-attachments/assets/82fa05bc-9954-4db7-b289-92353e571b43" />
<img width="1009" alt="group key vault admin" src="https://github.com/user-attachments/assets/51d4253f-9748-441f-bcfd-cfb114edbf67" />

---

## 🏷️ Step 4: Enforce Tags Using Azure Policy Initiative

Used built-in Azure Policy: **Inherit a tag from the resource group**

* **Tag Name:** `Environment`
* **Value:** `Project1`
* Assigned to Resource Group: `Vetolabs`

<img width="1069" alt="define initiative pt 2" src="https://github.com/user-attachments/assets/c2c47138-9494-4c0e-b274-c191815375ea" />
<img width="1112" alt="inherent tags" src="https://github.com/user-attachments/assets/de13ee0f-72f2-458c-92bf-c23899532f52" />

---

## 💰 Step 5: Analyze Costs

Used Azure Cost Management to:

* Filter costs by resource group `Vetolabs`
* Visualize cost trends
* Take action based on insights

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

