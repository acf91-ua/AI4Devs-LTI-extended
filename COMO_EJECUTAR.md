# 🚀 Guía Rápida - Cómo Ejecutar el Proyecto LTI ATS

## Pasos después de reiniciar el PC

### 1️⃣ Iniciar Docker Desktop
```
- Abre Docker Desktop desde el menú de inicio de Windows
- Espera a que el ícono de Docker en la bandeja del sistema esté verde
- Esto puede tomar 1-2 minutos
```

### 2️⃣ Iniciar la Base de Datos PostgreSQL
```bash
# Desde la raíz del proyecto
cd c:\Users\alber\AI4Devs-LTI-extended
docker-compose up -d
```

**Verificar que esté corriendo:**
```bash
docker-compose ps
```
Deberías ver `ai4devs-lti-extended-db-1` con estado `Up`

### 3️⃣ Iniciar el Backend
```bash
# Abrir una terminal en el backend
cd c:\Users\alber\AI4Devs-LTI-extended\backend
npm run dev
```

**Resultado esperado:**
```
Server is running at http://localhost:3010
```

### 4️⃣ Iniciar el Frontend
```bash
# Abrir OTRA terminal en el frontend
cd c:\Users\alber\AI4Devs-LTI-extended\frontend
npm start
```

**Resultado esperado:**
- Se abrirá automáticamente el navegador en `http://localhost:3000`
- O puedes abrir manualmente: http://localhost:3000

---

## 🎯 Resumen Rápido (Comandos en Orden)

```bash
# Terminal 1 - Base de datos
cd c:\Users\alber\AI4Devs-LTI-extended
docker-compose up -d

# Terminal 2 - Backend
cd c:\Users\alber\AI4Devs-LTI-extended\backend
npm run dev

# Terminal 3 - Frontend
cd c:\Users\alber\AI4Devs-LTI-extended\frontend
npm start
```

---

## 🌐 URLs de Acceso

- **Frontend (Aplicación Web):** http://localhost:3000
- **Backend (API):** http://localhost:3010
- **Base de Datos PostgreSQL:** localhost:5432

---

## 🛑 Detener el Proyecto

### Detener Backend y Frontend
- Presiona `Ctrl + C` en cada terminal

### Detener la Base de Datos
```bash
cd c:\Users\alber\AI4Devs-LTI-extended
docker-compose down
```

---

## ⚠️ Solución de Problemas Comunes

### Error: "Cannot connect to database"
- Verifica que Docker Desktop esté corriendo
- Ejecuta: `docker-compose ps` para verificar que la DB esté activa

### Error: "Port 3010 already in use"
- El backend ya está corriendo en otra terminal
- Cierra la terminal anterior o usa `Ctrl + C`

### Error: "Port 3000 already in use"
- El frontend ya está corriendo
- Cierra la terminal anterior o usa `Ctrl + C`

### Frontend no carga / Pantalla en blanco
- Verifica que el backend esté corriendo en el puerto 3010
- Revisa la consola del navegador (F12) para ver errores

---

## 📝 Notas Importantes

- **NO necesitas** volver a ejecutar `npm install` después de reiniciar
- **NO necesitas** volver a ejecutar las migraciones de Prisma
- **Solo necesitas** iniciar Docker, backend y frontend en ese orden
- Los datos de prueba ya están en la base de datos (seed ejecutado)

---

## 🎓 ¿Qué hace cada componente?

- **Docker + PostgreSQL:** Almacena todos los datos (candidatos, posiciones, entrevistas)
- **Backend (puerto 3010):** API REST que maneja la lógica de negocio
- **Frontend (puerto 3000):** Interfaz web React donde interactúas con la aplicación
