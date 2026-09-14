# Ansible Passwordless Multi-Node Automation

## 📌 Scenario

- **1 Ansible Control Node (Master)** — 1GB RAM, 1CPU
- **2 Managed Nodes (Workers)** — 1GB RAM, 1CPU each

**Goal:** Configure the environment so the Master can manage both Workers using Ansible **without passwords**.

---

## ✅ Requirements

### On All Nodes
- Create a user named `ansible`
- Set a password for the user
- Configure sudo privileges for the user
- Verify that the user can execute commands using `sudo`

### On the Master Node
- Install Ansible using `pip`
- Generate an SSH key pair for the `ansible` user
- Verify that the key pair was created successfully

### Configure Passwordless Authentication
- Copy the public key from the Master to both Workers using `ssh-copy-id`
- Verify that you can SSH from the Master to each Worker without entering a password

### Inventory Configuration
- Create an inventory file containing both workers named `inventory`
