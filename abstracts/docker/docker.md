# 🐳 Docker

```bash
# =========================
# LIMPEZA GERAL
# =========================
docker system prune -af

# =========================
# LIMPEZA GERAL COM VOLUMES
# =========================
docker system prune -af --volumes

# =========================
# REMOVER IMAGENS NÃO UTILIZADAS
# =========================
docker image prune -a

# =========================
# LIMPAR LOGS GRANDES DOS CONTAINERS
# =========================
sudo truncate -s 0 /var/lib/docker/containers/<ID_DO_CONTAINER>/*-json.log

# =========================
# IDENTIFICAR DIRETÓRIOS GRANDES DO DOCKER
# =========================
sudo du -h --max-depth=1 /var/lib/docker

# =========================
# RESET COMPLETO DO DOCKER (HARD RESET)
# =========================
sudo systemctl stop docker
sudo mv /var/lib/docker/volumes /var/lib/docker-volumes-backup
sudo apt remove --purge -y docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
sudo rm -rf /var/lib/docker
sudo rm -rf /var/lib/containerd
curl -fsSL https://get.docker.com | sudo sh
sudo systemctl daemon-reload
sudo systemctl restart docker
sudo systemctl stop docker
sudo rm -rf /var/lib/docker/volumes
sudo mv /var/lib/docker-volumes-backup /var/lib/docker/volumes
sudo systemctl start docker

# =========================
# REMOVER BRIDGE DOCKER ÓRFÃ
# =========================
sudo ip link delete br-83f0e1280c05

# =========================
# CONFIGURAÇÃO DE ROTAÇÃO DE LOGS DO DOCKER
# =========================
sudo nano /etc/docker/daemon.json
sudo systemctl restart docker
