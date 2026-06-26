# Prácticas de Sistemas Basados en Microprocesador

> **Este repositorio es un ejemplo.** Aquí puedes ver cómo se organiza un repositorio de prácticas y cómo se usa Git para desarrollarlas, tanto en GitHub como en GitLab. **No vas a trabajar directamente sobre este repositorio**: antes de empezar, crea tu propia copia siguiendo la sección **"Cómo obtener tu propio repositorio"** más abajo.

Plantilla de organización para las prácticas de la asignatura, desarrolladas en **C** sobre microcontrolador, usando **Keil µVision** y **VS Code (CMSIS-Toolbox)**. Cada alumno trabaja en su propia copia de este repositorio (creada como plantilla en GitHub e importada a GitLab), con la misma estructura.

## Estructura del repositorio

```
B1/   -> Bloque 1
B2/   -> Bloque 2
B3/   -> Bloque 3
```

Cada bloque contiene una o varias prácticas (`P0`, `P1`, `P2`...). Cada práctica es una carpeta independiente con su propio enunciado y, dentro, el código fuente y los proyectos de Keil/VS Code (ver la sección **"Organización de cada práctica"** más abajo).

## Organización de cada práctica

Cada práctica sigue siempre la misma organización interna, pensada para que el mismo código en C se pueda compilar y probar tanto desde **Keil Vision** como desde **VS Code** (con el CMSIS-Toolbox de Arm), sin duplicar el código fuente:

```
P0/
 README.md
 src/      <- código fuente en C, común a ambos entornos (.c / .h)
 keil/     <- proyecto de Keil Vision (.uvprojx, configuración RTE...)
 vc/       <- proyecto de VS Code / CMSIS-Toolbox (.csolution.yml, .cproject.yml...)
```

- **`src/`**: aquí se escribe el código de la práctica, paso a paso. Es la única carpeta donde se desarrolla la lógica; tanto el proyecto de Keil como el de VS Code compilan los mismos archivos, así que no hay que mantener dos copias del código.
- **`keil/`**: contiene el proyecto para abrir y compilar con Keil Vision (MDK-ARM). El archivo principal del proyecto tiene la extensión `.uvprojx`.
- **`vc/`**: contiene el proyecto para abrir y compilar en VS Code, usando la extensión de Arm CMSIS y el sistema de proyectos `csolution`/`cproject` (archivos `.csolution.yml` y `.cproject.yml`). 

> Esta organización está inspirada en la usada en el repositorio [SBM-rtos](https://github.com/mruizglz/SBM-rtos), donde cada ejemplo separa el código común (`src/`) de la configuración específica de cada entorno (`keil/`, `vc/`).

**Todas las prácticas de este repositorio (de cualquier bloque) deben seguir esta misma organización de carpetas.**

## Cómo obtener tu propio repositorio

Antes de tocar nada, necesitas tu propia copia de este repositorio, independiente del repositorio original. Los pasos varían un poco según la plataforma que uses.

### Si usas GitHub

1. Entra en la página de este repositorio en GitHub.
2. Pulsa el botón verde **"Use this template"** (arriba a la derecha) **"Create a new repository"**.
3. Elige un nombre para tu repositorio (por ejemplo, `practicas-nombre-apellido`) y selecciona tu cuenta personal como propietaria.
4. Pulsa **"Create repository"**.

### Si usas GitLab

1. Inicia sesión en GitLab y, en la barra lateral, selecciona **"Create new"** (icono **+**) **"New project/repository"**.
2. Selecciona la pestaña **"Import project"** **"Repository by URL"**.
3. En el campo de la URL del repositorio Git, pega la URL de clonación de este repositorio (la encontrarás en el botón verde **"Code"** de este repo en GitHub, copiando el enlace HTTPS).
4. Elige un nombre para tu proyecto, marca la visibilidad como **Private** y pulsa **"Create project"**.

GitLab importará todo el contenido de este repositorio (carpetas, README, etc.) a tu nuevo proyecto, que será completamente independiente del original.

En ambos casos, a partir de aquí trabajarás siempre sobre tu propia copia, nunca sobre este repositorio de ejemplo.

## Guía de Git para empezar desde cero

Si nunca has usado Git, sigue esta guía paso a paso. Los comandos de Git son los mismos en GitHub y en GitLab (Git es la misma herramienta en los dos casos); solo cambia cómo se obtiene el repositorio y, en algún punto, la web donde generas tus credenciales. No necesitas memorizar nada: vuelve a esta sección cada vez que lo necesites.

### 1. Instalar Git

Descarga e instala Git desde [git-scm.com/downloads](https://git-scm.com/downloads) (Windows, macOS o Linux). Para comprobar que se ha instalado correctamente, abre una terminal y escribe:

```bash
git --version
```

Si te devuelve un número de versión, está listo.

### 2. Configurar tu identidad (solo una vez por ordenador)

Antes de tu primer commit, dile a Git quién eres. Esto se guarda en tu ordenador y aparecerá firmando cada commit que hagas:

```bash
git config --global user.name "Tu Nombre"
git config --global user.email "tu_email@ejemplo.com"
```

Usa el mismo email que tengas asociado a tu cuenta de GitHub o GitLab (la que vayas a usar).

### 3. Descargar tu repositorio (clonar)

Una vez tengas **tu propio repositorio** (ver la sección "Cómo obtener tu propio repositorio" más arriba — no este repositorio de ejemplo), descárgalo a tu ordenador. Abre una terminal en la carpeta donde quieras guardarlo y ejecuta la línea que corresponda a tu plataforma:

```bash
git clone https://github.com/TU-USUARIO/practicas-tu-nombre.git    # si usas GitHub
git clone https://gitlab.com/TU-USUARIO/practicas-tu-nombre.git    # si usas GitLab
cd practicas-tu-nombre
```

Sustituye la URL por la de tu propio repositorio: la encontrarás pulsando el botón verde **"Code"** (en GitHub) o **"Clone"** (en GitLab) en la página de tu repositorio. Esto solo se hace una vez. A partir de aquí trabajarás siempre dentro de esa carpeta.

### 4. El ciclo de trabajo básico

Cada vez que avances en una práctica y quieras guardar tu progreso, repite estos cuatro pasos:

**a) Mira qué ha cambiado**
```bash
git status
```
Te dice qué archivos has modificado, creado o borrado desde el último commit.

**b) Añade los archivos que quieres guardar**
```bash
git add B1/P0/src/ejercicio.c
```
O, para añadir todos los cambios a la vez (cuidado con esto):
```bash
git add .
```

