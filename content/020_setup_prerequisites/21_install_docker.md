---
title: "2. Install Docker"
chapter: true
weight: 11
---

## Install Docker
Although Docker is not needed as a container runtime in Kubernetes, it still has a role to play in the Kubernetes ecosystem, and in your workflow. Docker is still going strong as a tool for developing and building container images, as well as running them locally.

:arrow_right: Install docker via package manager
```
sudo apt-get update && sudo apt-get install docker.io -y
```

:arrow_right: Add docker daemon to startup
```
echo '# Start Docker (if not already running)
RUNNING=$(ps aux | grep dockerd | grep -v grep)
if [ -z "$RUNNING" ]; then
    sudo dockerd > /dev/null 2>&1 &
    disown
fi' >> ~/.bashrc
```

:arrow_right: Add USER to sudoers
```
echo "$USER ALL=(ALL) NOPASSWD:ALL" | sudo tee -a /etc/sudoers.d/$USER
```

:arrow_right: Add USER to docker group
```
sudo usermod -aG docker $USER
```

:arrow_right: Reboot WSL **[Powershell/CMD]**
```
wsl -t Ubuntu-20.04
wsl -d Ubuntu-20.04
```
