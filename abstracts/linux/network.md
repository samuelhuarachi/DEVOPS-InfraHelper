# 🌐 Network

## Consumo de dados por interface
cat /sys/class/net/tun293/statistics/tx_bytes
cat /sys/class/net/tun293/statistics/rx_bytes

## IPv6
/sbin/ip -6 route add <ipv6network>/<prefixlength> dev <device>
/sbin/ip -6 route show

## Forwarding
sudo sysctl -w net.ipv4.ip_forward=1