**c) Crea el commit**

Un commit es como una "foto" del estado de tu código en ese momento, acompañada de un mensaje que explica qué hiciste (usa lenguaje imperativo):
```bash
git commit -m "B1-P0: implementa la lectura de datos"
```
El mensaje debe ser breve y describir el cambio real, no algo genérico como "cambios" o "avance".

**d) Sube los cambios a tu repositorio remoto**
```bash
git push
```
Esto funciona igual tanto si tu repositorio remoto está谩 en GitHub como en GitLab.

Repite este ciclo (`status` `add` `commit` `push`) cada vez que completes un paso. No esperes a tener la práctica completa para hacer tu primer commit.

### 5. Ver el historial de commits

```bash
git log              # historial detallado
git log --oneline    # una línea por commit, más fácil de leer
```

### 6. Etiquetas (tags): marcar un paso importante

Cuando el enunciado de una práctica lo pida, marca un paso concreto con una etiqueta, para poder identificarlo fácilmente más adelante:

```bash
git tag B1-P0-paso1
git push origin --tags
```

Las etiquetas se crean siempre **después** de hacer el commit correspondiente a ese paso. Funciona igual en GitHub y en GitLab.

### 7. Descargar cambios (pull)

Si trabajas desde varios ordenadores, o se actualiza algo en tu repositorio desde fuera, antes de empezar a trabajar es buena práctica traer los 煤últimos cambios:

```bash
git pull
```

### 8. Problemas comunes y cómo solucionarlos

- **Me olvidé de añadir un archivo al último commit (y aún no he hecho push):**
  ```bash
  git add archivo_olvidado.c
  git commit --amend --no-edit
  ```

- **Quiero deshacer cambios en un archivo que aún no he añadido con `git add`:**
  ```bash
  git restore archivo.c
  ```

- **Quiero deshacer el último commit pero conservar los cambios (todavía no he hecho push):**
  ```bash
  git reset --soft HEAD~1
  ```

- **GitHub o GitLab no me aceptan usuario y contraseña al hacer `git push`:** ambas plataformas han eliminado la autenticación con contraseña tradicional para Git mediante HTTPS. Necesitas un *Personal Access Token* (o configurar una clave SSH):
  - GitHub: [docs.github.com/es/authentication](https://docs.github.com/es/authentication)
  - GitLab: [docs.gitlab.com/user/profile/personal_access_tokens](https://docs.gitlab.com/user/profile/personal_access_tokens/)

- **No sé en qué carpeta estoy / qué repositorio es este:**
  ```bash
  pwd                  # muestra la carpeta actual
  git remote -v        # muestra a qué repositorio remoto está谩 conectado
  ```

### 9. Resumen de comandos esenciales

| Comando | Para qué sirve |
|---|---|
| `git status` | Ver qué ha cambiado |
| `git add <archivo>` / `git add .` | Preparar cambios para el commit |
| `git commit -m "mensaje"` | Guardar una "foto" de tus cambios |
| `git push` | Subir tus commits a tu repositorio remoto |
| `git pull` | Descargar cambios de tu repositorio remoto |
| `git log --oneline` | Ver el historial de commits |
| `git tag <nombre>` | Marcar un commit concreto |
| `git push origin --tags` | Subir las etiquetas a tu repositorio remoto |

## Cómo trabajar esta asignatura: el paso a paso

En esta asignatura es muy importante conocer como evoluciona el código:

- Haz **un commit por cada paso significativo** que completes en una práctica, no un único commit final con todo el código terminado.
- Usa mensajes de commit claros, indicando bloque y práctica (ej. `B1-P1: añade función de xxxxx).
- Cuando se indique en el enunciado, marca ese paso con un tag de Git (ver la sección "Etiquetas" de la guía anterior).

Si tienes dudas sobre cualquiera de estos comandos, repasa la guía de Git de más arriba.

## Entrega

Cuando finalices una práctica se te va a pedir que subas a Moodle el código final implementado. En github o gitlab puedes descargar una copia en zip del código. Súbela a Moodle.


