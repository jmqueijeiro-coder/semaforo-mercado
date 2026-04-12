# Semáforo de Mercado — Instrucciones de despliegue

## Archivos del proyecto

```
semaforo-pwa/
├── index.html      ← App completa
├── manifest.json   ← Configuración PWA
├── sw.js           ← Service worker (funciona sin conexión)
├── vercel.json     ← Configuración de despliegue
└── README.md       ← Este archivo
```

> **Nota sobre los iconos:** Vercel funciona sin los iconos. Para añadirlos,
> crea dos imágenes PNG (192×192 y 512×512) con el nombre `icon-192.png` e
> `icon-512.png` y ponlas en la misma carpeta. Puedes usar cualquier imagen
> o generarlas en https://favicon.io/

---

## Paso 1 — Crear cuenta en GitHub (si no tienes)

1. Ve a https://github.com y crea una cuenta gratuita.

---

## Paso 2 — Subir los archivos a GitHub

1. En GitHub, pulsa **"New repository"** (botón verde arriba a la derecha).
2. Nombre: `semaforo-mercado` (o el que quieras).
3. Déjalo **público**. Pulsa **"Create repository"**.
4. En la página del repositorio, pulsa **"uploading an existing file"**.
5. Arrastra los 4 archivos (`index.html`, `manifest.json`, `sw.js`, `vercel.json`).
6. Pulsa **"Commit changes"**.

---

## Paso 3 — Desplegar en Vercel

1. Ve a https://vercel.com y crea una cuenta gratuita (puedes usar tu cuenta de GitHub).
2. Pulsa **"Add New Project"**.
3. Selecciona el repositorio `semaforo-mercado`.
4. Vercel detecta automáticamente la configuración. Pulsa **"Deploy"**.
5. En 1-2 minutos tendrás una URL del tipo `semaforo-mercado.vercel.app`.

---

## Paso 4 — Instalar en el móvil como app

### iPhone (Safari)
1. Abre la URL en **Safari** (no Chrome).
2. Pulsa el botón de compartir (cuadrado con flecha arriba).
3. Desplázate y pulsa **"Añadir a pantalla de inicio"**.
4. Ponle el nombre que quieras → **Añadir**.

### Android (Chrome)
1. Abre la URL en **Chrome**.
2. Pulsa los tres puntos arriba a la derecha.
3. Pulsa **"Añadir a pantalla de inicio"** o **"Instalar app"**.

---

## Funcionamiento

- Al abrir la app, consulta automáticamente los 3 indicadores via API.
- Pulsa **↺ Actualizar** para refrescar los datos cuando quieras.
- El AAII se publica semanalmente (jueves). VIX y PCR son diarios.
- La app funciona como shell offline: si no hay conexión, muestra la interfaz
  pero no puede obtener datos nuevos (requiere internet para consultar).

---

## Umbrales

| Indicador | 🟢 Alcista | 🟡 Neutral | 🔴 Bajista |
|-----------|-----------|-----------|-----------|
| VIX | < 16 | 16 – 20 | > 20 |
| Put/Call | > 1.20 | 0.60 – 1.20 | < 0.60 |
| AAII B-B | < −20% | −20% a +30% | > +30% |
