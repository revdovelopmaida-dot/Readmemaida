# 🚀 Full-Stack App on DigitalOcean App Platform

![DigitalOcean](https://img.shields.io/badge/DigitalOcean-App%20Platform-0080FF?style=for-the-badge&logo=digitalocean&logoColor=white)
![License](https://img.shields.io/badge/License-MIT-green?style=for-the-badge)
![Status](https://img.shields.io/badge/Status-Active-brightgreen?style=for-the-badge)
![GitHub](https://img.shields.io/badge/GitHub-Repository-black?style=for-the-badge&logo=github)

---

## 🛠️ Tech Stack

![React](https://img.shields.io/badge/Frontend-React-61DAFB?style=flat-square&logo=react&logoColor=white)
![Node.js](https://img.shields.io/badge/Backend-Node.js-43853D?style=flat-square&logo=node.js&logoColor=white)
![Express](https://img.shields.io/badge/API-Express.js-000000?style=flat-square&logo=express&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/Database-PostgreSQL-336791?style=flat-square&logo=postgresql&logoColor=white)
![Git](https://img.shields.io/badge/Version%20Control-Git-F05032?style=flat-square&logo=git&logoColor=white)
![GitHub](https://img.shields.io/badge/Repository-GitHub-181717?style=flat-square&logo=github&logoColor=white)

---

## 📝 Deskripsi

Template README ini menjelaskan cara menjalankan dan mendeploy aplikasi **full‑stack** (frontend + backend + database) ke **DigitalOcean App Platform** (hosting terkelola, auto deploy, autoscaling, bayar sesuai pemakaian).

✨ **Fitur Utama:**
- ✅ Frontend, backend, dan database dalam satu platform
- ✅ Penyebaran otomatis tanpa downtime (rolling deploy)
- ✅ Skalakan secara otomatis sesuai traffic
- ✅ Bayar sesuai penggunaan (pay-as-you-go)
- ✅ Database terkelola terintegrasi

---

## 📁 Struktur Proyek (Monorepo Contoh)

```txt
.
├── frontend/               # React / Next / Vue / dll
│   ├── src/
│   ├── package.json
│   ├── vite.config.js      # atau webpack.config.js
│   └── ...
├── backend/                # Node / Express / Django / Laravel / dll
│   ├── src/
│   ├── package.json
│   ├── server.js           # entry point
│   └── ...
├── .gitignore
├── README.md               # File ini
└── app.yaml                # (opsional) config DigitalOcean App Platform
```

- **frontend**: aplikasi web (SPA/SSR) dengan `package.json` dan script `build` + `start`.
- **backend**: REST API / server dengan satu entry command (misalnya `npm start`, `gunicorn`, dsb).

---

## 🧑‍💻 Menjalankan Secara Lokal

### 1. Prasyarat

- ![Git](https://img.shields.io/badge/Git-2.40%2B-F05032?style=flat-square&logo=git)
- ![Node.js](https://img.shields.io/badge/Node.js-18%2B-43853D?style=flat-square&logo=node.js)
- ![npm](https://img.shields.io/badge/npm-9%2B-CB3837?style=flat-square&logo=npm)
- Database lokal atau akses ke managed database (PostgreSQL/MySQL)

**Instalasi:**

**Linux:**
```bash
# Ubuntu / Debian
sudo apt-get install -y git nodejs npm

# Cek versi
git --version
node --version
npm --version
```

**Windows (PowerShell as Administrator):**
```powershell
# Gunakan Chocolatey atau unduh langsung dari website
# Dengan Chocolatey:
choco install git nodejs

# Cek versi
git --version
node --version
npm --version
```

---

### 2. Clone Repository

#### Linux (Bash/Zsh)

```bash
# Clone repo
git clone https://github.com/USERNAME/NAMA-REPO.git
cd NAMA-REPO

# Cek status
git status

# Lihat branch tersedia
git branch -a
```

#### Windows (PowerShell)

```powershell
# Clone repo
git clone https://github.com/USERNAME/NAMA-REPO.git
cd NAMA-REPO

# Cek status
git status

# Lihat branch tersedia
git branch -a
```

---

### 3. Setup Backend

> Sesuaikan dengan bahasa/framework backend Anda (contoh Node.js + Express).

#### Linux

```bash
# Masuk folder backend
cd backend

# Install dependency
npm install

# Buat file .env
cat > .env << EOF
NODE_ENV=development
PORT=8080
DATABASE_URL="postgres://user:password@localhost:5432/namadb"
JWT_SECRET="your-secret-key"
EOF

# Jalankan migrasi database (jika ada)
npm run migrate

# Jalankan server
npm start
# Output: Server berjalan di http://localhost:8080
```

#### Windows (PowerShell)

```powershell
# Masuk folder backend
cd backend

# Install dependency
npm install

# Buat file .env
@"
NODE_ENV=development
PORT=8080
DATABASE_URL="postgres://user:password@localhost:5432/namadb"
JWT_SECRET="your-secret-key"
"@ | Out-File -Encoding UTF8 .env

# Jalankan migrasi database (jika ada)
npm run migrate

# Jalankan server
npm start
# Output: Server berjalan di http://localhost:8080
```

**Endpoint Backend (contoh):**
```
http://localhost:8080/api/users
http://localhost:8080/api/posts
http://localhost:8080/api/auth/login
```

---

### 4. Setup Frontend

> Sesuaikan dengan tool (React/Next/Vite/dll).

#### Linux

```bash
# Kembali ke root dan masuk frontend
cd ../frontend

# Install dependency
npm install

# Buat file .env
cat > .env.local << EOF
VITE_API_URL=http://localhost:8080
VITE_APP_NAME=MyApp
EOF

# Jalankan dev server
npm run dev
# Output: Frontend tersedia di http://localhost:5173 (atau port lain)
```

#### Windows (PowerShell)

```powershell
# Kembali ke root dan masuk frontend
cd ../frontend

# Install dependency
npm install

# Buat file .env.local
@"
VITE_API_URL=http://localhost:8080
VITE_APP_NAME=MyApp
"@ | Out-File -Encoding UTF8 .env.local

# Jalankan dev server
npm run dev
# Output: Frontend tersedia di http://localhost:5173 (atau port lain)
```

**Buka di browser:**
```
http://localhost:5173
```

---

## ☁️ Deploy ke DigitalOcean App Platform

> Anda memerlukan akun [DigitalOcean](https://www.digitalocean.com) dan minimal 1 project.

### Persyaratan Deployment

![DigitalOcean Account](https://img.shields.io/badge/Butuh-DigitalOcean%20Account-0080FF?style=flat-square)
![GitHub Account](https://img.shields.io/badge/Butuh-GitHub%20Account-181717?style=flat-square)
![Git Knowledge](https://img.shields.io/badge/Skill-Git%20Basics-F05032?style=flat-square)

---

### 1. Siapkan Repository GitHub

#### Linux

```bash
# Inisialisasi git (jika belum)
git init
git add .
git commit -m "Initial commit: full-stack app setup"

# Tambah remote origin
git remote add origin https://github.com/USERNAME/NAMA-REPO.git

# Push ke GitHub
git branch -M main
git push -u origin main
```

#### Windows (PowerShell)

```powershell
# Inisialisasi git (jika belum)
git init
git add .
git commit -m "Initial commit: full-stack app setup"

# Tambah remote origin
git remote add origin https://github.com/USERNAME/NAMA-REPO.git

# Push ke GitHub
git branch -M main
git push -u origin main
```

---

### 2. Buat App di App Platform

1. Buka **[DigitalOcean Control Panel](https://cloud.digitalocean.com)** → **Create → Apps**.
2. Hubungkan ke GitHub/GitLab/Bitbucket.
3. Pilih repository ini dan branch `main`.
4. DigitalOcean akan mencoba mendeteksi komponen secara otomatis.

---

### 3. Konfigurasi Komponen Frontend

**Settings di App Platform:**

| Parameter | Nilai |
|-----------|-------|
| **Type** | Static Site (untuk SPA) atau Web Service (untuk SSR) |
| **Source Directory** | `./frontend` |
| **Build Command** | `npm install && npm run build` |
| **Output Directory** | `dist` atau `build` (sesuaikan) |
| **Run Command** | `npm start` (untuk SSR) |
| **HTTP Route Path** | `/` |
| **Domain** | `namaapp.ondigitalocean.app` atau custom domain |

**Contoh Build Command untuk berbagai tools:**

```bash
# Vite + React
npm install && npm run build

# Next.js (static export)
npm install && npm run build

# Create React App
npm install && npm run build

# Vue + Vite
npm install && npm run build
```

---

### 4. Konfigurasi Komponen Backend (API)

**Settings di App Platform:**

| Parameter | Nilai |
|-----------|-------|
| **Type** | Web Service |
| **Source Directory** | `./backend` |
| **Build Command** | `npm install` |
| **Run Command** | `npm start` |
| **HTTP Port** | `8080` (sesuaikan dengan aplikasi) |
| **Route Path** | `/api` atau `/` |
| **Domain** | `api-namaapp.ondigitalocean.app` atau subdomain |

**Contoh Run Command untuk berbagai framework:**

```bash
# Node.js + Express
npm start

# Django
gunicorn config.wsgi:application

# Laravel
php artisan serve

# Python Flask
python app.py
```

---

## 🗄️ Database Terkelola (Managed Database)

### 1. Membuat Cluster Database

#### Linux / Windows

1. Buka **[DigitalOcean Control Panel](https://cloud.digitalocean.com)** → **Create → Databases**.
2. Pilih engine:
   - ![PostgreSQL](https://img.shields.io/badge/PostgreSQL-13%2B-336791?style=flat-square&logo=postgresql) (rekomendasi untuk Node.js)
   - ![MySQL](https://img.shields.io/badge/MySQL-8.0%2B-00758F?style=flat-square&logo=mysql&logoColor=white)
3. Tentukan ukuran dan jumlah node sesuai kebutuhan.
4. Tunggu cluster selesai dibuat (~5 menit).

---

### 2. Menghubungkan ke App Platform

#### Langkah-langkah:

```
1. Buka halaman App → tab "Components"
   ↓
2. Klik "Add Component" → "Create or attach database"
   ↓
3. Pilih database cluster yang sudah dibuat
   ↓
4. Pilih database dan user
   ↓
5. Klik "Attach Database"
   ↓
6. DigitalOcean otomatis menambah environment variable
```

**Environment Variable yang ditambahkan:**

```bash
DATABASE_URL="postgresql://doadmin:xxxpasswordxxx@db-xxx.ondigitalocean.com:25060/defaultdb?sslmode=require"
```

---

### 3. Menggunakan Database URL di Backend

#### Contoh Node.js + pg:

```javascript
// backend/src/db.js
const { Pool } = require('pg');

const pool = new Pool({
  connectionString: process.env.DATABASE_URL,
  ssl: { rejectUnauthorized: false } // untuk DigitalOcean managed DB
});

module.exports = pool;
```

#### Contoh dengan sequelize (ORM):

```javascript
// backend/config/database.js
module.exports = {
  development: {
    url: process.env.DATABASE_URL || 'postgres://...',
    dialect: 'postgres'
  },
  production: {
    url: process.env.DATABASE_URL,
    dialect: 'postgres',
    ssl: { rejectUnauthorized: false }
  }
};
```

---

## ⚙️ Environment Variables

### Frontend Environment Variables

```bash
# .env atau .env.production
VITE_API_URL=https://api-namaapp.ondigitalocean.app
VITE_APP_NAME=MyApp
VITE_APP_VERSION=1.0.0
VITE_ENABLE_ANALYTICS=true
```

### Backend Environment Variables

```bash
# .env (development)
NODE_ENV=development
PORT=8080
DATABASE_URL=postgres://user:password@localhost:5432/dbname
JWT_SECRET=your-secret-key-development
CORS_ORIGIN=http://localhost:5173

# .env (production di DigitalOcean)
NODE_ENV=production
PORT=8080
DATABASE_URL=${DATABASE_URL}  # dari managed database DigitalOcean
JWT_SECRET=${JWT_SECRET}     # set di App Platform → Settings
CORS_ORIGIN=https://namaapp.ondigitalocean.app
```

### Cara Mengatur di App Platform

```
1. Buka App → "Settings" tab
   ↓
2. Scroll ke "Environment Variables"
   ↓
3. Klik "Edit" dan tambah variable
   ↓
4. Pilih komponen yang memakai variable tersebut
   ↓
5. Klik "Save"
   ↓
6. App akan otomatis redeploy
```

---

## 🔁 Auto Deploy & Zero Downtime

### Mengaktifkan Auto Deploy

```
1. Buka App → "Settings" tab
   ↓
2. Scroll ke "Deploy on Push"
   ↓
3. Toggle ON untuk branch yang ingin auto-deploy (mis. main)
   ↓
4. Pilih "Production" environment
   ↓
5. Klik "Save"
```

### Workflow Deploy Otomatis

```
Local Development
    ↓
git commit & git push ke main
    ↓
GitHub webhook → DigitalOcean App Platform
    ↓
Build & Test (5-10 menit)
    ↓
Rolling Deploy (tanpa downtime)
    ↓
✅ Live di production
```

---

## 📈 Autoscaling & Biaya

### Mengatur Autoscaling

Untuk setiap komponen (frontend/backend):

```
1. Buka App → "Components" → pilih komponen
   ↓
2. Klik "Edit" → scroll ke "Scaling"
   ↓
3. Atur instance:
   - Min instances: 1 (atau 2 untuk HA)
   - Max instances: 3-5 (sesuaikan budget)
   ↓
4. Klik "Save"
```

### Perhitungan Biaya

| Komponen | Ukuran | Harga/jam | Keterangan |
|----------|--------|-----------|------------|
| Frontend (Static) | 128 MB | $0.00595 | Setiap instance |
| Backend | 512 MB | $0.01488 | Setiap instance |
| PostgreSQL | 1 CPU, 1 GB | $0.01786 | Per jam |

**Contoh untuk setup kecil:**
- 1 instance frontend + 1 instance backend + 1 node PostgreSQL ≈ **$8-12/bulan**

> 💡 **Tip**: Mulai dengan setup minimal, monitor, lalu scale up sesuai traffic.

---

## 🧪 Monitoring & Debugging

### View Logs di App Platform

#### Linux / Windows

```bash
# Gunakan DigitalOcean CLI (doctl)
# Instalasi: https://github.com/digitalocean/doctl

doctl apps list
doctl apps describe APP_ID
doctl apps logs APP_ID --component backend
doctl apps logs APP_ID --component frontend
```

#### Web UI

```
1. Buka App di control panel
   ↓
2. Tab "Logs"
   ↓
3. Pilih komponen (frontend/backend)
   ↓
4. Lihat output logs real-time
```

### Health Checks

Pastikan endpoint health-check tersedia di backend:

```bash
# GET /health atau /api/health
curl https://api-namaapp.ondigitalocean.app/health

# Response:
# { "status": "ok", "timestamp": "2026-01-09T10:44:00Z" }
```

---

## ✅ Testing & Best Practice

### Pre-Deployment Checklist

```bash
# ✓ Cek dependency
npm list --depth=0

# ✓ Lint code
npm run lint

# ✓ Build frontend
cd frontend && npm run build

# ✓ Build backend (jika ada)
cd ../backend && npm run build

# ✓ Run tests
npm test

# ✓ Cek environment variables
cat .env

# ✓ Git status clean
git status
```

### Staging Environment

Sebelum deploy ke production, gunakan staging app:

```
1. Buat branch: git checkout -b staging
2. Buat app baru di DigitalOcean dari branch staging
3. Test semua fitur
4. Merge ke main jika OK
5. Production app otomatis update via auto-deploy
```

### Best Practice

- ✅ Simpan semua secret (API key, password) di environment variables
- ✅ Gunakan `.env.example` untuk dokumentasi variable yang dibutuhkan
- ✅ Jangan commit file `.env` ke git (tambahkan di `.gitignore`)
- ✅ Dokumentasikan endpoint API di README atau Postman
- ✅ Gunakan database migration untuk schema management
- ✅ Implement error handling dan logging yang baik
- ✅ Monitoring cost dan autoscaling behavior

---

## 📚 Resources & Documentation

| Resource | Link |
|----------|------|
| **DigitalOcean App Platform** | https://docs.digitalocean.com/products/app-platform/ |
| **Sample Apps** | https://docs.digitalocean.com/products/app-platform/getting-started/sample-apps/ |
| **Database Management** | https://docs.digitalocean.com/products/app-platform/how-to/manage-databases/ |
| **Managed Databases** | https://docs.digitalocean.com/products/databases/ |
| **DigitalOcean CLI (doctl)** | https://docs.digitalocean.com/reference/doctl/ |

---

## 🔚 Ringkasan Perintah Cepat

### Linux (Bash/Zsh)

```bash
# ═══════════════════════════════════════════════
# SETUP & RUN LOKAL
# ═══════════════════════════════════════════════

# Clone repo
git clone https://github.com/USERNAME/NAMA-REPO.git
cd NAMA-REPO

# Backend
cd backend
npm install
export DATABASE_URL="postgres://user:pass@localhost:5432/db"
export NODE_ENV=development
npm start  # localhost:8080

# ────────────────────────────────────────────────
# Buka terminal baru
# ────────────────────────────────────────────────

# Frontend
cd ../frontend
npm install
export VITE_API_URL=http://localhost:8080
npm run dev  # localhost:5173

# ═══════════════════════════════════════════════
# DEPLOYMENT KE GITHUB
# ═══════════════════════════════════════════════

git add .
git commit -m "Setup: full-stack app"
git push origin main

# Kemudian setup di App Platform (via web UI)
```

### Windows (PowerShell)

```powershell
# ═══════════════════════════════════════════════
# SETUP & RUN LOKAL
# ═══════════════════════════════════════════════

# Clone repo
git clone https://github.com/USERNAME/NAMA-REPO.git
cd NAMA-REPO

# Backend
cd backend
npm install
$env:DATABASE_URL="postgres://user:pass@localhost:5432/db"
$env:NODE_ENV="development"
npm start  # localhost:8080

# ────────────────────────────────────────────────
# Buka PowerShell baru (tetap di repo root)
# ────────────────────────────────────────────────

# Frontend
cd frontend
npm install
$env:VITE_API_URL="http://localhost:8080"
npm run dev  # localhost:5173

# ═══════════════════════════════════════════════
# DEPLOYMENT KE GITHUB
# ═══════════════════════════════════════════════

git add .
git commit -m "Setup: full-stack app"
git push origin main

# Kemudian setup di App Platform (via web UI)
```

---

## 🐛 Troubleshooting

### Build gagal di App Platform

```
❌ Error: "npm: command not found"
✅ Solusi: Pastikan Node.js version >= 18 di app settings

❌ Error: "Cannot find module 'xxx'"
✅ Solusi: Jalankan "npm install" di build command

❌ Error: "Database connection timeout"
✅ Solusi: Cek DATABASE_URL di environment variables,
         atau pastikan database cluster sudah running
```

### Aplikasi crash setelah deploy

```
1. Lihat logs: App → "Logs" tab
2. Cek error message
3. Fix di local, push ke GitHub
4. Auto-deploy akan run otomatis
5. Monitor logs sampai OK
```

### Biaya tiba-tiba naik

```
1. Cek App → "Insights" tab untuk resource usage
2. Review autoscaling settings
3. Kurangi max instances jika tidak perlu
4. Cek database size dan cleanup data lama
5. Pertimbangkan upgrade plan jika traffic tinggi
```

---

## 📞 Support & Kontak

- 💬 **Issues & Bugs**: Buka [GitHub Issues](https://github.com/USERNAME/NAMA-REPO/issues)
- 📧 **Email**: your-email@example.com
- 💼 **Documentation**: Lihat folder `/docs` di repository

---

## 📄 Lisensi

![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg?style=flat-square)

Proyek ini dilisensikan di bawah **MIT License** - lihat file [LICENSE](LICENSE) untuk detail.

---

## 🙏 Acknowledgments

- ![DigitalOcean](https://img.shields.io/badge/Powered%20by-DigitalOcean-0080FF?style=flat-square&logo=digitalocean)
- ![React](https://img.shields.io/badge/Frontend-React-61DAFB?style=flat-square&logo=react)
- ![Node.js](https://img.shields.io/badge/Backend-Node.js-43853D?style=flat-square&logo=node.js)

---

## 🚀 Next Steps

1. ✅ Baca section "Menjalankan Secara Lokal"
2. ✅ Setup backend dan frontend di komputer Anda
3. ✅ Buat akun DigitalOcean jika belum
4. ✅ Push ke GitHub
5. ✅ Deploy ke App Platform via web UI
6. ✅ Test endpoint dan monitoring logs
7. ✅ Share aplikasi live ke publik! 🎉

---

**Last Updated**: 2026-01-09  
**Version**: 1.0.0  
**Status**: ![Status](https://img.shields.io/badge/Status-Active-brightgreen?style=flat-square)
