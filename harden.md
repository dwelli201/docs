[Back](./education.md)

# Hardening your VM or Linux IoT devices

Hardening your virtual machine (VM) is essential to secure it from potential exploits and attacks. Here are some best practices for hardening your VM, focusing on Debian-based systems but applicable to most Linux distributions.

### 1. **Keep Your System Updated**
Regularly update your system to apply security patches and fixes:
```bash
sudo apt update
sudo apt upgrade
```
Consider enabling unattended upgrades to automatically apply security patches:
```bash
sudo apt install unattended-upgrades
sudo dpkg-reconfigure unattended-upgrades
```

### 2. **Install and Configure a Firewall**
Using `firewalld` or `ufw` to control incoming and outgoing traffic is a basic but effective security measure.

- **Install UFW (Uncomplicated Firewall):**
   ```bash
   sudo apt install ufw
   ```
- **Allow only necessary services:**
   ```bash
   sudo ufw allow ssh
   sudo ufw enable
   ```

Check firewall status:
```bash
sudo ufw status
```

### 3. **Use SSH Securely**
If you're using SSH to access the VM, securing SSH is crucial.

- **Disable root login:**
  Edit the SSH config file:
  ```bash
  sudo nano /etc/ssh/sshd_config
  ```
  Set:
  ```
  PermitRootLogin no
  ```
  Restart SSH:
  ```bash
  sudo systemctl restart ssh
  ```

- **Change the default SSH port** to something other than `22` to avoid automated attacks:
  ```
  Port 2200
  ```

- **Use SSH key authentication** instead of passwords.

### 4. **Install Fail2ban**
Fail2ban helps protect against brute-force attacks by blocking IPs that show malicious behavior.

- **Install Fail2ban:**
   ```bash
   sudo apt install fail2ban
   ```

- **Enable and configure Fail2ban for SSH:**
   ```bash
   sudo systemctl enable fail2ban
   sudo systemctl start fail2ban
   ```

### 5. **Use AppArmor or SELinux for Mandatory Access Control**
AppArmor and SELinux provide Mandatory Access Control (MAC) to restrict the capabilities of processes, adding a layer of security.

- **Install AppArmor:**
   ```bash
   sudo apt install apparmor
   sudo apt install apparmor-profiles apparmor-utils
   ```

- **Enable AppArmor profiles:**
   Use AppArmor profiles to define what resources specific applications can access:
   ```bash
   sudo aa-enforce /etc/apparmor.d/*
   ```

### 6. **Configure Virtualization Security Settings**
Virtualization tools, like UTM or QEMU, may have security settings you can configure for hardening:

- **Disable unused hardware features** in your VM, like USB passthrough or audio.
- **Enable CPU and memory isolation** if available, preventing exploits from spreading across VMs.

### 7. **Limit Services Running on the VM**
Review and disable any unnecessary services that may be running on your VM:
```bash
sudo systemctl list-unit-files --type=service | grep enabled
```
Disable unused services:
```bash
sudo systemctl disable <service_name>
sudo systemctl stop <service_name>
```

### 8. **Install ClamAV for Anti-Malware Protection**
Install and configure **ClamAV** to scan for malware:

```bash
sudo apt install clamav clamav-daemon
sudo systemctl start clamav-freshclam
```

Run a manual scan:
```bash
sudo clamscan -r /home
```

### 9. **Enable Full Disk Encryption (FDE)**
Encrypting your VM’s disk ensures that data at rest is secure, even if an attacker gains access to the virtual disk.

- If your VM was not initially set up with encryption, you can encrypt sensitive directories (like `/home`, `/var`) using tools like **LUKS** or **ecryptfs**.

### 10. **Use Strong Password Policies**
Set password policies to enforce the use of strong passwords. Edit `/etc/pam.d/common-password` to enforce strong password rules using the `pam_cracklib` module:

```bash
password requisite pam_cracklib.so retry=3 minlen=12 difok=3
```

### 11. **Limit Access with User Privileges**
- **Disable root account login** (already covered with SSH hardening).
- **Use `sudo` instead of `su`:** Ensure users operate with minimal privileges and escalate only when needed.
- **Review and minimize the number of sudo users**.

### 12. **Install and Configure Auditd**
`auditd` is the userspace component to log and monitor system events, which is useful for detecting suspicious activities.

- **Install auditd:**
   ```bash
   sudo apt install auditd
   ```
- **Start and enable auditd:**
   ```bash
   sudo systemctl start auditd
   sudo systemctl enable auditd
   ```

### 13. **Monitor and Log Events**
Ensure logging is properly set up to monitor for suspicious activity.

- **Configure rsyslog:** It is usually installed by default, but verify it's running.
  ```bash
  sudo systemctl status rsyslog
  ```

- **Use log monitoring tools like `logwatch` or `syslog-ng`**:
   ```bash
   sudo apt install logwatch
   ```

- **Consider setting up remote logging** so that even if the VM is compromised, the logs are safe.

### 14. **Enable Kernel Hardening Options**
Debian kernels come with several hardening options that you can enable.

- **Disable unused filesystems** (e.g., USB storage, floppy disk drivers) by adding entries in `/etc/modprobe.d/blacklist.conf`.

- **Enable Address Space Layout Randomization (ASLR):**
   This can be checked and enabled with:
   ```bash
   sudo sysctl -w kernel.randomize_va_space=2
   ```

### 15. **Regular Backups**
Regularly back up your VM using snapshot tools (like those provided by UTM or other virtualization software) to ensure you can recover quickly from any exploit.

---

By implementing these measures, you can significantly reduce the risk of exploitation in your virtual machine. Each layer adds an extra defense, improving your overall security posture.
