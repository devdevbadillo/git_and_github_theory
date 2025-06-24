# Git & GitHub

## Tabla de contenido

- [Fundamentos de Git](#fundamentos-de-git)
  - [Control de versiones](#control-de-versiones)
    - [¿Qué es y por qué su importancia?](#que-es-y-su-importancia) 
  - [Conceptos básicos de Git](#conceptos-basicos-de-git)
    - [Repositorio (Repository)](#repository)
    - [Área de trabajo (Working Directory)](#working-directory)
    - [Área de preparación (Staging Area)](#staing-area)
    - [Historial de confirmaciones (Commit History)](#commit-history)
  - [Comandos esenciales de Git](#comandos-escenciales-de-git)
    - [git init: Inicializar un repositorio](#comando-git-init)
    - [git add: Añadir archivos al área de preparación](#comando-git-add)
    - [git commit: Confirmar cambios con un mensaje significativo](#comando-git-commit)
      - [Mensajes de confirmación con buenas prácticas](#mensajes-de-confirmacion)
    - [git status: Ver el estado de tu repositorio](#comando-git-status)
    - [git diff: Comparar cambios](#comando-git-diff)
    - [git log: Ver el historial de confirmaciones](#comando-git-log)
    - [git rm y git mv: Eliminar y mover archivos](#comando-git-rm-and-mv)
  - [Archivos ignorados (.gitignore)](#gitignore)
    - [Especificar archivos](#espeficar-archivos-ignorados)
- [Ramas (Branches) en Git](#git-branches)
  - [¿Qué son las ramas y por qué utilizarlas?](#que-son-las-ramas-y-su-uso)
  - [Comandos de ramas](#comandos-de-ramas)
    - [git branch: Crear, listar y borrar ramas](#comando-git-branch)
    - [git checkout: Cambiar entre ramas](#comando-git-checkout)
    - [git merge: Combinar cambios de una rama a otra](#comando-git-merge)
    - [git rebase: Reorganizar el historial de confirmaciones](#comando-git-rebase)
  - [Estrategias de ramificación](#estrategias-de-ramificacion)
    - [Git Flow](#git-flow)
    - [GitHub Flow](#github-flow)
    - [Trunk-based development](#trunk-based-development)
  - [Resolución de conflictos de fusión (Merge Conflicts)](#merge-conflicts)
- [Conceptos Avanzados de Git](#conceptos-avanzados-de-git)
  - [Revertir cambios](#revertir-cambios)
    - [git revert: Crear una nueva confirmación](#comando-git-revert)
    - [git reset: Mover el puntero del HEAD a una confirmación anterior](#comando-git-reset)
  - [Stashing](#stashing)
    - [git stash: Guardar temporalmente cambios no confirmados](#comando-git-stash)
  - [Cherry-picking](#cherry-picking)
    - [git cherry-pick: Aplicar una confirmación específica de una rama a otra](#comando-git-cherry-pick)
  - [Reflog](#reflog)
    - [git reflog: El historial del repositorio](#comando-git-reflog)
- [Colaboración con Git y GitHub](#colaboracion-con-github)
  - [Repositorios remotos](#repositorios-remotos)
    - [Repositorios en GitHub](#repositorios-en-github)
    - [Configuración de conexión](#configuracion-de-conexion)
  - [Comandos para repositorios remotos](#comandos-para-repositorios-remotos)
    - [git remote: Gestionar repositorios remotos](#comando-git-remote)
    - [git clone: Clonar un repositorio existente de GitHub](#comando-git-clone)
    - [git push: Subir cambios locales a un repositorio remoto](#comando-git-push)
    - [git pull: Descargar cambios de un repositorio remoto y fusionarlos](#comando-git-pull)
    - [git fetch: Descargar cambios de un remoto sin fusionarlos](#comando-git-fetch)
- [GitHub como plataforma](#github-como-plataforma)
  - [Issues](#issues)
    - [Seguimiento de tareas, errores y mejoras](#seguimiento-de-tareas-errores)
  - [Pull Requests (PRs)](#pull-request)
    - [Proceso de revisión de código](#proceso-de-revision-de-codigo)
    - [Integración continua/Despliegue continuo (CI/CD) con PRs](#ci/cd-con-pull-request) 
  - [Actions](#actions)
    - [Automatización de flujos de trabajo](#automatizacion-de-flujos-de-trabajo)
  - [Funcionalidades para la gestión de proyectos](#gestion-de-proyectos)
    - [Wikis](#wikis)
    - [Projects](#projects)
    - [Discussions](#discussions)
  - [Flujos de trabajo colaborativos](#flujos-de-trabajo-colaborativo)
    - [Centralized Workflow](#centralized-workflow)
    - [Fork: Contribuir a proyectos de código abierto](#forks)


 
<a id="fundamentos-de-git"></a>
## Fundamentos de Git

<a id="control-de-versiones"></a>
### Control de versiones

<a id="que-es-y-su-importancia"></a>
#### ¿Qué es y por qué su importancia?

<a id="conceptos-basicos-de-git"></a>
### Conceptos básicos de Git

<a id="repository"></a>
#### Repositorio (Repository)

<a id="working-directory"></a>
#### Área de trabajo (Working Directory)

<a id="staing-area"></a>
#### Área de preparación (Staging Area)

<a id="commit-history"></a>
#### Historial de confirmaciones (Commit History)

<a id="comandos-escenciales-de-git"></a>
### Comandos esenciales de Git

<a id="comando-git-init"></a>
#### git init: Inicializar un repositorio

<a id="comando-git-add"></a>
#### git add: Añadir archivos al área de preparación

<a id="comando-git-commit"></a>
#### git commit: Confirmar cambios con un mensaje significativo

<a id="mensajes-de-confirmacion"></a>
##### Mensajes de confirmación con buenas prácticas

<a id="comando-git-status"></a>
#### git status: Ver el estado de tu repositorio

<a id="comando-git-diff"></a>
#### git diff: Comparar cambios

<a id="comando-git-log"></a>
#### git log: Ver el historial de confirmaciones

<a id="comando-git-rm-and-mv"></a>
#### git rm y git mv: Eliminar y mover archivos

<a id="gitignore"></a>
### Archivos ignorados (.gitignore)

<a id="espeficar-archivos-ignorados"></a>
#### Especificar archivos

<a id="git-branches"></a>
## Ramas (Branches) en Git

<a id="que-son-las-ramas-y-su-uso"></a>
### ¿Qué son las ramas y por qué utilizarlas?

<a id="comandos-de-ramas"></a>
### Comandos de ramas

<a id="comando-git-branch"></a>
#### git branch: Crear, listar y borrar ramas

<a id="comando-git-checkout"></a>
#### git checkout: Cambiar entre ramas

<a id="comando-git-merge"></a>
#### git merge: Combinar cambios de una rama a otra

<a id="comando-git-rebase"></a>
#### git rebase: Reorganizar el historial de confirmaciones

<a id="estrategias-de-ramificacion"></a>
### Estrategias de ramificación

<a id="git-flow"></a>
#### Git Flow

<a id="github-flow"></a>
#### GitHub Flow

<a id="trunk-based-development"></a>
#### Trunk-based development

<a id="merge-conflicts"></a>
### Resolución de conflictos de fusión (Merge Conflicts)

<a id="conceptos-avanzados-de-git"></a>
## Conceptos Avanzados de Git

<a id="revertir-cambios"></a>
### Revertir cambios

<a id="comando-git-revert"></a>
#### git revert: Crear una nueva confirmación

<a id="comando-git-reset"></a>
#### git reset: Mover el puntero del HEAD a una confirmación anterior

<a id="stashing"></a>
### Stashing

<a id="comando-git-stash"></a>
#### git stash: Guardar temporalmente cambios no confirmados

<a id="cherry-picking"></a>
### Cherry-picking

<a id="comando-git-cherry-pick"></a>
#### git cherry-pick: Aplicar una confirmación específica de una rama a otra

<a id="reflog"></a>
### Reflog

<a id="comando-git-reflog"></a>
#### git reflog: El historial del repositorio

<a id="colaboracion-con-github"></a>
## Colaboración con Git y GitHub

<a id="repositorios-remotos"></a>
### Repositorios remotos

<a id="repositorios-en-github"></a>
#### Repositorios en GitHub

<a id="configuracion-de-conexion"></a>
#### Configuración de conexión

<a id="comandos-para-repositorios-remotos"></a>
### Comandos para repositorios remotos

<a id="comando-git-remote"></a>
#### git remote: Gestionar repositorios remotos

<a id="comando-git-clone"></a>
#### git clone: Clonar un repositorio existente de GitHub

<a id="comando-git-push"></a>
#### git push: Subir cambios locales a un repositorio remoto

<a id="comando-git-pull"></a>
#### git pull: Descargar cambios de un repositorio remoto y fusionarlos

<a id="comando-git-fetch"></a>
#### git fetch: Descargar cambios de un remoto sin fusionarlos

<a id="github-como-plataforma"></a>
## GitHub como plataforma

<a id="issues"></a>
### Issues

<a id="seguimiento-de-tareas-errores"></a>
#### Seguimiento de tareas, errores y mejoras

<a id="pull-request"></a>
### Pull Requests (PRs)

<a id="proceso-de-revision-de-codigo"></a>
#### Proceso de revisión de código

<a id="ci/cd-con-pull-request"></a>
#### Integración continua/Despliegue continuo (CI/CD) con PRs

<a id="ci/actions"></a>
### Actions

<a id="automatizacion-de-flujos-de-trabajo"></a>
#### Automatización de flujos de trabajo

<a id="gestion-de-proyectos"></a>
### Funcionalidades para la gestión de proyectos

<a id="wikis"></a>
#### Wikis

<a id="projects"></a>
#### Projects

<a id="discussions"></a>
#### Discussions

<a id="flujos-de-trabajo-colaborativo"></a>
### Flujos de trabajo colaborativos

<a id="centralized-workflow"></a>
#### Centralized Workflow

<a id="forks"></a>
#### Fork: Contribuir a proyectos de código abierto
