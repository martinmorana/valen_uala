# Ualá Junior Plus

Aplicación de educación financiera gamificada para adolescentes con supervisión parental y marketplace B2B.

## 🚀 Inicio Rápido

### Prerrequisitos
- Docker Desktop instalado
- Git

### Levantar el proyecto completo

```bash
# Clonar y entrar al directorio
git clone <repo-url>
cd Valen_uala

# Levantar todos los servicios
docker-compose up --build
```

### Servicios disponibles

Una vez levantado, tendrás acceso a:

- **API Backend**: http://localhost:3000
- **Panel Parental (Web)**: http://localhost:3001  
- **Panel Admin**: http://localhost:3002
- **Base de datos (Adminer)**: http://localhost:8080

### Cuentas de prueba

**Para Panel Parental:**
- Email: `parent@test.com`
- Password: `password`

**Para Panel Admin:**
- Email: `admin@uala.com`  
- Password: `password`

**Usuario Junior (para testing API):**
- Email: `junior@test.com`
- Password: `password`

## 📱 Arquitectura

```
┌─────────────────┐    ┌─────────────────┐    ┌─────────────────┐
│   Frontend Web  │    │   Admin Panel   │    │  Mobile App     │
│   (Parental)    │    │                 │    │  (Junior)       │
│   Port: 3001    │    │   Port: 3002    │    │  (React Native) │
└─────────────────┘    └─────────────────┘    └─────────────────┘
         │                       │                       │
         └───────────────────────┼───────────────────────┘
                                 │
                    ┌─────────────────┐
                    │   Backend API   │
                    │   Port: 3000    │
                    └─────────────────┘
                                 │
                    ┌─────────────────┐    ┌─────────────────┐
                    │   PostgreSQL    │    │     Redis       │
                    │   Port: 5432    │    │   Port: 6379    │
                    └─────────────────┘    └─────────────────┘
```

## 🛠️ Desarrollo

### Backend (Node.js + TypeScript)
```bash
cd backend
npm install
npm run dev
```

### Frontend Web (React)
```bash
cd frontend-web  
npm install
npm start
```

### Admin Panel (React)
```bash
cd admin-panel
npm install
npm start
```

## 📊 Base de Datos

La base de datos se inicializa automáticamente con:
- Esquema completo de tablas
- Datos de prueba (usuarios, misiones, partners)
- Índices para performance

**Acceso a Adminer**: http://localhost:8080
- Server: `postgres`
- Username: `postgres`
- Password: `postgres123`
- Database: `uala_junior`

## 🔑 API Endpoints

### Autenticación
- `POST /auth/register` - Registro de usuarios
- `POST /auth/login` - Login
- `POST /auth/invite-parent` - Generar código de vinculación
- `POST /auth/accept-link` - Aceptar vinculación padre-hijo

### Misiones (Junior)
- `GET /missions` - Obtener misiones de la semana
- `POST /missions/:id/progress` - Actualizar progreso
- `GET /missions/badges/me` - Obtener badges del usuario

### Metas de Ahorro
- `POST /goals` - Crear meta
- `GET /goals/me` - Obtener metas del usuario
- `PATCH /goals/:id` - Actualizar progreso de meta

### Marketplace
- `GET /marketplace/catalog` - Catálogo de productos
- `POST /marketplace/redeem/:itemId` - Canjear producto
- `GET /marketplace/redeem/history` - Historial de canjes

### Panel Parental
- `GET /parent/dashboard` - Dashboard con actividad del junior
- `GET /parent/juniors` - Lista de juniors vinculados

### Admin
- `GET /admin/missions` - CRUD de misiones
- `GET /admin/partners` - CRUD de partners
- `GET /admin/analytics` - Estadísticas de la plataforma

## 🎯 Funcionalidades MVP

### ✅ Implementado
- [x] Autenticación dual (Junior/Parent/Admin)
- [x] Sistema de vinculación padre-hijo
- [x] Misiones educativas con puntos
- [x] Metas de ahorro
- [x] Marketplace simulado con canjes
- [x] Dashboard parental
- [x] Panel administrativo
- [x] Base de datos completa
- [x] API REST funcional

### 🚧 En desarrollo
- [ ] App móvil React Native
- [ ] Sistema de badges automático
- [ ] Notificaciones push
- [ ] Reportes descargables
- [ ] Validación de evidencias

## 🔒 Seguridad

- JWT con expiración de 24h
- Passwords hasheados con bcrypt
- CORS configurado
- Validación de datos con Zod
- Roles y permisos RBAC

## 📱 App Móvil (Próximamente)

La app móvil para usuarios Junior se desarrollará con:
- React Native + Expo
- Navegación nativa
- Notificaciones push
- Cámara para evidencias
- Modo offline básico

## 🧪 Testing

```bash
# Backend tests
cd backend
npm test

# Frontend tests  
cd frontend-web
npm test
```

## 📈 Monitoreo

- Logs estructurados en consola
- Health check en `/health`
- Métricas básicas en admin panel

## 🚀 Despliegue

Para producción:
```bash
# Build optimizado
docker-compose -f docker-compose.prod.yml up --build

# Variables de entorno
cp .env.example .env
# Editar .env con valores de producción
```

## 📞 Soporte

Para issues y bugs, crear un ticket en el repositorio con:
- Descripción del problema
- Pasos para reproducir
- Logs relevantes
- Entorno (desarrollo/producción)

---

**Desarrollado para Ualá** 🚀
