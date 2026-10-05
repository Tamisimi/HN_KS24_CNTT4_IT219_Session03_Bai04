# Bài 4 — Nginx Virtual Hosts nhiều cổng (8080 / 8090)

## File nộp

- `multi-port.conf` — 2 server block
- `beta-app/index.html` — cổng 8080
- `internal-app/index.html` — cổng 8090

## Lệnh trên Droplet

```bash
sudo mkdir -p /var/www/beta-app/html /var/www/internal-app/html
sudo cp beta-app/index.html /var/www/beta-app/html/
sudo cp internal-app/index.html /var/www/internal-app/html/

sudo cp multi-port.conf /etc/nginx/sites-available/multi-port.conf
sudo ln -sf /etc/nginx/sites-available/multi-port.conf /etc/nginx/sites-enabled/

sudo nginx -t
sudo systemctl reload nginx

sudo ufw allow 8080/tcp
sudo ufw allow 8090/tcp
sudo ufw reload
```

DigitalOcean: **Networking → Firewalls** → mở inbound TCP **8080**, **8090**.

## Kiểm tra

```bash
curl http://<IP>:8080
curl http://<IP>:8090
```
