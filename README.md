# rx_isys

Sitio web generado originalmente con Manus y adaptado para despliegue estático en Cloudflare Pages.

## Cambios clave para que despliegue correctamente en Pages

- `wrangler.toml` usa `pages_build_output_dir = "dist"`.
- Se versiona `dist/` (incluye `index.html`, `_redirects`, `_headers`) para que Cloudflare pueda publicar aunque omita el build step.
- Los scripts de Wrangler usan `dist` (`wrangler pages dev dist` y `wrangler pages deploy dist`).

## Scripts

```bash
pnpm dev
pnpm build
pnpm start
pnpm preview
pnpm deploy:pages
```

## Configuración recomendada en Cloudflare Pages (si usas panel)

- Build command: *(vacío / none)*
- Build output directory: `dist`
- Root directory: *(vacío / repo root)*

## Si hay conflictos en PR

Para `wrangler.toml`, `.gitignore`, `package.json` y `dist/*`, **no aceptes automáticamente "incoming" ni "current"**.
Resuelve manualmente y conserva:

- `pages_build_output_dir = "dist"`
- scripts `preview/deploy:pages` apuntando a `dist`
- excepciones de `.gitignore` para permitir versionar `dist/*`
