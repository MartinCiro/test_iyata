# Iyata - Sistema de Gestión de Proyectos y Tareas

Sistema completo full-stack para la gestión de proyectos y tareas, compuesto por un frontend en Vue.js y un backend en Laravel.

## 🏗️ Estructura del Proyecto

```
iyata/
├── frontend/     # Aplicación Vue.js (Submodule)
├── backend/      # API Laravel (Submodule)
└── README.md
```

## 📦 Componentes

### Frontend (Vue.js)
- **Tecnología**: Vue 3 + Vite
- **Puerto**: 3000
- **Repositorio**: [iyata-frontend](https://github.com/MartinCiro/iyata-frontend)

### Backend (Laravel API)
- **Tecnología**: Laravel 10 + MariaDB
- **Puerto**: 8000
- **Arquitectura**: Hexagonal (Ports & Adapters)
- **Repositorio**: [iyata-api](https://github.com/MartinCiro/iyata-api)

## 🚀 Instalación Rápida

### 1. Clonar el proyecto principal con submodules
```bash
git clone --recursive https://github.com/MartinCiro/test_iyata.git
cd test_iyata
```

### 2. Si ya clonaste sin submodules
```bash
git submodule update --init --recursive
```

## 🔄 Actualización de Proyectos

**Para actualizar todos los proyectos a sus últimas versiones:**

```bash
git submodule update --remote
```

Este comando actualizará tanto el frontend como el backend a los últimos commits de sus respectivas ramas principales.

### Actualización individual
```bash
# Actualizar solo el frontend
git submodule update --remote frontend

# Actualizar solo el backend
git submodule update --remote backend
```

## 🐳 Despliegue con Docker

### Opción A: Desplegar todo el sistema
```bash
# Backend (desde la carpeta backend)
cd backend
docker-compose up -d --build
docker-compose exec laravel_back php artisan migrate

# Frontend (desde la carpeta frontend)
cd ../frontend
docker-compose up -d --build
```

### Opción B: Desarrollo local
```bash
# Backend
cd backend
composer install
php artisan migrate
php artisan serve

# Frontend
cd ../frontend
npm install
npm run dev
```

## 🌐 URLs de la Aplicación

- **Frontend**: http://localhost:3000
- **Backend API**: http://localhost:8000
- **Documentación API**: Ver README.md en backend/

## 📚 Documentación de la API

### Autenticación
```bash
# Registro
POST /api/auth/register
{
    "name": "Usuario",
    "email": "usuario@ejemplo.com",
    "password": "password123",
    "password_confirmation": "password123"
}

# Login
POST /api/auth/login
{
    "email": "usuario@ejemplo.com",
    "password": "password123"
}
```

### Endpoints Principales
- `GET/POST /api/projects` - Gestión de proyectos
- `GET/POST /api/projects/{id}/tasks` - Gestión de tareas
- `PATCH /api/projects/{id}/status` - Actualizar estado de proyecto
- `PATCH /api/projects/{id}/tasks/{taskId}/status` - Actualizar estado de tarea

## 🛠️ Comandos de Desarrollo

### Trabajar en submodules
```bash
# Hacer cambios en un submodule
cd frontend
# Realizar modificaciones...
git add .
git commit -m "feat: nueva funcionalidad"
git push origin main

# Actualizar la referencia en el proyecto principal
cd ..
git add frontend
git commit -m "feat: actualizar frontend a última versión"
git push origin main
```

### Ver estado de submodules
```bash
# Ver commits actuales de submodules
git submodule status

# Ver diferencias
git diff --submodule
```

## 🔧 Configuración

### Variables de Entorno
Cada submodule tiene su propio archivo `.env`:
- `backend/.env` - Configuración de Laravel y base de datos
- `frontend/.env` - Configuración de Vue y API endpoints

### Base de Datos
El backend utiliza MariaDB con las siguientes credenciales por defecto:
- **Host**: localhost
- **Puerto**: 3306
- **Database**: iyata
- **Usuario**: root
- **Contraseña**: 1234

## 📁 Estructura de Archivos

```
test_iyata/
├── .gitmodules
├── frontend/                 # Submodule Vue.js
│   ├── dist/
│   ├── src/
│   ├── docker-compose.yml
│   └── package.json
├── backend/                  # Submodule Laravel
│   ├── app/
│   ├── routes/
│   ├── docker-compose.yml
│   └── composer.json
└── README.md
```

## 🐛 Solución de Problemas

### Si los submodules no se actualizan
```bash
# Forzar actualización
git submodule update --init --force
git submodule update --remote
```

### Si hay conflictos en submodules
```bash
# Actualizar cada submodule individualmente
cd frontend && git pull origin main
cd ../backend && git pull origin main
cd .. && git add frontend backend
git commit -m "fix: resolve submodule conflicts"
```

### Reclonar todo desde cero
```bash
rm -rf test_iyata
git clone --recursive https://github.com/MartinCiro/test_iyata.git
```

## 📞 Soporte

- **Frontend Issues**: [Repositorio Frontend](https://github.com/MartinCiro/iyata-frontend/issues)
- **Backend Issues**: [Repositorio Backend](https://github.com/MartinCiro/iyata-api/issues)
- **Proyecto Principal**: [Repositorio Principal](https://github.com/MartinCiro/test_iyata/issues)

---

**⚠️ Recordatorio Importante**: Después de cada pull del proyecto principal, ejecuta `git submodule update --remote` para asegurarte de tener las últimas versiones de todos los componentes.