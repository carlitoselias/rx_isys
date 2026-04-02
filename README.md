# rx_isys

Sitio web generado originalmente con Manus y refactorizado para despliegue **estático** en **Cloudflare Pages**.

## Cambios de estructura para Cloudflare Pages

- El build de Vite ahora genera archivos en `dist/` (directorio esperado por Pages).
- Se agregó `wrangler.toml` con la configuración de Pages.
- Se agregó `client/public/_redirects` para soportar SPA routing (`/* /index.html 200`).
- Se agregó `client/public/_headers` con headers de seguridad sin afectar la UI/UX.
- Se eliminaron los pasos de empaquetado del servidor Node para mantener un flujo 100% estático.

## Scripts

```bash
pnpm dev
pnpm build
pnpm start
pnpm preview
pnpm deploy:pages
```

- `pnpm build`: compila el sitio estático en `dist/`.
- `pnpm start`: vista previa local con Vite (`vite preview`).
- `pnpm preview`: emula Cloudflare Pages localmente con Wrangler.
- `pnpm deploy:pages`: despliega `dist/` a Cloudflare Pages.

## Deploy en Cloudflare Pages

1. Instala dependencias:
   ```bash
   pnpm install
   ```
2. Build del sitio:
   ```bash
   pnpm build
   ```
3. Login en Cloudflare (una vez):
   ```bash
   pnpm wrangler login
   ```
4. Deploy:
   ```bash
   pnpm deploy:pages
   ```

## Configuración en el panel de Cloudflare Pages (opcional)

Si conectas el repo directamente desde Cloudflare Pages:

- **Build command**: `pnpm build`
- **Build output directory**: `dist`
- **Node version**: 20+

