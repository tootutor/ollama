# Ollama with GPU and Opem WebUI / Anything LLM

## Install Nvidia driver in debian

### Edit repositories
```
sudo nano /etc/apt/sources.list
```

### Add repositories
```
deb http://deb.debian.org/debian bookworm main contrib non-free non-free-firmware
deb http://security.debian.org/debian-security bookworm-security main contrib non-free non-free-firmware
deb http://deb.debian.org/debian bookworm-updates main contrib non-free non-free-firmware
```

### Update packages list
```
sudo apt update
```

### Install NVIDIA driver
```
sudo apt install -y nvidia-driver firmware-misc-nonfree
```

### Reboot
```
sudo reboot
```

### Verfiy
```
nvidia-smi
```

## Install NVIDIA contrainer toolkit

### Config the repositories
```
curl -fsSL https://nvidia.github.io/libnvidia-container/gpgkey | sudo gpg --dearmor -o /usr/share/keyrings/nvidia-container-toolkit-keyring.gpg \
  && curl -s -L https://nvidia.github.io/libnvidia-container/stable/deb/nvidia-container-toolkit.list | \
    sed 's#deb https://#deb [signed-by=/usr/share/keyrings/nvidia-container-toolkit-keyring.gpg] https://#g' | \
    sudo tee /etc/apt/sources.list.d/nvidia-container-toolkit.list
```

### Update packgage list
```
sudo apt-get update
```

### Install the NVIDIA Container Toolkit Packages
```
sudo apt-get install -y nvidia-container-toolkit
```

### Reboot
```
sudo reboot
```

## Up and run Ollama with Open WebUI / Anything LLM

### Create container
```
docker compose up -d
```

### Attach to container
```
docker exec -it ollama bash
```

### Verify inside container
```
nvidia-smi
```
 
## Access the UIs
Open Web UI : http://hostname:3000
Anything LLM : http://hostname:3001

