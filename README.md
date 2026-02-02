Installation Docker Desktop on Ubuntu
🌟 What You Will Achieve

✅ Install Docker Desktop on Ubuntu step‑by‑step
✅ Use GUI + Terminal together
✅ Proper Docker repository setup using .sh script
✅ Verify Docker, Docker Compose & CLI

🟢 STEP 1: Go to Docker Website

🌐 Open browser and go to:

👉 https://www.docker.com

Actions:

Put your cursor on Download Docker Desktop

Click Docker Desktop for Linux

Choose Ubuntu

📌 Keep this page open

🟢 STEP 2: Read Installation Instructions

On the same page, scroll to:

Install Docker Desktop on Ubuntu

You will see:

Recommended approach to install Docker Desktop on Ubuntu

👉 Click “Install using the apt repository”

📋 COPY the repository setup code (we will paste it in a script)

🟢 STEP 3: Create Installation Script (.sh)
Open Terminal
cd ~/Downloads
Create script file
touch install-docker-desktop.sh
Open file in editor
nano install-docker-desktop.sh
Paste this code inside 👇
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

Save & exit:

CTRL + O → ENTER → CTRL + X
🟢 STEP 4: Run the Script
Give permission
chmod 700 install-docker-desktop.sh
Run script
./install-docker-desktop.sh

✅ Docker repository is now configured correctly

🟢 STEP 5: Download Docker Desktop (.deb)

Go back to Docker website

👉 Click:

Download the latest DEB package

📥 File will download to:

~/Downloads/docker-desktop-amd64.deb
🟢 STEP 6: Install Docker Desktop

In terminal:

sudo apt-get update
sudo apt install ./docker-desktop-amd64.deb
⚠️ IMPORTANT NOTE

You may see this warning (IGNORE IT):

N: Download is performed unsandboxed as root
Permission denied

✔️ This is normal & safe

📍 Installed location:

/opt/docker-desktop
🟢 STEP 7: What Installer Does Automatically

✔ Maps privileged ports
✔ Sets resource limits
✔ Adds Kubernetes DNS to /etc/hosts
✔ Creates Docker CLI symlink

/usr/local/bin/com.docker.cli → /usr/bin/docker
🟢 STEP 8: Launch Docker Desktop
🎨 GUI Method

Open Applications

Click Docker Desktop

Accept Docker Subscription Agreement

🚨 Docker Desktop will NOT start without accepting terms

⚡ Terminal Method
systemctl --user start docker-desktop

Enable auto‑start on login:

systemctl --user enable docker-desktop

Stop Docker Desktop:

systemctl --user stop docker-desktop
🟢 STEP 9: Verify Installation
docker compose version
docker --version
docker version

Expected output example:

Docker Compose version v2.39.4
Docker version 28.4.0
🎉 SUCCESS! YOU ARE DONE

✅ Docker Desktop GUI
✅ Docker CLI
✅ Docker Compose v2
✅ Enterprise‑ready setup

❤️ Final Words

This guide is beginner‑proof, production‑ready, and future‑safe.

📌 Share this repo with your team — anyone can install Docker Desktop in minutes.
