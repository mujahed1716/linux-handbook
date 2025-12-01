# linux-handbook


✔️ A **GitHub-upload ready folder structure**
✔️ Three folders: **basic**, **intermediate**, **advanced**
✔️ Each folder contains **multiple working Linux automation scripts**
✔️ You can directly **push to GitHub** and execute scripts properly

---

## ✅ Project Structure (Copy-Paste into your Repo)

```
linux-server-automation/
│
├── basic/
│   ├── create_users.sh
│   ├── set_permissions.sh
│   ├── install_packages.sh
│   └── system_info.sh
│
├── intermediate/
│   ├── automate_backup.sh
│   ├── log_cleanup.sh
│   ├── check_service_status.sh
│   └── performance_monitor.sh
│
└── advanced/
    ├── custom_systemd_service.sh
    ├── ssh_hardening.sh
    ├── lvm_setup.sh
    ├── firewall_setup.sh
    └── logrotate_config.sh
```

---

---

## 🟩 **Folder: basic**
[basic](linux-server-automation/basic/create_users.sh)

### 1️⃣ `create_users.sh`

```bash
#!/bin/bash
sudo groupadd devteam
for user in dev1 dev2 dev3; do
    sudo useradd -m -G devteam $user
    echo "User $user created and added to devteam"
done
```

### 2️⃣ `set_permissions.sh`

```bash
#!/bin/bash
sudo mkdir -p /opt/devproject
sudo chown :devteam /opt/devproject
sudo chmod 770 /opt/devproject
echo "Permissions set for /opt/devproject"
```

### 3️⃣ `install_packages.sh`

```bash
#!/bin/bash
sudo apt update -y
sudo apt install -y git nginx default-jdk
echo "Git, Nginx & Java installed"
```

### 4️⃣ `system_info.sh`

```bash
#!/bin/bash
echo "CPU Info:"; lscpu
echo "Memory Info:"; free -h
echo "Disk Info:"; df -h
```

---

## 🟨 **Folder: intermediate**

### 1️⃣ `automate_backup.sh`

```bash
#!/bin/bash
SOURCE=/opt/devproject
BACKUP=/backup/devproject_$(date +%F).tar.gz
sudo tar -czvf $BACKUP $SOURCE
echo "Backup stored at $BACKUP"
```

*(Add to cron: `0 2 * * * /path/automate_backup.sh`)*

### 2️⃣ `log_cleanup.sh`

```bash
#!/bin/bash
find /var/log -type f -mtime +7 -exec rm -f {} \;
echo "Old logs cleared"
```

### 3️⃣ `check_service_status.sh`

```bash
#!/bin/bash
SERVICES="nginx ssh"
for svc in $SERVICES; do
    sudo systemctl is-active --quiet $svc && \
    echo "$svc is running" || \
    echo "$svc is down"
done
```

### 4️⃣ `performance_monitor.sh`

```bash
#!/bin/bash
echo "---CPU Load---"; top -b -n1 | head -5
echo "---Disk Space---"; df -h
echo "---Memory---"; free -h
```

---

## 🟥 **Folder: advanced**

### 1️⃣ `custom_systemd_service.sh`

```bash
#!/bin/bash
cat <<EOF | sudo tee /etc/systemd/system/myapp.service
[Unit]
Description=My Custom App Service

[Service]
ExecStart=/usr/bin/python3 /opt/myapp/app.py
Restart=always

[Install]
WantedBy=multi-user.target
EOF

sudo systemctl daemon-reload
sudo systemctl enable myapp
sudo systemctl start myapp
```

### 2️⃣ `ssh_hardening.sh`

```bash
#!/bin/bash
sudo sed -i 's/#PasswordAuthentication yes/PasswordAuthentication no/' /etc/ssh/sshd_config
sudo systemctl restart sshd
echo "SSH Hardening Applied: Password login disabled"
```

### 3️⃣ `lvm_setup.sh`

```bash
#!/bin/bash
sudo pvcreate /dev/sdb
sudo vgcreate myvg /dev/sdb
sudo lvcreate -n mylv -L 5G myvg
sudo mkfs.ext4 /dev/myvg/mylv
sudo mkdir /mnt/lvmdata
sudo mount /dev/myvg/mylv /mnt/lvmdata
echo "LVM setup completed"
```

### 4️⃣ `firewall_setup.sh`

