# Cómo publicar tu perfil de GitHub — LordBaseX

## Archivos de este paquete

- `README.md`: portada principal en inglés, con enlaces a los otros idiomas.
- `README.es.md`: versión completa en español.
- `README.pt.md`: versión completa en portugués brasileño.
- `assets/lordbasex.png`: la imagen que compartiste, sin modificaciones.
- `REPOSITORIES.md`, `REPOSITORIES.es.md`, `REPOSITORIES.pt.md`: índice inicial verificado que se completará automáticamente.
- `scripts/build_catalog.py`: consulta el API público de GitHub y construye los catálogos completos.
- `.github/workflows/update-repositories.yml`: actualiza automáticamente el catálogo con GitHub Actions.

## Opción 1: desde GitHub (sin usar la terminal)

1. Iniciá sesión en GitHub con tu cuenta `lordbasex`.
2. Abrí https://github.com/new y creá un repositorio **público** llamado **`lordbasex`** (exactamente igual al nombre de usuario).
3. Activá **Add a README file** y creá el repositorio.
4. Entrá al repositorio. En `README.md`, hacé clic en el lápiz y reemplazá el contenido por el del `README.md` de este paquete. Guardá con **Commit changes**.
5. Usá **Add file → Upload files** desde la raíz para subir `README.es.md` y `README.pt.md`. Subí también los archivos `REPOSITORIES*`, la carpeta `scripts/` y `.github/workflows/` conservando sus rutas. Para la imagen, creá primero la carpeta `assets`: elegí **Add file → Create new file**, nombrá el archivo `assets/.gitkeep`, escribí una breve línea y guardalo. Entrá a la carpeta `assets`, seleccioná **Add file → Upload files** y subí `lordbasex.png`. La ruta final debe ser `assets/lordbasex.png`. Luego podés borrar `.gitkeep`.
6. Visitá https://github.com/lordbasex para ver la portada.

Si ya existe el repositorio `lordbasex/lordbasex`, solo actualizá los archivos. No hace falta crear uno nuevo.

## Opción 2: terminal (recomendado)

Desde la carpeta `lordbasex-github-profile` extraída del ZIP:

```bash
git init
git branch -M main
git add README.md README.es.md README.pt.md REPOSITORIES*.md assets/lordbasex.png scripts/build_catalog.py .github/workflows/update-repositories.yml
git commit -m "Add multilingual LordBaseX GitHub profile"
git remote add origin https://github.com/lordbasex/lordbasex.git
git push -u origin main
```

**Importante:** Antes de `git push`, creá el repositorio público vacío `lordbasex` en GitHub **sin inicializar un README**. Si lo creaste con README, usá `git clone` del repositorio existente y copiá encima los archivos, para evitar historias diferentes.

## Qué sucede con los logros

- GitHub muestra automáticamente las insignias oficiales de **Achievements** que haya conseguido tu cuenta. El README no permite agregarlas de forma legítima ni reemplazarlas.
- Los badges de seguidores y estrellas de LordOS en el README son dinámicos y se actualizan de acuerdo con GitHub (utilizan `shields.io`).
- Los badges de tecnologías representan tu stack, no certificaciones oficiales.

## Personalización posterior

- Editá `README.md`, `README.es.md` y `README.pt.md` cuando quieras incorporar proyectos nuevos.
- Podés fijar hasta seis repositorios destacados en la sección de proyectos fijados de tu perfil.
- La vista pública del README solo puede renderizar imágenes en rutas accesibles. Conservá `assets/lordbasex.png` en el repositorio público.

## Sincronizar todos tus repositorios (nuevo)

El enlace de tu perfil no permite verificar un inventario completo desde este entorno. Por ese motivo los archivos `REPOSITORIES*.md` incluidos inicialmente contienen solo proyectos públicos verificados: **NO son la lista completa**.

1. Subí todos los archivos del ZIP, **incluidas** las carpetas `.github/workflows/` y `scripts/`.
2. Entrá a `https://github.com/lordbasex/lordbasex/actions`.
3. Elegí **Refresh public repository catalog** y hacé clic en **Run workflow** (rama `main`). Si está deshabilitado, habilitá GitHub Actions para el repositorio.
4. Al finalizar exitosamente, GitHub Actions guardará en el mismo repositorio tres catálogos completos en inglés, español y portugués. La portada tendrá enlaces a esos archivos.

La sincronización se repetirá diariamente (GitHub puede demorar las tareas programadas). No requiere publicar tokens manualmente: el workflow usa el token temporal `GITHUB_TOKEN` de GitHub Actions. Para poder guardar los cambios se necesita permiso **Contents: write**, configurado en el workflow, y que la configuración de tu cuenta permita a Actions escribir en el repositorio.

El script consulta **solo repositorios públicos**, con paginación de hasta 10.000 repositorios. Los agrupa en proyectos propios, forks y archivados. No inventa proyectos y no crea ni modifica ninguno de tus repositorios de código.
