# Ansible Passwordless Multi-Node Automation

Configuring an Ansible Control Node (Master) to manage two Managed Nodes (Workers) without passwords, using SSH key-based authentication and a custom inventory file — a DEPI DevOps Track task.

---

## 📋 Scenario

- **1 Ansible Control Node (Master)** — 1GB RAM, 1 CPU
- **2 Managed Nodes (Workers)** — 1GB RAM, 1 CPU each

**Goal:** Configure the environment so the Master can manage both Workers using Ansible without passwords.

---

## ✅ Requirements

**On All Nodes**
1. Create a user named `ansible`
2. Set a password for the user
3. Configure sudo privileges for the user
4. Verify the user can execute commands using `sudo`

**On the Master Node**
1. Install Ansible using `pip`
2. Generate an SSH key pair for the `ansible` user
3. Verify the key pair was created successfully

**Configure Passwordless Authentication**
1. Copy the public key from the Master to both Workers using `ssh-copy-id`
2. Verify SSH from the Master to each Worker works without a password

**Inventory Configuration**
1. Create an inventory file containing both workers, named `inventory`

---

## 🔧 Setup Steps

### 1. Create the `ansible` user and configure sudo (run on all nodes)

![User creation, sudo config, and SSH keygen](./images/01-user-sudo-ssh-keygen.png)

```bash
useradd ansible
passwd ansible
su - ansible
```

Then edit the sudoers file:

```bash
visudo
```

Add the following line to grant passwordless sudo:
