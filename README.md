# Odoo-Setup

### Install VirtualBox - https://www.virtualbox.org/wiki/Linux_Downloads
### Download and install Ubuntu Server form - https://www.osboxes.org/
### install docker in ubuntu server form - https://docs.docker.com/engine/install/ubuntu/
### after installing successfully install Odoo inside docker - https://www.digitalocean.com/community/tutorials/how-to-install-odoo-with-docker-on-ubuntu - not follow all steps only till create mkdir

## 0. instsll all text editor in ubuntu
```
apt install vim
apt install nano
apt install gedit
```

## 1. create mkdir
```
mkdir ~/odoo
cd ~/odoo
```

## 2. make file inside this folder
```
vi docker-compose.yml
vi .env
```

## 3. inside these file paste this code
- `docker-compose.yml`

## 📄 `.env` (FULLY FILLED)

```env
# =========================
# PostgreSQL Configuration
# =========================
POSTGRES_DB=postgres
POSTGRES_USER=odoo
POSTGRES_PASSWORD=odoo123

# =========================
# Odoo Configuration
# =========================
ODOO_DB_HOST=postgres
ODOO_DB_USER=odoo
ODOO_DB_PASSWORD=odoo123
```

---

## 🐳 `docker-compose.yml` (FULLY FILLED – NO VARIABLES)

```yaml
version: '3.1'

services:
  postgres:
    image: postgres:13
    container_name: odoo_postgres
    environment:
      POSTGRES_DB: postgres
      POSTGRES_USER: odoo
      POSTGRES_PASSWORD: odoo123
    volumes:
      - odoo_db:/var/lib/postgresql/data

  odoo:
    image: odoo:15.0
    container_name: odoo_app
    depends_on:
      - postgres
    ports:
      - "8069:8069"
    environment:
      HOST: postgres
      USER: odoo
      PASSWORD: odoo123
    volumes:
      - odoo_data:/var/lib/odoo

volumes:
  odoo_db:
  odoo_data:
```

---

## ▶️ Run Commands (IMPORTANT)

1. Old data hata ke fresh start karo 👇

```bash
docker-compose down -v
```
```
docker-compose up -d
```

2. Check containers:

```bash
docker ps
```

3. Logs:

```bash
docker logs odoo_app --tail=20
```

4. check ip:
```
ip a
```
<hr>

* Odoo HTTP server **running hai**

```
http://192.168.0.101:8069/web
```

---

## 🔥 Proof #2 — Port Listening

```
0.0.0.0:8069  (docker-proxy)
[::]:8069
```

👉 Matlab:

* Port 8069 **open**
* IPv4 + IPv6 dono pe listen
* Docker networking **perfect**

---

## 🟢 FINAL STATUS (Seal of Approval)

| Component      | Status         |
| -------------- | -------------- |
| Postgres       | ✅ Connected    |
| Odoo App       | ✅ Running      |
| Docker         | ✅ Correct      |
| Port 8069      | ✅ Exposed      |
| Firewall       | ✅ Not blocking |
| Browser Access | ✅ Ready        |

---

## 🌐 Access Summary (Use THIS)

### From Host / Browser

```
http://192.168.0.101:8069
```

or

```
http://192.168.0.101:8069/web
```

### From VM Terminal

```
curl http://0.0.0.0:8069/web
```

---

## 🚀 Ab REAL GAME Shuru

Tum technically **production-ready** ho.
Next logical steps (choose one 👇):

### 🧩 1️⃣ Indian ERP Banayein

* GST
* Invoice
* TDS
* Multi-company

### ☁️ 2️⃣ AWS EC2 pe Live Host karein

* Public IP
* Domain
* HTTPS
* Backup

### 💰 3️⃣ Monthly ERP Business Model

* ₹999 / ₹1999 / ₹4999 plans
* Local shop owners target
* Demo + WhatsApp pitch

### 🛠️ 4️⃣ Custom Modules Banana

* Python + XML
* Client ke hisaab se

<hr>

> # Commands

```
docker-compose stop
docker-compose down
docker volume rm odoo_db


docker compose version
apt remove docker-compose -y
apt install docker-compose-plugin -y
docker-compose start
docker ps
docker-compose logs -f
docker logs odoo
ufw status
ufw allow 8069
apt install ufw - if have not in ubuntu
```

## Step 2: Old stopped containers clean karo
```
docker container prune -f
```

<hr>
> # Reset Password CMD

```
docker-compose down
docker-compose up -d
docker exec -it odoo_postgres psql -U odoo -d postgres -c "\l"

docker exec -it odoo_app bash
odoo shell -d abc_company --db_host=postgres --db_user=odoo --db_password=odoo123

env['res.users'].search([('login','=','admin')]).write({'password':'NewAdmin123'}
```