```bash
#!/bin/bash
sudo ufw allow OpenSSH
sudo ufw allow 80/tcp
sudo ufw enable
echo "Firewall configured: SSH + HTTP allowed"
```

### 5️⃣ `logrotate_config.sh`

```bash
#!/bin/bash
cat <<EOF | sudo tee /etc/logrotate.d/myapp
/var/log/myapp.log {
    daily
    rotate 7
    compress
    missingok
    notifempty
}
EOF
echo "Logrotate config added"
```

---

# 👉 Execution Steps

```bash
chmod +x basic/*.sh
chmod +x intermediate/*.sh
chmod +x advanced/*.sh
```

Now run any script, e.g.:

```bash
./basic/install_packages.sh
```

---

# 🚀 GitHub Upload Instructions

```bash
git init
git add .
git commit -m "Initial automation project commit"
git branch -M main
git remote add origin <your_github_repo_url>
git push -u origin main
```






---

### **What is Linux?**

Linux is an **open-source operating system** based on the **Unix** architecture.
It acts as a bridge between **hardware and applications**, managing **processes, memory, file systems, and security**.

💡 Key points:

* Open-source → source code is freely available
* Highly secure and stable
* Most servers, cloud platforms, and DevOps environments run on Linux
* Supports CLI (Command Line Interface) and GUI

Commonly used in:

* AWS, Azure, GCP servers
* Containers (Docker uses Linux kernel features)
* CI/CD tools, Kubernetes, DevOps automation

---

### **Dynamic Linux Commands for DevOps Engineers**

Here are the **most important** commands grouped by usage:

---

#### 🔍 System & Process Monitoring

| Command                      | Purpose                       |
| ---------------------------- | ----------------------------- |
| `top` / `htop`               | View running processes live   |
| `ps aux`                     | Detailed process list         |
| `free -h`                    | Memory usage                  |
| `df -h`                      | Disk space usage              |
| `du -sh *`                   | Disk usage by files/folders   |
| `systemctl status <service>` | Check service status          |
| `journalctl -xe`             | View logs for system services |

---

#### 📂 File & Directory Management

| Command                                   | Purpose                 |
| ----------------------------------------- | ----------------------- |
| `ls -l`                                   | Detailed directory view |
| `cd`, `pwd`                               | Navigate paths          |
| `mkdir`, `rmdir`                          | Create/remove folders   |
| `cp`, `mv`, `rm -rf`                      | Copy/move/delete        |
| `find / -name filename`                   | Search files            |
| `touch`, `cat`, `less`, `head`, `tail -f` | Create & view files     |

---

#### 🔐 Permissions & Ownership

| Command                        | Purpose            |
| ------------------------------ | ------------------ |
| `chmod 755 file`               | Change permissions |
| `chown user:group file`        | Change ownership   |
| `useradd`, `passwd`, `usermod` | User management    |

---

#### 🌐 Network Commands

| Command                         | Purpose                        |
| ------------------------------- | ------------------------------ |
| `ifconfig` / `ip a`             | Check network interfaces       |
| `ping google.com`               | Check connectivity             |
| `curl <URL>`                    | API testing                    |
| `netstat -tulnp` or `ss -tulnp` | Check open ports               |
| `scp`, `rsync`                  | Transfer files between servers |

---

#### 📝 Log & File Inspection

| Command                     | Purpose                                     |
| --------------------------- | ------------------------------------------- |
| `grep "error" filename`     | Search inside files                         |
| `awk`, `sed`                | Text processing (mostly used in automation) |
| `tail -f /var/log/messages` | Live log view                               |

---

#### 🔧 Package Management

| OS Type       | Commands                     |
| ------------- | ---------------------------- |
| RHEL/CentOS   | `yum install`, `rpm -qa`     |
| Ubuntu/Debian | `apt-get install`, `dpkg -l` |

---

#### 🐳 Container & DevOps Tools (Bonus)

| Tool       | Example Command                     |
| ---------- | ----------------------------------- |
| Docker     | `docker ps`, `docker images`        |
| Git        | `git status`, `git pull`, `git log` |
| Kubernetes | `kubectl get pods`                  |

---

### 💡 Tip for Interviews

They often ask:

* How do you check CPU/memory usage?
* How do you find which process is using a port?
* How do you monitor logs in real time?
* How do you troubleshoot service failure?

