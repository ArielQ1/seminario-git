# Repositorio de Introducción a Git

Este repositorio contiene información detallada sobre el uso de Git, un sistema de control de versiones distribuido ampliamente utilizado en el desarrollo de software. A continuación, encontrarás una explicación detallada de los temas básicos de Git que te ayudarán a comprender y manejar este poderoso sistema.

---

## 📖 Contenido

1. [Introducción a Git](#introducción-a-git)
2. [Historia de Git](#historia-de-git)
3. [Instalación de Git](#instalación-de-git)
4. [Configuración de Git](#configuración-de-git)
5. [`git init`](#git-init)
6. [Ramas en Git](#ramas-en-git)
7. [`git add` && `git commit`](#git-add--git-commit)
8. [`git log` && `git status`](#git-log--git-status)
9. [`git checkout` && `git reset`](#git-checkout--git-reset)
10. [`.gitignore`](#gitignore)
11. [`git diff`](#git-diff)
12. [Desplazamiento por una rama](#desplazamiento-por-una-rama)
13. [`git reset --hard` && `git reflog`](#git-reset---hard--git-reflog)
14. [`git branch` && `git switch`](#git-branch--git-switch)
15. [`git merge`](#git-merge)
16. [Resolución de conflictos](#resolución-de-conflictos)
17. [`git branch -d <nombre de la rama>`](#git-branch--d-nombre-de-la-rama)
18. [Introducción a GitHub](#introducción-a-github)
19. [¿Qué es un repositorio?](#qué-es-un-repositorio)
20. [`git remote`](#git-remote)
21. [Subida de un proyecto](#subida-de-un-proyecto)
22. [`git pull` && `git fetch`](#git-pull--git-fetch)
23. [`git clone`](#git-clone)
24. [`git push`](#git-push)
25. [Fork](#fork)
26. [Pull Requests (PR)](#pull-requests-pr)
27. [Herramientas gráficas para Git y GitHub](#herramientas-gráficas-para-git-y-github)

---

## Introducción a Git

Git es un sistema de control de versiones distribuido diseñado para rastrear los cambios en el código fuente durante el desarrollo de software.  
Es ampliamente utilizado por desarrolladores para colaborar de manera eficiente y mantener un historial detallado de las modificaciones realizadas en un proyecto.

### ¿Por qué usar Git?
- **Control de versiones**: Permite guardar diferentes versiones del proyecto y restaurarlas cuando sea necesario.
- **Colaboración**: Facilita el trabajo en equipo al permitir que varios desarrolladores trabajen en el mismo proyecto sin conflictos.
- **Desempeño**: Su diseño distribuido lo hace rápido y eficiente.

---

## Historia de Git

Git fue creado en 2005 por **Linus Torvalds**, el creador de Linux. Fue desarrollado como una herramienta de control de versiones rápida, eficiente y confiable para reemplazar a un sistema propietario llamado BitKeeper.  
Desde entonces, Git se ha convertido en el estándar de la industria para el control de versiones gracias a sus características avanzadas y facilidad de uso.

**Hitos importantes:**
- **2005**: Creación inicial por Linus Torvalds.
- **2007**: Git se convierte en un sistema de código abierto con gran adopción.
- **2010**: GitHub, un servicio basado en Git, se populariza como una plataforma para proyectos colaborativos.

---

## Instalación de Git

### En Windows
1. Descarga el instalador desde [git-scm.com](https://git-scm.com/).
2. Ejecuta el instalador y sigue las instrucciones.
3. Verifica la instalación con:
   ```bash
   git --version
   ```

### En macOS
Usa Homebrew:
```bash
brew install git
```

### En Linux
Usa el gestor de paquetes de tu distribución:
```bash
sudo apt-get install git        # Para distribuciones basadas en Debian
sudo yum install git            # Para distribuciones basadas en Red Hat
```

---

## Configuración de Git

Después de instalar Git, configura tu nombre de usuario y correo electrónico. Estos datos se usarán para etiquetar tus cambios:

```bash
git config --global user.name "Tu Nombre"
git config --global user.email "tuemail@example.com"
```

Para verificar la configuración:
```bash
git config --list
```

---

## `git init`

El comando `git init` inicializa un nuevo repositorio de Git en un directorio. Este comando crea un subdirectorio `.git` que contiene todos los archivos necesarios para el control de versiones.

```bash
git init
```

### Ejemplo:
```bash
mkdir mi-proyecto
cd mi-proyecto
git init
```

---

## Ramas en Git

Una rama es una línea separada de desarrollo que permite trabajar en características o correcciones sin afectar la rama principal (`main` o `master`).

### Comandos útiles:
- Crear una nueva rama:
  ```bash
  git branch nombre_rama
  ```
- Cambiar a una rama:
  ```bash
  git checkout nombre_rama
  ```
- Listar ramas:
  ```bash
  git branch
  ```
- Fusionar ramas:
  ```bash
  git merge nombre_rama
  ```

---

## `git add` && `git commit`

### `git add`
Agrega archivos al área de preparación (staging area), preparándolos para ser confirmados en el historial.

```bash
git add archivo.txt        # Agregar un archivo específico
git add .                  # Agregar todos los archivos en el directorio actual
```

### `git commit`
Confirma los cambios agregados en el repositorio con un mensaje descriptivo.

```bash
git commit -m "Descripción de los cambios"
```

---

## `git log` && `git status`

### `git log`
Muestra el historial de confirmaciones del repositorio.

```bash
git log
```

### Opciones útiles:
- Ver historial en una línea:
  ```bash
  git log --oneline
  ```

### `git status`
Muestra el estado actual del repositorio, incluyendo archivos modificados, no rastreados o en el área de preparación.

```bash
git status
```

---

## `git checkout` && `git reset`

### `git checkout`
Permite cambiar entre ramas o restaurar archivos en una confirmación anterior.

- Cambiar a una rama:
  ```bash
  git checkout nombre_rama
  ```

- Restaurar un archivo a su última confirmación:
  ```bash
  git checkout archivo.txt
  ```

### `git reset`
Deshace cambios en el historial de confirmaciones o elimina archivos del área de preparación.

- Restablecer el área de preparación:
  ```bash
  git reset archivo.txt
  ```

- Deshacer la última confirmación (sin perder los cambios):
  ```bash
  git reset --soft HEAD~1
  ```

---


## `.gitignore`

El archivo `.gitignore` se utiliza para excluir ciertos archivos o directorios del seguimiento de Git. Es útil para ignorar archivos temporales, configuraciones locales o archivos sensibles.

### Ejemplo de un archivo `.gitignore`:
```
# Ignorar archivos temporales
*.log
*.tmp

# Ignorar carpetas específicas
node_modules/
dist/

# Ignorar configuraciones locales
.env
```

Para aplicar los cambios en el archivo `.gitignore`, asegúrate de que los archivos a ignorar no estén ya siendo rastreados.

---

## `git diff`

El comando `git diff` muestra las diferencias entre archivos modificados pero no confirmados o entre ramas.

### Ejemplos:
- Comparar los cambios en el área de trabajo:
  ```bash
  git diff
  ```

- Comparar cambios en el área de preparación:
  ```bash
  git diff --staged
  ```

---

## Desplazamiento por una rama

Para navegar a una rama específica, utiliza el comando `git switch`:

```bash
git switch nombre_rama
```

Si necesitas cambiar a una rama existente pero utilizando un método más antiguo, puedes usar `git checkout`:

```bash
git checkout nombre_rama
```

---

## `git reset --hard` && `git reflog`

### `git reset --hard`
Este comando restaura el historial del repositorio y el área de trabajo a un estado anterior. **Nota:** Los cambios no confirmados se perderán.

```bash
git reset --hard HEAD~1
```

### `git reflog`
Permite rastrear todos los cambios realizados en el repositorio, incluso después de un `git reset --hard`.

```bash
git reflog
```

Puedes usar `git reflog` para encontrar un commit perdido y restaurarlo:

```bash
git reset --hard <id_commit>
```

---

## `git branch` && `git switch`

### `git branch`
Lista todas las ramas en el repositorio:

```bash
git branch
```

Crear una nueva rama:
```bash
git branch nueva_rama
```

### `git switch`
Cambia a una rama específica:
```bash
git switch nombre_rama
```

Crear y cambiar a una nueva rama:
```bash
git switch -c nueva_rama
```

---

## `git merge`

El comando `git merge` combina los cambios de una rama en la rama actual. Esto es útil para integrar características o correcciones de errores.

```bash
git merge nombre_rama
```

### Tipos de fusiones:
- **Fast-forward**: Ocurre cuando no hay cambios divergentes entre las ramas.
- **Merge commit**: Crea una nueva confirmación para combinar ramas con historial divergente.

---

## Resolución de conflictos

Los conflictos ocurren cuando dos ramas modifican la misma parte de un archivo. Git marca los conflictos en los archivos afectados con secciones como:

```
<<<<<<< HEAD
código desde la rama actual
=======
código desde la rama fusionada
>>>>>>> nombre_rama
```

### Pasos para resolver conflictos:
1. Edita los archivos marcados por Git para solucionar el conflicto.
2. Agrega los archivos resueltos al área de preparación:
   ```bash
   git add archivo_resuelto
   ```
3. Completa la fusión con un commit:
   ```bash
   git commit
   ```

---

## `git branch -d <nombre de la rama>`

El comando `git branch -d` elimina una rama local que ya no necesitas.

```bash
git branch -d nombre_rama
```

Si la rama no ha sido fusionada, usa `-D` para forzar la eliminación:
```bash
git branch -D nombre_rama
```

---

## Introducción a GitHub

GitHub es una plataforma basada en la web que utiliza Git para el control de versiones. Proporciona un espacio para colaborar, almacenar código y gestionar proyectos.

### Características principales:
- Repositorios remotos para almacenar proyectos.
- Herramientas para colaboración como Issues, Pull Requests y Wikis.
- Integraciones con CI/CD, despliegue y herramientas de monitoreo.

---

## ¿Qué es un repositorio?

Un repositorio es un espacio donde se almacena el historial de un proyecto, incluyendo sus archivos, ramas y commits. Puede ser:
- **Local**: Un repositorio en tu máquina.
- **Remoto**: Un repositorio alojado en un servidor como GitHub.

### Crear un repositorio en GitHub:
1. Ve a tu cuenta en GitHub.
2. Haz clic en **New Repository**.
3. Proporciona un nombre y opcionalmente agrega una descripción.
4. Configura la visibilidad como pública o privada y haz clic en **Create Repository**.

---

## `git remote`

El comando `git remote` gestiona las conexiones entre tu repositorio local y los repositorios remotos.

### Ejemplos:
- Ver repositorios remotos:
  ```bash
  git remote -v
  ```

- Añadir un repositorio remoto:
  ```bash
  git remote add origin https://github.com/usuario/repo.git
  ```

- Eliminar un repositorio remoto:
  ```bash
  git remote remove origin
  ```

---

## Subida de un proyecto

Para subir un proyecto local a un repositorio remoto en GitHub:
1. Asegúrate de haber inicializado el repositorio local:
   ```bash
   git init
   ```
2. Añade un repositorio remoto:
   ```bash
   git remote add origin https://github.com/usuario/repo.git
   ```
3. Sube los archivos:
   ```bash
   git add .
   git commit -m "Primer commit"
   git push -u origin main
   ```

---

## `git pull` && `git fetch`

### `git pull`
Obtiene los últimos cambios del repositorio remoto y los combina con tu rama local.

```bash
git pull origin main
```

### `git fetch`
Obtiene los últimos cambios del repositorio remoto sin fusionarlos en tu rama local.

```bash
git fetch origin
```

---

## `git clone`

El comando `git clone` crea una copia de un repositorio remoto en tu máquina local.

```bash
git clone https://github.com/usuario/repo.git
```

Opcionalmente, puedes especificar una carpeta para clonar el repositorio:
```bash
git clone https://github.com/usuario/repo.git carpeta_local
```

---

## `git push`

El comando `git push` sube los cambios confirmados al repositorio remoto.

```bash
git push origin main
```

Para subir todas las ramas:
```bash
git push --all origin
```

---

## Fork

Un fork es una copia de un repositorio alojado en GitHub que se encuentra bajo tu cuenta. Te permite realizar cambios sin afectar el proyecto original.

### Cómo crear un fork:
1. Haz clic en el botón **Fork** en la página del repositorio.
2. Trabaja en tu copia personal.
3. Envía cambios al repositorio original mediante un **Pull Request**.

---

## Pull Requests (PR)

Un Pull Request es una solicitud para fusionar cambios de un repositorio (o rama) en otro. Es esencial para colaborar en proyectos de código abierto.

### Pasos para crear un PR:
1. Haz cambios en tu fork o rama.
2. Sube los cambios a tu repositorio remoto.
3. En GitHub, haz clic en **New Pull Request**.
4. Describe los cambios y solicita la revisión.

---

## Herramientas gráficas para Git y GitHub

Si prefieres una interfaz gráfica en lugar de usar la línea de comandos, estas herramientas pueden ser útiles:

- **GitHub Desktop**: Una aplicación oficial para gestionar repositorios GitHub.
- **Sourcetree**: Herramienta gratuita para manejar repositorios Git.
- **GitKraken**: Interfaz gráfica avanzada para Git con integración con GitHub.
- **VS Code**: Editor con extensiones integradas para Git y GitHub.

---



## 📜 Créditos

Este repositorio fue desarrollado como parte de los contenidos académicos bajo la guía del **Ph.D. Marisol Tellez Ramírez** y el auxiliar **Ariel Quizaya Callisaya**.

Siéntete libre de contribuir o reportar problemas en este repositorio. ¡Gracias por tu interés en aprender Git!