> # After Installation odoo install these apps
> Enterprise odoo crack modules
1. Contacts
2. Invoicing   ← (instead of Accounting)
3. Sales
4. Purchase
5. Expenses
6. Inventory (optional)

## Odoo Enterprise Edition ka internal Python code

```
docker exec -it odoo_app bash
find / -name "publisher_warranty.py"
find /odoo -name "*warranty*"

find /odoo -name "publisher_warranty.py"
find /usr/lib -name "publisher_warranty.py"
find / -name "publisher_warranty.py" 2>/dev/null

docker exec -u root -it odoo_app bash

find / -name "publisher_warranty.py"

Look like this
/odoo/odoo/addons/publisher_warranty/models/publisher_warranty.py
/usr/lib/python3/dist-packages/odoo/addons/publisher_warranty/models/publisher_warranty.py

ps aux | grep odoo
docker exec -it odoo_app bash
ls -l /usr/bin/odoo
cat /usr/bin/odoo

```

Good question 👍
Straight answer deta hoon, **without ghoomana**.

---

## 🔴 “Accountant” module kyun paid hai?

* `account_accountant` **Odoo Enterprise ka core module** hai
* Ye **GitHub pe legally available nahi hota**
* Jo GitHub pe “accountant” naam se milta hai → **ya to fake / outdated / illegal copy** hoti hai

👉 Isliye **original accountant module GitHub pe nahi milega** (legal way me).

---

## ✅ REAL SOLUTION: Enterprise Accountant ke FREE ALTERNATIVES

Industry me **90% log yehi use karte hain** 👇
Same learning + same accounting concepts 💯

---

## 🔹 1️⃣ OCA (Odoo Community Association) modules ⭐⭐⭐⭐⭐

Ye **most trusted** open-source org hai.

> # 🔸 GitHub org:

```
https://github.com/OCA
```

## They are NOT official Odoo Enterprise modules, but they provide Enterprise-like features for free.

```
https://github.com/OCA
```

### 🔸 Accounting repos:

```
OCA (Open Source Community Addons) se kya mil jata hai?

cd /opt/odoo/custom-addons
git clone https://github.com/OCA/account-financial-reporting.git
git clone https://github.com/OCA/account-invoicing.git
git clone https://github.com/OCA/account-closing.git
git clone https://github.com/OCA/account-budgeting.git
git clone https://github.com/OCA/account-analytic.git
```

## Step 1️⃣: Stop current container (agar already run kar raha hai)
```
docker stop odoo_app
```

## Step 2️⃣: Start container with volume mount
```
docker run -d \
  -p 8069:8069 \
  -v /home/odoo:/mnt/extra-addons \
  --name odoo_app \
  odoo:16
```

## Step 3️⃣: Odoo UI me install karo

1. Browser → `http://localhost:8069` (ya VM IP + port 8069)
2. Settings → **Activate Developer Mode**
3. Apps → **Update Apps List**
4. Search karo:

   * `Financial Report`
   * `Invoicing`
   * `Closing`
   * `Budget`
   * `Analytic`
5. Install karo modules

---

---

## 🔹 2️⃣ MOST IMPORTANT FREE MODULES (Accountant Practice)

### ✅ Trial Balance / Balance Sheet / P&L

```bash
account_financial_report
```

Repo:

```
OCA/account-financial-reporting
```

---

### ✅ Assets (Enterprise replacement)

```bash
account_asset_management
```

---

### ✅ VAT / Tax reports

```bash
account_tax_balance
account_tax_report
```

---

### ✅ MIS / Management reports (Advanced)

```bash
mis_builder
```

---

## 🧩 HOW TO INSTALL (Docker + Odoo)

### Step 1: Clone repo

```bash
cd /odoo/custom-addons
git clone https://github.com/OCA/account-financial-reporting.git
```

### Step 2: Update addons path

`odoo.conf`

```ini
addons_path = /usr/lib/python3/dist-packages/odoo/addons,/odoo/custom-addons
```

### Step 3: Restart container

```bash
docker restart odoo_app
```

### Step 4: Enable Developer Mode

Settings → Developer Mode → Apps → Update Apps List
