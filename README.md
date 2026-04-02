# rx_isys

Sitio web generado originalmente con Manus y adaptado para despliegue estático en Cloudflare Pages.

## Cambios clave para que despliegue correctamente en Pages

- `wrangler.toml` usa `pages_build_output_dir = "."` para que Cloudflare publique directamente desde la raíz del repo (evita el error `Output directory "dist" not found` cuando Pages omite el build step).
- Se agregaron `_redirects` y `_headers` en la raíz para enrutamiento SPA y headers básicos en hosting estático.
- Se agregó `index.html` en la raíz para garantizar un documento de entrada desplegable.
- Los scripts de Wrangler se ajustaron para publicar la raíz (`wrangler pages dev .` y `wrangler pages deploy .`).

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
- Build output directory: `.`
- Root directory: *(vacío / repo root)*
