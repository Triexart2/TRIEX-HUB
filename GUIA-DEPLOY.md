# 🚀 GUÍA DE DEPLOY — TRIEX HUB
## Publicar la app en internet (una sola vez, ~15 minutos)

---

## ✅ LO QUE VAS A LOGRAR
Al finalizar esta guía tendrás:
- Una URL fija: **https://triex-interno.web.app**
- Login con email y contraseña para cada vendedor
- Todos los datos guardados en la nube automáticamente
- Funciona desde cualquier dispositivo, 24/7

---

## PASO 1 — Instalar Node.js
1. Ir a: **https://nodejs.org**
2. Descargar la versión **LTS** (botón verde)
3. Instalar con todas las opciones por defecto
4. Verificar: abrir **Símbolo del sistema** (CMD) y escribir:
   ```
   node --version
   ```
   Debe mostrar algo como: `v20.x.x`

---

## PASO 2 — Instalar Firebase CLI
En el Símbolo del sistema (CMD), ejecutar:
```
npm install -g firebase-tools
```
Esperar que termine (puede tardar 1-2 minutos).

---

## PASO 3 — Iniciar sesión en Firebase
```
firebase login
```
Se va a abrir el navegador → iniciar sesión con la cuenta Google del proyecto (la misma del Firebase Console).

---

## PASO 4 — Preparar los archivos
1. Descomprimir la carpeta **triex-deploy** en tu escritorio
2. La estructura debe verse así:
   ```
   triex-deploy/
   ├── firebase.json
   ├── .firebaserc
   ├── firestore.rules
   └── public/
       └── index.html
   ```

---

## PASO 5 — Publicar las reglas de seguridad
En CMD, navegar a la carpeta:
```
cd C:\Users\Equipo\Desktop\triex-deploy
```
Luego ejecutar:
```
firebase deploy --only firestore:rules
```

---

## PASO 6 — Publicar la app
```
firebase deploy --only hosting
```
Al finalizar vas a ver:
```
✔ Deploy complete!
Hosting URL: https://triex-interno.web.app
```

---

## PASO 7 — Crear cuentas para el equipo
1. Ir a: **https://console.firebase.google.com**
2. Proyecto: **triex-interno**
3. Menú izquierdo: **Authentication** → **Users**
4. Clic en **"Add user"**
5. Para cada vendedor:
   - Email: el email del equipo
   - Contraseña: una temporal (el sistema permite cambiarla)

**Usuarios a crear:**
| Nombre | Email |
|--------|-------|
| Milagros Agüero (ADMIN) | info@triexviajes.com.ar |
| Celeste Garro | celeste@triexviajes.com.ar |
| Florencia Benavides | florbenavides@triexviajes.com.ar |
| Eliana Rivero | eliana@triexviajes.com.ar |
| Victoria Amaya | victoria@triexviajes.com.ar |
| Nicolas Cozzani | nicolascozzani@triexviajes.com.ar |
| Franco Agüero | reservas@triexviajes.com.ar |
| Hugo Fisigaro | hugo@triexviajes.com.ar |
| Laura Paredes | wineadventure@triexviajes.com.ar |
| Eugenio Saad | eugenio@triexviajes.com.ar |
| Lucia Tirador | luciatirador@triexviajes.com.ar |

---

## PASO 8 — Asignar roles (admin)
El sistema detecta automáticamente que `info@triexviajes.com.ar` es admin.
Los demás usuarios son vendedores por defecto.

Si necesitás cambiar el rol de alguien:
1. Firebase Console → **Firestore Database**
2. Colección `usuarios`
3. Buscar por email → campo `rol` → cambiar a `admin` o `vendedor`

---

## ✅ LISTO — URL DE LA APP
```
https://triex-interno.web.app
```
Compartir esta URL con todo el equipo.

---

## 🔄 ACTUALIZACIONES FUTURAS
Cada vez que quieras actualizar la app:
1. Reemplazar `index.html` en la carpeta `public/`
2. Ejecutar: `firebase deploy --only hosting`
¡Listo! Se actualiza en segundos.

---

## 🆘 PROBLEMAS FRECUENTES

**"firebase: command not found"**
→ Reiniciar el CMD y volver a intentar.

**"Error: permission denied"**
→ Ejecutar CMD como Administrador.

**"Project not found"**
→ Verificar que estás logueado con la cuenta correcta de Google.

**La app abre pero no deja loguear**
→ Verificar en Firebase Console → Authentication → Email/Password esté habilitado.

---

## 📊 BACKUP AUTOMÁTICO
Firebase hace backup automático de Firestore.
Para exportar manualmente:
1. Firebase Console → **Firestore**
2. Clic en los tres puntos (**⋮**)
3. **Export data** → guardar en Google Cloud Storage

---
