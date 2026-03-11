# gcp-minecraft-server-lab
# Minecraft Server Deployment on Google Cloud

This project demonstrates how to deploy a Minecraft server on Google Cloud Platform using Compute Engine, Persistent Disks, Firewall rules, and Cloud Storage backups.

---

## Architecture

The infrastructure includes:

- Google Compute Engine VM
- Persistent SSD Disk for game data
- Firewall rule allowing Minecraft traffic
- Static External IP
- Cloud Storage bucket for backups
- Cron job for automated backups

---

## VM Configuration

- Instance Name: mc-server
- OS: Debian GNU/Linux 12
- Machine Type: e2-medium
- Disk: 50GB SSD Persistent Disk
- Region: us-central1
- Firewall Port: TCP 25565

---

## Installation Steps

### 1. Update System

```bash
sudo apt-get update

2. Install Java Runtime

sudo apt-get install -y default-jre-headless

3. Install wget

sudo apt-get install wget

4. Download Minecraft Server

sudo wget https://launcher.mojang.com/v1/objects/d0d0fe2b1dc6ab4c65554cb734270872b72dadd6/server.jar

5. Start the Server

sudo java -Xmx1024M -Xms1024M -jar server.jar nogui

Firewall Rule

Port opened:

TCP 25565

Used for Minecraft client connections.

Backup System

Backups are stored in a Cloud Storage bucket.

Script used:

scripts/backup.sh

Backup is scheduled every 4 hours using cron.

Cron Job

0 */4 * * * /home/minecraft/backup.sh

Screenshots

Screenshots of the deployment process are included in the screenshots folder.

Result

The Minecraft server is successfully deployed on Google Cloud and accessible via the external IP address.

Automated backups ensure the world data is securely stored in Cloud Storage.
