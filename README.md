<p align="center">
  <img src="https://raw.githubusercontent.com/docker/docs/main/static/img/docker-logo-white.png" width="420" />
</p>

<p align="center">
  <a href="https://www.linkedin.com/in/raja-ramees-804a7b262" target="_blank">
    <img src="https://img.shields.io/badge/LinkedIn-Raja%20Ramees-0A66C2?logo=linkedin&logoColor=white&style=for-the-badge" />
  </a>
</p>

<h1 align="center">  INSTALLATION · DOCKER DESKTOP · UBUNTU</h1>

<p align="center">
  <b>⚡ One Guide · One Flow · Zero Confusion ⚡</b><br/>
  <i>Built for beginners, trusted by professionals</i>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Ubuntu-22.04%20%7C%2024.04-FF6C37?logo=ubuntu&style=for-the-badge" />
  <img src="https://img.shields.io/badge/Docker-Desktop-2496ED?logo=docker&style=for-the-badge" />
  <img src="https://img.shields.io/badge/Setup-Type%20%7C%20GUI%20+%20CLI-0db7ed?style=for-the-badge" />
</p>

<hr/>

<p align="center">
  <img src="https://www.vectorlogo.zone/logos/docker/docker-ar21.svg" width="300" />
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Ubuntu-22.04%20%7C%2024.04-orange?logo=ubuntu&style=for-the-badge" />
  <img src="https://img.shields.io/badge/Docker-Desktop-blue?logo=docker&style=for-the-badge" />
  <img src="https://img.shields.io/badge/Level-Beginner%20Friendly-green?style=for-the-badge" />
</p>

---

## 🌟 What You Will Achieve

✅ Install **Docker Desktop** on Ubuntu step‑by‑step
✅ Use **GUI + Terminal** together
✅ Proper **Docker repository setup using `.sh` script**
✅ Verify Docker, Docker Compose & CLI

---

## 🟢 STEP 1: Go to Docker Website

🌐 Open browser and go to:

