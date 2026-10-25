# Melanoma HUSJR — app

Carpeta lista para publicar como PWA (app instalable) y, a partir de ella, generar el .apk.

## 1. Publicar (necesario: HTTPS)
Sube la carpeta completa a cualquier hosting estático: GitHub Pages, Netlify (arrastrar carpeta en app.netlify.com/drop), Cloudflare Pages, o junto a DerMate.app.
No funciona desde `file://` (el service worker y la instalación exigen HTTPS).

## 2. Instalar como app (sin .apk)
Android/Chrome: abrir la URL → menú ⋮ → "Instalar aplicación" / "Añadir a pantalla de inicio".
iPhone/Safari: compartir → "Añadir a pantalla de inicio".
Resultado: icono propio, pantalla completa sin barra del navegador, funciona sin conexión.

## 3. Generar el .apk (opción A, 5 minutos, sin programar)
1. Ir a https://www.pwabuilder.com y pegar la URL publicada.
2. "Package for stores" → Android → descargar. Entrega un .apk (para instalar directamente) y un .aab (para Google Play).
3. Para instalar el .apk en el móvil: pasar el archivo y permitir "instalar apps de origen desconocido".

## 3b. Generar el .apk (opción B, Android Studio)
    npm init -y && npm i @capacitor/core @capacitor/cli @capacitor/android
    npx cap init "Melanoma HUSJR" cat.husjr.melanoma --web-dir .
    npx cap add android && npx cap open android
En Android Studio: Build → Build Bundle(s)/APK(s) → Build APK(s).

## Notas
- Versión de lógica: 1.0 (25/10/2026). Si cambia la guía, actualizar `index.html` y la constante CACHE de `sw.js` (v2, v3…) para que los móviles recarguen.
- La app no guarda datos de pacientes; solo los valores del formulario en el propio móvil.
