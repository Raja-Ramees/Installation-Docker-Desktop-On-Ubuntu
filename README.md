 Installation-Docker-Desktop-On-Ubuntu

Install Docker Desktop on Ubuntu 22.04 / 24.04 with GUI & Terminal support.
Follow this step-by-step guide designed for beginners and pros alike.

🌟 Why Docker Desktop?

Free hardened images for developers 🛡️

Enterprise-ready for SLAs, compliance, and security 🏢

GUI + Terminal integration ⚡

Cloud-enabled Docker CLI & Docker Compose v2 ☁️

📌 Prerequisites

Ubuntu 22.04, 24.04, or latest non-LTS

x86-64 architecture

GNOME Desktop or gnome-terminal installed

sudo apt update
sudo apt install gnome-terminal -y

📥 Step 1: Download Docker Desktop

Visit the official Docker Desktop page

Select Ubuntu → Download .deb file

Default download location:

~/Downloads/docker-desktop-amd64.deb

🛠️ Step 2: Install Docker Desktop
sudo apt-get update
sudo apt install ./Downloads/docker-desktop-amd64.deb


⚠️ Ignore any warning like Download is performed unsandboxed as root – normal behavior.

Installer automatically:

Sets capabilities & resource limits

Configures Kubernetes DNS

Creates CLI symlinks for cloud integration

Default install location:

/opt/docker-desktop

🖥️ Step 3: Launch Docker Desktop
GUI Method:

Open Applications → Docker Desktop

Accept Docker Subscription Service Agreement

Docker Desktop starts

Terminal Method:

Start Docker Desktop:

systemctl --user start docker-desktop


Enable auto-start on login:

systemctl --user enable docker-desktop


Stop Docker Desktop:

systemctl --user stop docker-desktop

💻 Step 4: Verify Installation

Check Docker CLI:

docker --version
# Docker version 28.4.0, build d8eb465


Check Docker Compose:

docker compose version
# Docker Compose version v2.39.4


Test with hello-world container:

docker run hello-world


✅ If success: you’ll see a confirmation message in terminal.

🔧 Step 5: Optional - Install Latest Docker Engine via apt
sudo apt update
sudo apt install ca-certificates curl -y

sudo install -m 0755 -d /etc/apt/keyrings
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
sudo chmod a+r /etc/apt/keyrings/docker.asc

sudo tee /etc/apt/sources.list.d/docker.sources <<EOF
Types: deb
URIs: https://download.docker.com/linux/ubuntu
Suites: $(. /etc/os-release && echo "${UBUNTU_CODENAME:-$VERSION_CODENAME}")
Components: stable
Signed-By: /etc/apt/keyrings/docker.asc
EOF

sudo apt update
sudo apt install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin -y
sudo systemctl start docker
sudo docker run hello-world

🎨 Step 6: Pro Tips

Add your user to docker group to avoid sudo every time:

sudo usermod -aG docker $USER
newgrp docker


Keep Docker Desktop updated via official DEB downloads
.

Accept subscription terms in GUI to use Docker Desktop fully.

CLI binary with cloud integration is at /usr/local/bin/com.docker.cli

✅ Step 7: Conclusion

Congratulations! 🎉
You now have Docker Desktop running on Ubuntu with:

GUI & Terminal support

Cloud-enabled CLI & Docker Compose v2

Enterprise-ready features

This setup is perfect for developers, testers, and cloud workflows.
