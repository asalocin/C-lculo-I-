# Cálculo I

Repositorio dedicado a la creación de un texto guía para un primer curso de cálculo diferencial en una variable.

**Autor:** Ignacio Tobar  
**Co-autor:** Nicolás Aguilar  
**Estado:** 🚧 Proyecto en proceso  
**Tecnologías:** LaTeX / Visual Studio Code / GitHub

---

## Estructura del repositorio

```
main.tex                  ← Punto de entrada del libro (no editar directamente)
book/order.tex            ← Define el orden de los capítulos
shared/preamble.tex       ← Preámbulo LaTeX compartido
frontmatter/portada.tex   ← Portada del libro
assets/
  images/                 ← Imágenes
  figures/                ← Figuras generadas
chapters/
  capitulo-XX/
    nicolas/contenido.tex ← Borrador de Nicolás
    ignacio/contenido.tex ← Borrador de Ignacio
    final.tex             ← Versión final (incluida en el PDF)
.github/workflows/
  build-book.yml          ← Compilación automática del PDF en GitHub Actions
```

---

## Flujo de trabajo

### Reglas básicas

1. **Nadie escribe directamente en `main.tex`.**
2. Cada colaborador escribe únicamente en su propia carpeta:
   - Nicolás escribe en `chapters/capitulo-XX/nicolas/contenido.tex`
   - Ignacio escribe en `chapters/capitulo-XX/ignacio/contenido.tex`
3. Una vez acordado el contenido, se fusiona en `chapters/capitulo-XX/final.tex`.
4. El PDF final se genera **solo desde `main.tex`**, el cual incluye únicamente los archivos `final.tex` de cada capítulo, en el orden definido en `book/order.tex`.

### Compilar localmente

```bash
pdflatex main.tex
pdflatex main.tex   # segunda pasada para índice y referencias
```

O usando `latexmk`:

```bash
latexmk -pdf main.tex
```

### PDF automático (CI)

Cada vez que se hace un `push` o un `pull request` a `main`, GitHub Actions compila el libro automáticamente. El PDF queda disponible como artefacto en la pestaña **Actions** del repositorio.
