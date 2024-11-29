<link rel="stylesheet" href="dark-theme.css">

# Backup and Restore Raspberry Pi Over SSH

This document outlines how to back up your Raspberry Pi's SD card over SSH and restore it when needed.

---

## **Backup the Raspberry Pi SD Card Over SSH**
This method creates an image backup of the Raspberry Pi's SD card and saves it to your Mac.

### **Backup Steps**

1. **Ensure SSH is Enabled**:
   SSH must be enabled on your Raspberry Pi. Use `sudo raspi-config` to enable it if needed.

2. **Connect to Your Raspberry Pi**:
   Test the SSH connection from your Mac:
   ```bash
   ssh pi@<Pi_IP_Address>
   ```

3. **Run the Backup Command**:
   Copy and execute the following command on your Mac to back up the SD card:
   ```bash
   ssh pi@<Pi_IP_Address> "sudo dd if=/dev/mmcblk0 bs=4M status=progress" | dd of=~/RaspberryPiBackup.img bs=4M
   ```

4. **Compress the Backup File (Optional)**:
   Save storage by compressing the image:
   ```bash
   gzip ~/RaspberryPiBackup.img
   ```

---

## **Restore the Raspberry Pi SD Card Over SSH**

### **Restore Steps**

1. **Copy the Backup File to Raspberry Pi**:
   Transfer the backup file from your Mac to the Raspberry Pi:
   ```bash
   scp ~/RaspberryPiBackup.img pi@<Pi_IP_Address>:~/RaspberryPiBackup.img
   ```

2. **Restore the SD Card**:
   Write the backup image to the SD card:
   ```bash
   sudo dd if=~/RaspberryPiBackup.img of=/dev/mmcblk0 bs=4M status=progress
   ```

3. **Verify the Restoration**:
   Power off the Raspberry Pi, eject the SD card, and test the restored system.

---

## **Notes**
- Replace `/dev/mmcblk0` with the correct SD card device name (use `lsblk` to check).
- The backup process can be scripted for automation.
- Ensure enough storage on your Mac for the `.img` file.

---

Copy and paste these commands as needed for a seamless backup and restoration process.
