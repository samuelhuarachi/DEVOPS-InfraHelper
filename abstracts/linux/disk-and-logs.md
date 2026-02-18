# 💾 Disco e Logs

## Limpeza de logs
find /var/log -type f -delete
sudo journalctl --vacuum-size=100M
sudo journalctl --vacuum-time=1d

## Arquivos grandes
find / -size +10M -ls

## Uso de disco
sudo du -xh / | sort -h | tail -20
