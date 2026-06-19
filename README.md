# Vue 3 + Vite

This template should help get you started developing with Vue 3 in Vite. The template uses Vue 3 `<script setup>` SFCs, check out the [script setup docs](https://v3.vuejs.org/api/sfc-script-setup.html#sfc-script-setup) to learn more.

Learn more about IDE Support for Vue in the [Vue Docs Scaling up Guide](https://vuejs.org/guide/scaling-up/tooling.html#ide-support).

## Docker

Build the production image:

```sh
docker build -t web-bdiel .
```

Run the container:

```sh
docker run --rm -p 8080:80 web-bdiel
```

Or use Docker Compose:

```sh
docker compose up --build
```

The site will be available at `http://localhost:8080`.
# web-bdiel

## Deploy en cPanel

Este proyecto es una app Vue/Vite estática. En cPanel no se sube el código fuente completo: se genera la carpeta `dist/` y se publica su contenido.

### Opción recomendada: build local y subir archivos

1. Instala Node.js en tu equipo si no lo tienes.
2. En la carpeta del proyecto ejecuta:

```sh
npm install
npm run build
```

3. Entra a cPanel > File Manager.
4. Abre `public_html` si el sitio va en el dominio principal.
5. Sube todo el contenido de la carpeta `dist/`, no la carpeta `dist` completa.
6. Verifica que `public_html` tenga archivos como `index.html`, `.htaccess` y la carpeta `assets/`.

### Si va en un subdirectorio

Si el sitio va en una ruta como `tudominio.com/portfolio/`, configura `base` en `vite.config.js` antes de compilar:

```js
export default defineConfig({
  base: '/portfolio/',
  plugins: [
    vue(),
    tailwindcss(),
  ],
})
```

Después vuelve a ejecutar `npm run build` y sube el contenido de `dist/` al subdirectorio correspondiente dentro de `public_html`.

### Subir por Git en cPanel

También puedes clonar el repositorio con Git Version Control de cPanel. Este repo incluye `.cpanel.yml`, que ejecuta el build y copia `dist/` a `public_html` cuando usas Deploy HEAD Commit.

El archivo usa Node.js 20 desde esta ruta típica de cPanel:

```sh
/opt/cpanel/ea-nodejs20/bin/npm
```

Si tu hosting tiene otra versión de Node.js, cambia esa ruta en `.cpanel.yml`. Por ejemplo, algunos servidores usan `ea-nodejs18`.

Después de clonar el repositorio en cPanel:

1. Entra a Git Version Control.
2. Abre el repositorio.
3. Haz clic en Deploy HEAD Commit.
4. cPanel ejecutará `npm ci`, `npm run build` y copiará el contenido de `dist/` a `public_html`.