👉 **[https://www.docker.com](https://www.docker.com)**

### Actions:

1. Put your **cursor on `Download Docker Desktop`**
2. Click **Docker Desktop for Linux**
3. Choose **Ubuntu**

📌 Keep this page open

---

## 🟢 STEP 2: Read Installation Instructions

On the same page, scroll to:

> **Install Docker Desktop on Ubuntu**

You will see:

> **Recommended approach to install Docker Desktop on Ubuntu**

👉 Click **“Install using the apt repository”**

📋 **COPY the repository setup code** (we will paste it in a script)

---

## 🟢 STEP 3: Create Installation Script (.sh)

### Open Terminal

```bash
cd ~/Downloads
```

### Create script file

```bash
touch install-docker-desktop.sh
```

### Open file in editor

```bash
nano install-docker-desktop.sh
```

### Paste this code inside 👇

```bash
#!/bin/bash

# Add Docker's official GPG key:
sudo apt update
sudo apt install -y ca-certificates curl
sudo install -m 0755 -d /etc/apt/keyrings
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
sudo chmod a+r /etc/apt/keyrings/docker.asc

# Add the repository to Apt sources:
sudo tee /etc/apt/sources.list.d/docker.sources > /dev/null <<EOF
Types: deb
URIs: https://download.docker.com/linux/ubuntu
Suites: $(. /etc/os-release && echo "${UBUNTU_CODENAME:-$VERSION_CODENAME}")
Components: stable
Signed-By: /etc/apt/keyrings/docker.asc
EOF

sudo apt update
```

Save & exit:

```
CTRL + O → ENTER → CTRL + X
```

---

## 🟢 STEP 4: Run the Script

### Give permission

```bash
chmod 700 install-docker-desktop.sh
```

### Run script

```bash
./install-docker-desktop.sh
```

✅ Docker repository is now configured correctly

---

## 🟢 STEP 5: Download Docker Desktop (.deb)

Go back to **Docker website**

👉 Click:

**Download the latest DEB package**

📥 File will download to:

```
~/Downloads/docker-desktop-amd64.deb
```

---

## 🟢 STEP 6: Install Docker Desktop

In terminal:

```bash
sudo apt-get update
sudo apt install ./docker-desktop-amd64.deb
```

### ⚠️ IMPORTANT NOTE

You may see this warning (IGNORE IT):

```
N: Download is performed unsandboxed as root
Permission denied
```

✔️ This is **normal & safe**

📍 Installed location:

```
/opt/docker-desktop
```

---

## 🟢 STEP 7: What Installer Does Automatically

✔ Maps privileged ports
✔ Sets resource limits
✔ Adds Kubernetes DNS to `/etc/hosts`
✔ Creates Docker CLI symlink

```
/usr/local/bin/com.docker.cli → /usr/bin/docker
```

---

## 🟢 STEP 8: Launch Docker Desktop

### 🎨 GUI Method

1. Open **Applications**
2. Click **Docker Desktop**
3. Accept **Docker Subscription Agreement**

🚨 Docker Desktop will NOT start without accepting terms

---

### ⚡ Terminal Method

```bash
systemctl --user start docker-desktop
```

Enable auto‑start on login:

```bash
systemctl --user enable docker-desktop
```

Stop Docker Desktop:

```bash
systemctl --user stop docker-desktop
```

---

## 🟢 STEP 9: Verify Installation

```bash
docker compose version
docker --version
docker version
```

Expected output example:

```
Docker Compose version v2.39.4
Docker version 28.4.0
```

---

## 🎉 SUCCESS! YOU ARE DONE

<p align="center">
  <img src="https://img.shields.io/badge/Docker-Desktop%20Installed-success?style=for-the-badge&logo=docker" />
</p>

✅ Docker Desktop GUI
✅ Docker CLI
✅ Docker Compose v2
✅ Enterprise‑ready setup

---

## ❤️ Final Words

This guide is **beginner‑proof, production‑ready, and future‑safe**.

📌 Share this repo with your team — anyone can install Docker Desktop in **minutes**.

---

🔥 Happy Dockering!

---

# 🧹 Clean Uninstall Docker (Fresh Install Preparation)

<p align="center">
  <img src="https://img.shields.io/badge/Docker-Cleanup-FF4C4C?logo=docker&style=for-the-badge" />
  <img src="https://img.shields.io/badge/Mode-Fresh%20Install-yellow?style=for-the-badge" />
</p>

> ⚠️ **RUN THIS FIRST if Docker is already installed on your system.**
> This ensures a **100% clean & conflict-free installation**.

---

## ✅ Step 1: Stop All Docker Services

```bash
sudo systemctl stop docker docker.socket containerd
```

---

## ✅ Step 2: Remove All Docker Packages

```bash
sudo apt purge -y docker-ce docker-ce-cli docker.io docker-buildx-plugin docker-compose-plugin containerd runc
```

---

## ✅ Step 3: Remove Unused Dependencies

```bash
sudo apt autoremove -y --purge
```

---

## ⚠️ Step 4: DELETE Docker Data (IMPORTANT)

> ❗ This will remove **all containers, images, volumes & networks**

```bash
sudo rm -rf /var/lib/docker
sudo rm -rf /var/lib/containerd
```

---

## ✅ Step 5: Remove Docker Binaries / Leftovers

```bash
sudo rm -f /usr/bin/docker
sudo rm -f /usr/local/bin/docker
sudo rm -f /usr/bin/docker-compose
```

---

## ✅ Step 6: Remove Docker APT Repo & Keys

```bash
sudo rm -f /etc/apt/sources.list.d/docker.list
sudo rm -f /etc/apt/keyrings/docker.gpg
```

---

## ✅ Step 7: Delete Docker Group (if exists)

```bash
sudo groupdel docker 2>/dev/null
```

---

## ✅ Step 8: Refresh APT Cache

```bash
sudo apt clean
sudo apt update
```

---

<p align="center">
  <img src="https://img.shields.io/badge/System-CLEAN%20%26%20READY-success?style=for-the-badge" />
</p>

🎉 **System cleaned successfully. Proceed to NEW INSTALLATION below.**

---
