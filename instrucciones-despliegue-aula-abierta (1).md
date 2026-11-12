# Instrucciones para Desplegar Tu Blog "Aula Abierta"

## Antes de empezar — Prerrequisitos

1. **GitHub:** Crea tu cuenta en github.com y crea un **repositorio público vacío** con el nombre que quieras para tu blog (ej: `mi-blog-docente`, `aula-ciencias-5to`)
2. **Render:** Crea tu cuenta en render.com
3. **Claude.ai:** Activa los conectores de **GitHub** y **Render** (ver tutorial del profesor)

## Qué hacer

1. Abre un **chat nuevo** en Claude.ai (con los conectores activos)
2. **Adjunta el archivo `aula-abierta-blog.zip`** al chat
3. **Copia y pega** todo el texto dentro del recuadro de abajo
4. **Completa** los dos campos marcados con [ ] antes de enviar
5. Envía el mensaje y sigue las indicaciones de Claude

---

## Prompt — Copiar todo lo que está dentro del recuadro

```
Soy estudiante de la clase de Tecnología Educativa (MTEMA). Adjunto un archivo .zip que contiene los 16 archivos de un blog educativo estático listo para desplegar. Necesito tu ayuda para ponerlo en internet.

MI INFORMACIÓN:
- Mi usuario de GitHub es: [ESCRIBE TU USUARIO DE GITHUB]
- Mi repositorio (ya creado, público y vacío) se llama: [ESCRIBE EL NOMBRE DE TU REPO]

PASO 1 — SUBIR ARCHIVOS A GITHUB:
Sube TODOS los archivos del .zip a mi repositorio. Son 16 archivos que van en la raíz del repo (sin subcarpetas):
- 11 archivos HTML (index, publicaciones, lectura, recursos, panel, gestion, editor, biblioteca, moderacion, perfil, admin-login)
- 2 archivos JS (db.js, profile-loader.js)
- 1 archivo _redirects
- 1 archivo package.json
- 1 archivo README.md

PASO 2 — CREAR STATIC SITE EN RENDER:
Crea un Static Site (NO Web Service) en Render conectado a mi repositorio de GitHub con esta configuración:
- Branch: main
- Publish Directory: . (punto — los HTML están en la raíz)
- Build Command: vacío o "echo No build needed"
- NO necesita variables de entorno
- Es un sitio estático gratuito, no necesita backend ni base de datos

PASO 3 — VERIFICAR:
Confirma que el sitio cargó correctamente en la URL que Render asigne.

CONTEXTO TÉCNICO DEL BLOG (para que entiendas la arquitectura):
- Es un sitio 100% estático: HTML + Tailwind CSS (CDN) + JavaScript vanilla
- Toda la persistencia es client-side con IndexedDB (módulo db.js)
- NO requiere servidor backend, NO requiere base de datos externa, NO requiere build step
- db.js crea automáticamente datos de ejemplo educativos la primera vez que se visita
- profile-loader.js permite que el docente personalice su perfil desde perfil.html y se refleje en todas las páginas usando atributos data-tp="campo"
- El archivo _redirects es crítico para que Render enrute correctamente todas las páginas
- El login en admin-login.html es demo (no tiene autenticación real, solo redirige al panel)

DESPUÉS del despliegue exitoso, ayúdame a personalizar mi blog. Pregúntame:
1. ¿Cómo me llamo y cuál es mi título académico?
2. ¿En qué escuela o distrito trabajo?
3. ¿Qué materia(s) enseño y en qué grado(s)?
4. ¿Qué nombre quiero para mi blog? (en vez de "Aula Abierta")
5. ¿Qué color prefiero como tema principal? (morado actual, azul, verde, rojo, ámbar, u otro)

Con mis respuestas, haz los cambios en el código del repositorio: renombrar el blog, cambiar la paleta de colores (clases Tailwind), y actualizar los datos semilla del perfil docente en db.js.
```

---

> **Nota para el profesor:** El .zip contiene SOLO los 16 archivos del blog (sin documentación extra). El prompt incluye todo el contexto técnico que Claude necesita. El estudiante solo debe completar su usuario y nombre de repo de GitHub antes de enviar.
