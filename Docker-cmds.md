> # ** Odoo + Postgres Docker project** me jo **REAL me use hue** + **future me daily kaam aane wale** Docker commands ki **complete + practical list** hai.

---

# 🐳 Docker Commands – Odoo ERP Project (Complete List)

## 📦 1. Docker Basics (Environment Check)

```bash
docker --version
docker info
docker images
docker ps
docker ps -a
```

👉 Use:

* Docker installed hai ya nahi
* Running / stopped containers dekhna

---

## 🧱 2. Docker Compose Commands (MOST IMPORTANT)

### 🔹 Start containers

```bash
docker-compose up
docker-compose up -d
```

### 🔹 Stop containers

```bash
docker-compose stop
```

### 🔹 Stop + remove containers, network

```bash
docker-compose down
```

### 🔹 Recreate containers (after env / config change)

```bash
docker-compose up -d --force-recreate
```

### 🔹 Pull latest images

```bash
docker-compose pull
```

### 🔹 Restart all services

```bash
docker-compose restart
```

### 🔹 Check compose config (debug)

```bash
docker-compose config
```

---

## 📄 3. Container Logs (Debugging)

### 🔹 Odoo logs

```bash
docker logs odoo_app
docker logs odoo_app --tail=50
docker logs odoo_app -f
```

### 🔹 Postgres logs

```bash
docker logs odoo_postgres
```

👉 Used to fix:

* DB connection error
* Password mismatch
* Port issues

---

## 🔐 4. Exec into Containers (VERY IMPORTANT)

### 🔹 Enter Odoo container

```bash
docker exec -it odoo_app bash
```

### 🔹 Enter Postgres container

```bash
docker exec -it odoo_postgres bash
```

### 🔹 Connect Postgres manually

```bash
psql -U odoo -d postgres
```

---

## 🌐 5. Networking & Port Check

### 🔹 Check exposed ports

```bash
docker ps
```

### 🔹 Verify port listening

```bash
ss -tulnp | grep 8069
```

### 🔹 Test service

```bash
curl http://localhost:8069
curl http://127.0.0.1:8069
```

---

## 💾 6. Volume Commands (Data Safety)

### 🔹 List volumes

```bash
docker volume ls
```

### 🔹 Inspect volume

```bash
docker volume inspect odoo_db
```

### 🔹 Remove unused volumes

```bash
docker volume prune
```

⚠️ **Danger (DB data delete)**

```bash
docker-compose down -v
```

---

## 🧹 7. Cleanup Commands

### 🔹 Remove stopped containers

```bash
docker container prune -f
```

### 🔹 Remove unused images

```bash
docker image prune
```

### 🔹 Full cleanup

```bash
docker system prune
```

---

## 🧪 8. Debug / Troubleshooting Commands

### 🔹 Check container details

```bash
docker inspect odoo_app
```

### 🔹 Check environment variables

```bash
docker exec odoo_app env
```

### 🔹 Check network

```bash
docker network ls
docker network inspect odoo_default
```

---

## 🏗️ 9. Images Used in This Project

```bash
docker pull odoo:15.0
docker pull postgres:13
```

---

## 📁 10. Project Folder Structure (Reference)

```bash
odoo/
├── docker-compose.yml
├── .env
├── addons/          # future custom modules
├── config/          # odoo.conf (optional)
```

---

## 🎯 Interview-Ready One-Liners (Use These 🔥)

* **docker-compose up -d**
  → Start multi-container app in background

* **docker logs**
  → Debug runtime issues

* **docker exec -it**
  → Access running container

* **Volumes**
  → Persist Postgres & Odoo data

* **Ports**
  → Expose Odoo on 8069

---
