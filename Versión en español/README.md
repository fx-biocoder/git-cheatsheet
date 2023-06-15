# Git: una breve guía introductoria para principiantes

## 1. ¿Qué es Git?

Git es un sistema de control de versiones distribuido utilizado para rastrear los cambios realizados en un conjunto de archivos por parte de individuos o grupos. Es una herramienta de código abierto (FOSS, por sus siglas en inglés) que se utiliza ampliamente en empresas debido a su eficiencia y rapidez.

Git permite la creación de ramas de desarrollo paralelas, lo que te permite a ti y a los miembros de tu equipo trabajar simultáneamente en diferentes características del proyecto y luego fusionarlas más tarde. Al realizar un seguimiento de los cambios realizados en el proyecto, puedes revertir fácilmente a una versión anterior en caso de que surjan problemas.

- [Ver: ¿Qué es el control de versiones? (en inglés)](https://git-scm.com/video/what-is-version-control)

## 2. Instalar Git en el ordenador

### Windows:

[Instalador de Git para Windows](https://gitforwindows.org/)

### Debian/Ubuntu:

```bash
$ sudo apt-get update
$ sudo apt-get install git-all
```

### Fedora:

```bash
$ sudo dnf install git-all
```

### Mac:

[Instalador de git-osx](https://sourceforge.net/projects/git-osx-installer/files/git-2.23.0-intel-universal-mavericks.dmg/download?use_mirror=autoselect)

Usando Homebrew:

```bash
$ bew install git
```

Luego de instalar git, necesitás configurarlo estableciendo tu usuario global y e-mail:

```bash
$ git config --global user.name "Your username"
$ git config --global user.email "youremail@domain.com"
```

Si deseás configurar un nombre de usuario y e-mail diferente para un repositorio específico, podés correr los mismos comandos anteriores en la carpeta del repositorio, pero sin añadir la opción `--global`.

## 3. Conceptos básicos

![Operaciones de Git](https://github.com/fx-biocoder/git-cheatsheet/assets/90737264/8f491fb0-01e8-46d9-ada9-5cd80937b0f6)

En Git, tenés tres estados principales: el directorio de trabajo, el área de preparación (staging) y el directorio Git (o repositorio local). También podés tener un repositorio remoto conectado a tu directorio Git.

El directorio de trabajo es, en esencia, una copia de la versión de tu proyecto. Git guarda una copia comprimida de todas tus versiones dentro de una carpeta oculta, y se descomprimen cuando necesitás acceder a ellas.

El área de preparación guarda información sobre los cambios que están por ser commiteados en el repositorio.

El directorio Git (o repositorio local) guarda todos los metadatos importantes para tu proyecto: commits, repositorios remotos, logs, etcétera.

- [Leer: ¿Qué es Git? (en inglés)](https://git-scm.com/book/en/v2/Getting-Started-What-is-Git%3F)


## 4. Establecer un repositorio local

### Crear un repositorio nuevo

Cuando comenzás un proyecto nuevo, podés crear una carpeta nueva para almacenar tu repositorio Git, el cual es creado con `git init`

```bash
$ mkdir projectfolder
$ cd projectfolder
$ git init
```

### Ver el estado actual del repositorio

Este comando te muestra qué archivos han sido modificados recientemente en la carpeta del proyecto.

```bash
$ git status
```

### Agregar archivos al área de preparación

Luego de crear y/o modificar los archivos del directorio de trabajo, podés agregarlos simultáneamente al área de preparación usando este comando:

```bash
$ git add .
```

Si querés agregar un solo archivo:

```bash
$ git add nombredearchivo
```

### Enviar archivos del área de preparación al repositorio local

Para enviar todos los cambios al repositorio local, podés usar este comando:

```bash
$ git commit -m "Comentario
```

El comentario debe indicar qué cambios se han realizado recientemente al repositorio. Es una buena práctica el escribir comentarios detallados que reflejen de forma precisa los cambios realizados: Si tipeás `git commit` sin agregar nada más, se abrirá un editor de texto que permitirá agregar un mensaje. El envío de los cambios se realizará tan pronto se cierre la ventana del editor de texto.

## 5. Verificar cambios en el repositorio local

### Ver lista de cambios

```bash
$ git log
```

### Ver qué se modificó recientemente antes de enviarlo al repositorio local

Luego de modificar un archivo, se verá clasificado como "modified" al correr el comando `git status`. Para ver los cambios que se han realizado desde el último envío al repositorio local:

```bash
$ git diff
```

## 6. Ramas

### Ver rama actual

```bash
$ git branch
```

Este comando imprime en la terminal la rama en la que uno se encuentra trabajando actualmente.

- [Leer: Documentación de git-branch](https://git-scm.com/docs/git-branch)

### Crear una rama nueva

Comenzá por verificar que no tenés commits pendientes:

```bash
$ git status
```

Creá una rama nueva:

```bash
$ git checkout -b nuevarama
```

Es una buena práctica el crear ramas nuevas cuando querés agregar una nueva funcionalidad al proyecto. Podés nombrarlas como `funcionalidad/nueva-funcionalidad` donde "nueva-funcionalidad" corresponde al nombre de la funcionalidad que querés agregar.


### Moverse hacia otra rama

Para moverse desde una rama hacia otra:

```bash
$ git checkout nombredelarama
```

Donde "nombredelarama" representa la rama hacia la cual querés ir.

*NOTA: también podés usar git-checkout" para restaurar archivos modificados a su última versión.*

- [Leer: Documentación de git-checkout](https://git-scm.com/docs/git-checkout)

### Combinar ramas

Digamos que tenés que rama que está varios commits adelantada de otra. Para combinar esa rama con tu rama actual:

```bash
$ git merge nombredelarama
```

Donde "nombredelarama" corresponde a la rama que querés combinar con la actual.

- [Leer: Documentación de git-merge](https://git-scm.com/docs/git-merge)

### Resolver conflictos de combinación de ramas

- [Leer: Resolviendo conflictos de combinación de ramas usando la línea de comandos](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/addressing-merge-conflicts/resolving-a-merge-conflict-using-the-command-line)


## 7. Repositorios remotos

Podés comunicarte con repositorios remotos usando Git.

### Pushear un repositorio existente a una localización remota

Si querés "pushear" hacia un repositorio remoto, como un de Github:

```bash
$ git remote add origin git@github.com:nombredeusuario/repositorio.git
$ git branch -M main
$ git push -u origin main
```

Donde "nombredeusuario" corresponde al dueño y "repositorio" es el nombre del repositorio remoto.

*TIP: podés reemplazar la palabra "origin" por cualquier otra palabra que desees, solamente es un identificador.*

### Clonar repositorio remoto en local

```bash
$ git clone url-repositorio
```

Donde `url-repositorio` es la URL del repositorio remoto que querés clonar dentro de tu directorio actual.

### Ver repositorios remotos configurados

```bash
$ git remote -v
```

### Obtener cambios realizados en el repositorio remoto y enviarlos al local

Para descargar los cambios realizados en una sola localización remota:

```bash
$ git fetch origin
```

Para descargar cambios de todas las localizaciones remotas:

```bash
$ git fetch --all
```

- [Leer: Documentación de git-fetch](https://git-scm.com/docs/git-fetch)

### Obtener cambios del remoto e integrarlos al directorio de trabajo

*NOTA IMPORTANTE: No es recomendable usar este comando para descargar e integrar todos los cambios de una sola vez, a menos que sepas que esto no generará conflictos. Es mejor usar git-fetch primero.*

```bash
$ git pull origin
```

Para integrar los cambios de todas las localizaciones remotas:

```bash
$ git pull --all
```

- [Leer: Documentación de git-pull](https://git-scm.com/docs/git-pull)

## 8. Mejores prácticas de Git

Algunos recursos externos gratuitos (en inglés) para aprender y aplicar las mejores prácticas de Git:

- [GitLab: What are Git version control best practices?](https://about.gitlab.com/topics/version-control/version-control-best-practices/)
- [Atlassian: Source code management](https://www.atlassian.com/git/tutorials/source-code-management)
- [Grant Weatherston: Git Best Practices - How to Write Meaningful Commits, Effective Pull Requests, and Code Reviews](https://www.freecodecamp.org/news/git-best-practices-commits-and-code-reviews/)


## Notas finales

Este artículo fue creado por Facundo Martínez © 2023. Está licenciado bajo CC BY-NC-SA 4.0.

Me encanta crear contenido gratuito para todos. Si mis artículos y repositorios te han sido útiles, considera apoyarme en Github Sponsors, Ko-Fi o PayPal. Sería de gran ayuda y lo apreciaría mucho.

[![Github-sponsors](https://img.shields.io/badge/sponsor-30363D?style=for-the-badge&logo=GitHub-Sponsors&logoColor=#EA4AAA)](https://github.com/sponsors/fx-biocoder) [![Ko-Fi](https://img.shields.io/badge/Ko--fi-F16061?style=for-the-badge&logo=ko-fi&logoColor=white)](https://ko-fi.com/biocoder) [![PayPal](https://img.shields.io/badge/PayPal-00457C?style=for-the-badge&logo=paypal&logoColor=white)](https://paypal.me/facumartinez680)
