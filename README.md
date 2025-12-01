# linux-handbook


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

 🚀
