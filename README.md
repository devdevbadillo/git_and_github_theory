# Git & GitHub

## Tabla de contenido

- [Fundamentos de Git](#fundamentos-de-git)
  - [Control de versiones](#control-de-versiones)
    - [¿Por qué su importancia?](#su-importancia) 
  - [Conceptos básicos de Git](#conceptos-basicos-de-git)
    - [Repositorio (Repository)](#repository)
    - [Área de trabajo (Working Directory)](#working-directory)
    - [Área de preparación (Staging Area)](#staging-area)
    - [Historial de confirmaciones (Commit History)](#commit-history)
      - [Mensajes de confirmación con buenas prácticas](#mensajes-de-confirmacion) 
  - [Comandos esenciales de Git](#comandos-escenciales-de-git)
    - [git init: Inicializar un repositorio](#comando-git-init)
    - [git add: Añadir archivos al área de preparación](#comando-git-add)
    - [git commit: Confirmar cambios con un mensaje significativo](#comando-git-commit)
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
    - [Resolución de conflictos de fusión (Merge Conflicts)](#merge-conflicts)
    - [git rebase: Reorganizar el historial de confirmaciones](#comando-git-rebase)
  - [Estrategias de ramificación](#estrategias-de-ramificacion)
    - [Git Flow](#git-flow)
    - [GitHub Flow](#github-flow)
    - [Trunk-based development](#trunk-based-development)
- [Conceptos Avanzados de Git](#conceptos-avanzados-de-git)
  - [Revertir cambios](#revertir-cambios)
    - [git revert: Crear una nueva confirmación y deshacer una confirmación anterior](#comando-git-revert)
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
    - [Fork: Contribuir a proyectos de código abierto](#forks)


 
<a id="fundamentos-de-git"></a>
## Fundamentos de Git

<a id="control-de-versiones"></a>
### Control de versiones
El control de versiones **es un sistema que registra los cambios realizados en un archivo o un conjunto de archivos a lo largo del tiempo**, de modo que se puedan recuperar versiones específicas más adelante. No solo guarda el estado dentro de los archivos en un momento dado, sino que **también registra quién hizo qué cambio, cuándo lo hizo y por qué**.

> [!NOTE]
>
> - Git es un sistema de control de versiones distribuido (DVCS). Esto significa que cada desarrollador tiene una copia completa del historial del proyecto en su máquina local

<a id="su-importancia"></a>
#### ¿Por qué su importancia?

- `Historial completo`: Te permite ver la evolución de cualquier proyecto. Permite rastrear cada modificación, quién la introdujo y el propósito detrás de ella.

- `Colaboración eficiente`: Múltiples personas pueden trabajar en el mismo proyecto simultáneamente sin pisarse los cambios. El sistema ayuda a fusionar las contribuciones de cada uno.

- `Recuperación de errores`: Si se introduce un error que rompe el código o se desea revertir a una versión anterior estable, el control de versiones te permite hacerlo con facilidad.

- `Experimentación segura`: Se pueden crear "ramas" (**versiones alternativas de tu código**) para probar nuevas ideas o características sin afectar la versión principal o estable del proyecto.

<a id="conceptos-basicos-de-git"></a>
### Conceptos básicos de Git
Ahora que entendemos la necesidad del control de versiones, veamos cómo Git maneja los datos

<a id="repository"></a>
#### Repositorio (Repository)
Un repositorio (o "repo") es una base de datos donde Git **almacena todo lo que necesita saber para gestionar y controlar las versiones del proyecto**.

Cuando se inicializa un repositorio dentro de un proyecto Git crea una sub carpeta oculta llamada `.git` dentro de esa carpeta contiene:
1. Todo el historial de confirmaciones
2. Las ramas
3. Las configuraciones
4. Los objetos que representan los archivos del proyecto

> [!NOTE]
> 
> - Si se elimina la carpeta .git, entonces, se perderá todo el historial de versiones y el proyecto deja de ser un repositorio Git.

<a id="working-directory"></a>
#### Área de trabajo (Working Directory)
El área de trabajo (también conocido como "directorio de trabajo" o "árbol de trabajo") es simplemente la carpeta del proyecto dentro del sistema de archivos del SO. En otras palabras, es la carpeta que contiene los todos archivos y directorios que se pueden ver, editar y manipular directamente.

Cuando se clona un repositorio o se cambia de rama, Git *extrae* una instantánea del historial y la coloca en el área de trabajo para que se inicie con los cambios.

> [!NOTE]
>
> - **Es la versión del proyecto** con la que estás interactuando activamente.

<a id="staging-area"></a>
#### Área de preparación (Staging Area)
**No es una carpeta física, sino un archivo** (generalmente el índice en el directorio .git) que **almacena una lista de los cambios que se han realizado en el área de trabajo**. Estos cambios se han marcado para la próxima confirmación.

Pensemos en el área de preparación como una *caja de cambios* antes de empaquetarlos para el envío. Cuando se usa `git add <archivo>`, **no se está guardando el archivo en el historial definitivo**; en cambio, se está preparando esa versión específica del archivo para que sea incluida en la próxima confirmación. Esto permite:

1. `Confirmar solo los cambios relevantes`: Se pudo haber hecho muchos cambios dentro del área de trabajo, pero solo seleccionar un subconjunto de esos cambios para incluir en una confirmación específica.

2. `Construir confirmaciones atómicas`: Permite agrupar lógicamente cambios relacionados en una sola confirmación, haciendo que el historial sea más limpio y fácil de entender

<a id="commit-history"></a>
#### Historial de confirmaciones (Commit History)
El historial de confirmaciones **representa la evolución de un proyecto**. Te permite navegar hacia atrás y hacia adelante en el tiempo, ver cómo evolucionó un proyecto, quién hizo qué y por qué. Es la base para revertir cambios, fusionar ramas y colaborar de manera efectiva.

Cada vez que se ejecuta el comando `git commit`, se está creando una nueva confirmación (commit).

Una confirmación es como una "fotografía" o "punto de guardado" de un proyecto en un momento específico. Cada confirmación contiene:

1. `Un hash SHA-1 único`: Un identificador criptográfico que garantiza la integridad de los datos

2. `Puntero al commit padre (o padres)`: La mayoría de los commits apuntan a un commit anterior, creando una cadena lineal de historial. Los commits de fusión (merge commits) pueden apuntar a múltiples padres

3. `Metadatos`: Información sobre la confirmación, como el autor, la fecha y la hora en que se hizo

4. `Mensaje de la confirmación`: Una descripción significativa de los cambios que se realizaron en esa confirmación

<a id="mensajes-de-confirmacion"></a>
##### Mensajes de confirmación con buenas prácticas
Los buenos mensajes de confirmación son fundamentales por varias razones:

1. `Claridad del historial`: Facilitan la comprensión del historial del proyecto para cualquiera que lo lea

2. `Depuración`: Ayudan a localizar rápidamente cuándo y por qué se introdujo un error

3. `Revisión de Código`: Hacen que las revisiones de código sean más eficientes, ya que el revisor puede entender el contexto del cambio

4. `Colaboración`: Mejoran la comunicación dentro de un equipo, asegurando que todos estén al tanto de los cambios y su propósito

Buenas prácticas para mensajes de confirmación:

1. Línea de asunto concisa (y obligatoria):

- La primera línea del mensaje (el "asunto") debe tener 50 caracteres o menos.

- Debe ser una descripción imperativa de lo que hace el commit. Piensa en "Si se aplica este commit, él hará [tu asunto]".

Ejemplos: 
- Fix: Corregir error de inicio de sesión
- Feat: Añadir funcionalidad de carrito de compras
- Docs: Actualizar README con instrucciones de instalación.

2. Cuerpo del mensaje detallado (opcional pero recomendado):

- El cuerpo debe explicar el "por qué" del cambio. ¿Cuál fue el problema que se resolvió? ¿Qué nueva funcionalidad se añadió? ¿Por qué se tomó esa decisión específica?

Ejemplo:
```
Feat: Añadir validación de email en formulario de registro

Implementa validación del formato del email en el formulario de registro de usuario.
Esto asegura que solo se acepten direcciones de correo electrónico válidas, lo que mejora la seguridad del sistema.
```

<a id="comandos-escenciales-de-git"></a>
### Comandos esenciales de Git

<a id="comando-git-init"></a>
#### git init: Inicializar un repositorio
El comando `git init` es el punto de partida para cualquier proyecto que desees controlar con Git. **Su función principal es convertir un directorio existente en un repositorio Git** o crear un nuevo repositorio Git vacío.

- Uso
```
  cd mi_proyecto # Navegamos al directorio del proyecto
  git init      # Inicializamos el repositorio Git aquí
```

Después de ejecutarlo, el directorio actual **se convierte en un área de trabajo (working directory)**, y Git está listo para empezar a rastrear los cambios en los archivos dentro de él.

<a id="comando-git-add"></a>
#### git add: Añadir archivos al área de preparación
Su propósito es **mover los cambios del área de trabajo al área de preparación (staging area)**.

¿Cómo funciona?

- Cuando se modifica un archivo en el área de trabajo, Git lo considera un `cambio sin seguimiento` (untracked change). Para decirle a Git que se quiere incluir esos cambios en la próxima confirmación (commit), se deben *añadir* al área de preparación.

> Uso
1. Añadir un archivo específico:
```
   git add archivo_especifico.txt
```

2. Añadir múltiples archivos:
```
   git add archivo1.txt archivo2.txt
```

3. Añadir todos los archivos en el área de trabajo:
```
   git add .
```

> [!IMPORTAN]
> 
> - Usar `git add .` añade todos los archivos nuevos, modificados y eliminados (a menos que estén en .gitignore) al área de preparación. Siempre uno debe de asegurarse de que esto es lo que se quiere antes de usarlo.

<a id="comando-git-commit"></a>
#### git commit: Confirmar cambios con un mensaje significativo
Su función es guardar los cambios que se tienen en la `área de preparación` en el `historial de confirmaciones` del repositorio. 

> ¿Cómo funciona?
>
> - Git toma una instantánea (snapshot) de todos los archivos tal como están en la `área de preparación` en ese momento. Luego, guarda esa instantánea de forma permanente en la base de datos del repositorio y crea una nueva *confirmación* (commit).

- Uso
```
git commit -m "Feat: Añadir validación de formulario de contacto"
```

> [!NOTE]
> 
> - La opción -m te permite escribir el mensaje de confirmación directamente. Ideal para mensajes de una sola línea, pero para mensajes más complejos, es mejor usar la opción sin -m.

<a id="comando-git-status"></a>
#### git status: Ver el estado de tu repositorio
Su función principal es **mostrar el estado actual del área de trabajo y del área de preparación**.

- `git status` te informará sobre:

1. `La rama actual`: Te dice en qué rama estás trabajando.

2. `Archivos sin seguimiento (Untracked files)`: Archivos nuevos en el área de trabajo que Git aún no está controlando (no los ha visto antes).

3. `Cambios para ser confirmados (Changes to be committed)`: Archivos que se han añadido al área de preparación (`git add`) y que están listos para la próxima confirmación.

4. `Cambios no preparados para la confirmación (Changes not staged for commit)`: Archivos que Git está rastreando y que se han modificado en el área de trabajo, pero que **aún no se han añadido al área de preparación** (git add).

5. `Archivos sin modificar`: Archivos que Git está rastreando y que no han sido modificados desde la última confirmación

> Ejemplo de salida:
```
On branch main
Your branch is up to date with 'origin/main'.

Changes to be committed:
(use "git restore --staged <file>..." to unstage)
new file:   src/utils.js
modified:   src/app.js

Changes not staged for commit:
(use "git add <file>..." to update what will be committed)
(use "git restore <file>..." to discard changes in working directory)
modified:   index.html

Untracked files:
(use "git add <file>..." to include in what will be committed)
temp.txt
```

<a id="comando-git-diff"></a>
#### git diff: Comparar cambios
Sirve para **mostrar las diferencias entre diferentes versiones de los archivos dentro del proyecto**.

- `git diff` puede comparar:

1. `Cambios en el área de trabajo vs. el área de preparación`: Muestra los cambios que se han hecho en los archivos del proyecto, pero, que aún no se han añadido al área de preparación.

2. `Cambios en el área de preparación vs. la última confirmación`: Muestra los cambios que ya están en el área de preparación y que serán parte de la próxima confirmación.

3. `Cambios entre dos confirmaciones`: Te permite comparar el estado de los archivos entre cualquier par de commits en el historial.

4. `Cambios entre una rama y otra`: Muy útil para ver qué diferencias hay entre líneas de desarrollo.

> Uso

1. Ver cambios en el área de trabajo que NO están en el área de preparación:
```
git diff
```

2. Ver cambios que SÍ están en el área de preparación (listos para el commit):
```
git diff --staged
# O también
git diff --cached
```

3. Ver cambios entre dos commits específicos:
```
git diff <hash_commit_1> <hash_commit_2>
```

4. Ver cambios entre la rama actual y otra rama:
```
git diff <rama_actual> <otra_rama>
```

- La salida de git diff se muestra en formato "diff" unificado, donde las líneas precedidas por + son adiciones y las líneas precedidas por - son eliminaciones.

<a id="comando-git-log"></a>
#### git log: Ver el historial de confirmaciones
Su función principal es explorar el historial de confirmaciones del repositorio. Te **permite ver un registro de cada commit, su autor, fecha y el mensaje de confirmación**.

¿Cómo funciona?

- `git log` recorre la cadena de commits hacia atrás desde el HEAD actual (la última confirmación de la rama actual) y muestra cada commit en orden cronológico inverso (los más recientes primero).

> Uso

1. Ver el historial completo (por defecto)
   ```
   git log
   ```

2. Ver un historial conciso (una línea por commit):
   ```
   git log --oneline
   ```

3. Ver el historial con un gráfico de ramas y merges:

   ```
    git log --graph --oneline --decorate
   ```

Filtrar el historial:

1. Por autor: `git log --author="Tu Nombre"`

2. Por fecha: `git log --since="2 weeks ago" o git log --until="2023-01-01"`

3. Por mensaje de commit: `git log --grep="feat: añadir"`

4. Por archivo afectado: `git log -- <nombre_del_archivo>`

<a id="comando-git-rm-and-mv"></a>
#### git rm y git mv: Eliminar y mover archivos

> git rm: Eliminar archivos

Cuando se usa `git rm`, Git no solo borra el archivo de tu sistema de archivos, sino que también lo "desindexa", es decir, lo elimina del área de preparación. Esto le dice a Git que, en la próxima confirmación, ese archivo ya no debería estar presente en el repositorio.

> Uso

1. Eliminar un archivo y registrar la eliminación para el próximo commit:
   ```
    git rm archivo_a_eliminar.txt
   ```

2. Eliminar un archivo del área de preparación, pero mantenerlo en el área de trabajo
   ```
   git rm --cached archivo_que_no_quiero_rastrear.log
   ```

> git mv: Mover archivos

Git no rastrea directamente el "movimiento" de un archivo. **En cambio, detectaría que un archivo antiguo fue eliminado y uno nuevo fue añadido**. `git mv` maneja esto de una manera más elegante.

Cuando se utiliza `git mv`, Git realiza internamente tres operaciones:

1. Renombra o mueve el archivo en tu sistema de archivos

2. Desindexa el archivo original (como si se hubiera eliminado con `git rm`)

3. Añade el nuevo archivo (con su nueva ubicación/nombre) al área de preparación (como si se hubiera hecho `git add`).

De esta manera, Git entiende que el archivo fue "movido" o "renombrado" en lugar de simplemente eliminado y recreado, lo que mantiene el historial más limpio

> Uso
1. Renombrar un archivo:
```
   git mv archivo_original.txt archivo_nuevo.txt
```

2. Mover un archivo a otro directorio:
```
   git mv archivo_original.txt directorio_nuevo/archivo_nuevo.txt
```


<a id="gitignore"></a>
### Archivos ignorados (.gitignore)
Cuando se trabaja en un proyecto, es común que se generen archivos que no necesitas ni quieres rastrear con Git. Estos pueden incluir:

1. `Archivos generados automáticamente`: Como archivos compilados (.class, .o, .exe), módulos de dependencias (node_modules/, vendor/), archivos de caché, logs (.log), archivos temporales, etc.

2. `Archivos de configuración local`: Configuraciones específicas de tu entorno de desarrollo, credenciales de API, variables de entorno que no deben ser compartidas.

3. `Archivos específicos del IDE (Entorno de Desarrollo Integrado)`: Carpetas y archivos que tu IDE usa para su funcionamiento (.idea/, .vscode/, .DS_Store).

Incluir estos archivos en el repositorio Git no solo lo hace innecesariamente grande, sino que también puede causar conflictos con otros desarrolladores, exponer información sensible o simplemente ensuciar el historial de tu proyecto con cambios irrelevantes.

Aquí es donde entra el archivo `.gitignore`, su función principal es indicarle a Git qué archivos y directorios debe ignorar y no incluir en el control de versiones. Cuando Git ejecuta un comando como `git status` o `git add`, consulta el archivo `.gitignore` para saber qué elementos debe pasar por alto.

¿Dónde colocar el archivo .gitignore?

- En la raíz del repositorio: Esta es la ubicación más común y recomendada. Un archivo .gitignore en el directorio raíz de tu proyecto afectará a todo el repositorio.

<a id="espeficar-archivos-ignorados"></a>
#### Especificar archivos

1. Ignorar un archivo específico

```
my_secret_key.pem
```

2. Ignorar todos los archivos con una extensión específica
```
*.log        # Ignora todos los archivos .log
*.tmp        # Ignora todos los archivos .tmp
```

3. Ignorar un directorio
```
build/       # Ignora el directorio 'build' y todo lo que hay dentro
node_modules/ # Común para proyectos Node.js
```

4. Ignorar archivos en un directorio específico, pero no en otros:
```
src/*.log    # Ignora archivos .log solo dentro del directorio 'src'
!src/*.tmp   # Ignora archivos .tmp en cualquier otro directorio
```

5. Ignorar un patrón en cualquier parte del proyecto

```
**/temp      # Ignora cualquier archivo o directorio llamado 'temp' en cualquier nivel de repositorio
```

6. Ignorar un archivo con un nombre específico en cualquier subdirectorio:

```
**/config.json # Ignora cualquier archivo 'config.json' dondequiera que se encuentre
```

- Ejemplo de un archivo .gitignore:
```
# Archivos de logs
*.log
logs/
error.txt

# Archivos de compilación
*.class
*.jar
*.pyc
/target/

# Dependencias de Node.js
node_modules/

# Archivos de configuración local y sensible
.env
config.local.js
*.env.local

# Archivos del sistema operativo
.DS_Store # macOS
Thumbs.db # Windows

# Archivos del IDE
.idea/
.vscode/
*.swp   # Vim swap files
```

<a id="git-branches"></a>
## Ramas (Branches) en Git

<a id="que-son-las-ramas-y-su-uso"></a>
### ¿Qué son las ramas y por qué utilizarlas?
Podemos imaginar a las ramas como caminos que se bifurcan desde un punto común. La rama principal (generalmente llamada main o master) representa la línea principal de desarrollo, mientras que las ramas adicionales permiten explorar diferentes direcciones sin afectar el código principal.

![image](https://github.com/user-attachments/assets/491795be-95c6-41ff-b395-4a7146843070)




1. `Desarrollo paralelo`: Permiten que múltiples desarrolladores trabajen en diferentes características o correcciones de errores al mismo tiempo sin interferir entre sí.

2. `Aislamiento de cambios`: Cualquier cambio que se haga en una rama no afecta a otras ramas hasta que se decida fusionarla. Esto es crucial para probar nuevas funcionalidades sin romper la versión estable del código.

3. `Experimentación segura`: Se puede experimentar con nuevas ideas o enfoques radicales en una rama sin miedo a estropear el proyecto principal. Si la idea no funciona, simplemente eliminas la rama.

4. `Flujos de trabajo organizados`: Las ramas son la base de flujos de trabajo como Git Flow o GitHub Flow, que ayudan a organizar el proceso de desarrollo y despliegue de software.

5. `Revisión de código`: Las ramas son intrínsecas a los Pull Requests (en GitHub) o Merge Requests (en GitLab), donde el código es revisado por otros antes de ser integrado en la rama principal.

<a id="comandos-de-ramas"></a>
### Comandos de ramas
Ahora que entendemos la importancia, veamos los comandos clave para manipular ramas.

<a id="comando-git-branch"></a>
#### git branch: Crear, listar y borrar ramas
El comando `git branch` es la herramienta principal para gestionar las ramas en tu repositorio local.

> Uso

1. Listar todas las ramas locales
- Input:
```
  git branch
```

- Output:
```
* main
  feature/nueva-funcionalidad
  bugfix/error-login  
```

Donde el asterisco (*) indica la rama actual.

2. Crear una nueva rama
```
git branch <nombre-de-la-nueva-rama>
```

- **Esto crea la rama, pero no te mueve a ella**

3. Borrar una rama local (después de fusionarla)
```
git branch -d nombre-de-la-rama-a-borrar
```

> [!IMPORTANT]
> 
> - La opción `-d (o --delete)` es una "eliminación segura". Solo permite borrar la rama **si ya ha sido fusionada en la rama actual** (o en la rama que especificaste como upstream). Esto previene la pérdida de trabajo no fusionado.

4. Borrar una rama local (forzado)
```
git branch -D nombre-de-la-rama-a-borrar
```

- La opción `-D (o --delete --force)` forzará la eliminación de la rama, **incluso si contiene cambios que aún no han sido fusionados** en otra rama. 

<a id="comando-git-checkout"></a>
#### git checkout: Cambiar entre ramas
El comando `git checkout` sirve para cambiar entre ramas y restaurar archivos del historial. Aunque su uso para cambiar de rama es muy común, es importante saber que en versiones recientes de Git (2.23+), el comando  `git switch` **se introdujo específicamente para esta tarea, haciendo el checkout más enfocado en restaurar archivos**.

- ¿Cómo funciona? 

1. Actualiza el área de trabajo `(working directory)` para que refleje la instantánea del commit al que apunta esa rama.

2. Actualiza tu área de preparación `(staging area)`.

3. Mueve el puntero `HEAD` (que indica tu rama actual) a la rama que has seleccionado.

> Uso

1. Cambiar a una rama existente:
```
  git checkout <nombre-de-la-rama-existente>
```

2. Crear una nueva rama y cambiar a ella inmediatamente:
```
  git checkout -b <nombre-de-la-nueva-rama>
```

- La opción -b (o --branch) es un atajo para `git branch <nombre-de-la-nueva-rama>` 

> [!IMPORTANT]
>
>  - En nuevas versiones de Git, `git switch` es la opción preferida para cambiar de rama:
> 
> ```git switch <nombre-de-la-rama-existente>```
> 
>  ```git switch -c <nombre-de-la-nueva-rama> # Crear y cambiar```

<a id="comando-git-merge"></a>
#### git merge: Combinar cambios de una rama a otra
El comando `git merge` te permite integrar los cambios de una rama en otra. Es la forma más común de combinar líneas de desarrollo.

Cuando se intenta fusionar una rama (por ejemplo, `feature-x`) en otra (por ejemplo, `main`), Git intenta integrar los cambios de `feature-x` en `main`. Hay dos escenarios principales:

1. `Fast-Forward Merge (Avance Rápido)`: Si la rama `main` **no ha tenido cambios desde que se creó la rama que con la que se quiere fusionar (feature-x)**, Git simplemente **mueve el puntero de `main` hacia adelante al último commit de `feature-x`**. 

2. `Three-Way Merge (Fusión de Tres Vías)`: Si ambas ramas (`main` y `feature-x`) han evolucionado de forma independiente **desde su punto de ancestro común**, Git **realiza una fusión de tres vías**. Esto significa que Git necesita comparar el ancestro común con los estados de ambas ramas para crear **un nuevo commit de fusión que contenga los cambios de ambas ramas**.

> Uso

1. Primero, se debe de asegurar de estar en la rama que va a recibir los cambios:
```
git switch main # O git checkout main
```

2. Fusionamos la rama
```
git merge feature-x
```

<a id="merge-conflicts"></a>
### Resolución de conflictos de fusión (Merge Conflicts)
Un conflicto de fusión ocurre cuando Git no puede fusionar automáticamente los cambios de dos ramas diferentes en el mismo lugar de un archivo. Esto sucede típicamente en los siguientes escenarios:

1. `Modificaciones idénticas en la misma línea`: Dos ramas editan la misma línea de código de forma diferente.

2. `Un archivo modificado y otro eliminado`: Una rama modifica un archivo mientras la otra lo elimina.

3. `Un archivo modificado y otro renombrado`: Una rama modifica un archivo mientras la otra lo renombra.

Cuando Git encuentra un conflicto, **no puede proceder con la fusión** y te lo notifica, dejando el repositorio en un estado de "fusión en curso" (`MERGING`). En este punto, **Git espera que se intervenga y se resuelva el desacuerdo manualmente**.

> El Proceso de resolución de conflictos

1. Cuando ocurre un conflicto, se mostrará un mensaje cómo:

```
On branch main
You have unmerged paths.
  (fix conflicts and run "git commit")
  (use "git merge --abort" to abort the merge)

Unmerged paths:
  (use "git add <file>..." to mark resolution)
        both modified:   src/app.js
```       

- Esto significa que `src/app.js` tiene un conflicto.

2. Identificar los archivos en conflicto: `git status` también sirve para indicarte qué archivos tienen conflictos.


3. Abrir los archivos en conflicto: Abre cada archivo en conflicto en un editor de código preferentemente. Dentro de estos archivos, **Git habrá insertado unos marcadores de conflicto especiales** para mostrar dónde están las diferencias y de dónde provienen:
```
<<<<<<< HEAD
Esta es la versión de la línea en la rama actual (HEAD, es decir, 'main' o la rama en la que se estaba iniciando la fusión).
=======
Esta es la versión de la línea en la rama que se está intentando fusionar (por ejemplo, 'feature/new-feature').
>>>>>>> feature/new-feature
```

- `<<<<<<< HEAD`: Marca el inicio del conflicto y el contenido de la rama actual.

- `=======`: Separa las dos versiones en conflicto.

- `>>>>>>> nombre-de-la-rama`: Marca el final del conflicto y el contenido de la rama se está queriendo fusionar.


4. Editar manualmente el archivo: Uno tiene que decidir qué versión de las líneas en conflicto se quiere mantener. Tienes tres opciones:

- Mantener los cambios actuales (HEAD): Elimina el contenido de la otra rama.

- Mantener los cambios de la otra rama: Elimina el contenido de la rama actual.

- Combinar ambos: Se permite integrar ambos conjuntos de cambios de la manera que tenga sentido lógico.

> Ejemplo

- Si el conflicto es:
```
function greet() {
<<<<<<< HEAD
    console.log("Hello, world!");
=======
    console.log("Hi there!");
>>>>>>> feature/spanish-greeting
}
```

- Uno puede quedarse con los cambios actuales y eliminar los cambios de la otra rama:
```
function greet() {
    console.log("Hello, world!");
}
```

5. Una vez que se haya editado el archivo y eliminado todos los marcadores de conflicto, se debe de indicar que el conflicto en ese archivo ha sido resuelto. Esto se hace usando `git add`:
```
git add src/app.js
```

> [!IMPORTANT]
> 
> Si se tienen varios archivos en conflicto, se debe de repetir este proceso para cada uno de ellos y luego `git add` en cada archivo resuelto.

6. Completar la fusión: Una vez que todos los archivos en conflicto han sido resueltos y marcados con `git add`, se finaliza la fusión con un `git commit`

> [!IMPORTANT]
> 
> Si se inicia una fusión, y existen conflictos y no se quiere continuar con la fusión, entonces, se tiene que utilizar el comando:
>
> - `git merge --abort`

<a id="comando-git-rebase"></a>
#### git rebase: Reorganizar el historial de confirmaciones
El comando `git rebase` permite **reorganizar o reescribir el historial de confirmaciones**

> [!NOTE]
> A diferencia de `git merge`, que crea un nuevo commit de fusión, `git rebase` **toma los commits de LA rama y los "reproduce" sobre otra base**, haciendo que parezca que la rama se creó directamente desde el punto final de esa nueva base.

1. Antes de Rebase:
```   
A -- B -- C (main)
      \
       D -- E (feature)
```

2. Después de `git rebase` main en feature:
```
A -- B -- C (main)
           \
            D' -- E' (feature)
```

- **Donde D' y E' son los mismos cambios que D y E**, pero con nuevos hashes de commit porque su "padre" (`HEAD`) ha cambiado.

1. Primero, se debe de asegurar de estar en la rama que se quiere rebasar (la rama de trabajo):
```
git switch feature/nueva-funcionalidad
```

2. Luego, se ejecuta el rebase sobre la rama objetivo (por ejemplo, `main`)
```
git rebase main
```

<a id="estrategias-de-ramificacion"></a>
### Estrategias de ramificación
Las estrategias de ramificación son metodologías que los equipos de desarrollo adoptan para organizar el uso de las ramas en Git. Su objetivo principal es **optimizar el flujo de trabajo, mejorar la colaboración y asegurar la estabilidad del código**.

<a id="git-flow"></a>
#### Git Flow
Está diseñada para proyectos con **ciclos de lanzamiento bien definidos**  que requieren un historial muy limpio y organizado. Es más compleja que otras estrategias, pero ofrece un control granular sobre el proceso de desarrollo y liberación.

- Git Flow se basa en dos ramas principales de larga duración y varias ramas de apoyo de corta duración

 > Ramas principales de Git Flow:

1. Rama `main`
  - `Propósito`: Contiene el código de producción estable y listo para ser desplegado.
  - `Historial`: Cada confirmación en main debe ser una versión liberada.
  - `Vida útil`: Es una rama permanente.

2. Rama `develop`
  - `Propósito`: Contiene el código de desarrollo más reciente, donde **se integran todas las nuevas características y correcciones**
  - `Historial`: Representa el estado actual de desarrollo que eventualmente se convertirá en la próxima versión.
  - `Vida útil`: Es una rama permanente.

3. Rama `feature/` (Ramas de Características):
  - `Origen`: Creadas a partir de develop.
  - `Propósito`: Desarrollar una nueva característica de forma aislada. Cada característica tiene su propia rama.
  - `Convención de nombres`: **feature/<nombre-caracteristica>** (ej., feature/login-oauth).
  - `Integración`: Cuando la característica está completa, se fusiona de vuelta en develop. **Se eliminan después de la fusión**.

4. Rama `release/` (Ramas de Lanzamiento)
  - `Origen`: **Creadas a partir de develop** cuando el develop está lo suficientemente maduro para una nueva versión.
  - `Propósito`: Preparar una nueva versión de producción. **Solo se permiten correcciones de errores (bug fixes)** y preparación final (número de versión, etc.). **No se añaden nuevas características**.
  - `Convención de nombres`: **release/<numero-version>** (ej., release/1.0.0).
  - `Integración`: Cuando la versión está lista, se fusiona tanto en `main` (para ser desplegada) como en `develop` (para asegurar que las correcciones también estén en la próxima versión). **Se etiquetan con un tag (git tag) en main para marcar la versión.**
  - `Vida útil`: Una vez que se realiza la liberación, la rama se elimina.

5. Rama `hotfix/` (Ramas de correcciones urgentes)
  - `Origen`: Creadas a partir de `main` cuando se necesita una corrección urgente para un error en producción.
  - `Propósito`: Arreglar rápidamente un error crítico en la versión desplegada sin esperar al ciclo de desarrollo normal.
  - `Convención de nombres`: **hotfix/<descripcion-error>** (ej., hotfix/bug-sesion-caducada).
  - `Integración`: Cuando la versión está lista, se fusiona tanto en `main` (para ser desplegada) como en `develop` (para asegurar que las correcciones también estén en la próxima versión).  **Se etiquetan con un tag (git tag) en main para marcar la versión.**
  - `Vida útil`: Una vez que se realiza la corrección, la rama se elimina.

6. Rama `bugfix/` (Ramas de correcciones antes de la liberación)

> Desventajas de Git Flow 

* `Complejidad`: Requiere más ramas y más comandos de Git, lo que puede ser abrumador para equipos pequeños o nuevos en Git.

* `No es ideal para CI/CD`: Su rigidez puede dificultar flujos de integración y despliegue continuo (CI/CD) donde los despliegues son frecuentes.

- ¿Cuándo usarlo? Proyectos grandes, software con lanzamientos programados (software de escritorio, librerías, etc.), o **equipos que necesitan un proceso muy estructurado**.

<a id="github-flow"></a>
#### GitHub Flow
Es una estrategia mucho más ligera y sencilla que `Git Flow`, popularizada por GitHub (obviamente). **Está diseñada para equipos que despliegan con frecuencia (varias veces al día, incluso) y buscan un proceso de desarrollo continuo e iterativo**.

> Principios clave de GitHub Flow

GitHub Flow se basa en **solo una rama principal y ramas de características de corta duración, centradas alrededor de los Pull Requests**.

1. Rama `main`:
   - `Propósito`: La única rama principal. **Todo el código en main debe ser desplegable en cualquier momento**.
   - `Historial`: Es la fuente de la verdad para la versión en producción.
   - `Vida útil`: Permanente.

- Flujo de desarrollo:

1. `Crear una rama de característica`: Siempre se crea una nueva rama desde main **para cada nueva característica o corrección de error**.
    - Convención de nombres: Descriptiva y corta (ej., **add-user-profile**, **fix-login-bug**).

2. `Trabajar y confirmar`: Se desarrollan los cambios en esta rama, realizando confirmaciones frecuentes y significativas.

3. `Abrir un Pull Request (PR)`: Cuando la característica está lista (o incluso si no lo está pero necesitas feedback), **se abre un PR desde la rama de característica hacia la rama `main`**.

  - Revisión de código: El PR se utiliza para discutir los cambios, recibir feedback y realizar más iteraciones. Se ejecutan pruebas automatizadas (CI).
  - Discusión y colaboración: Otros miembros del equipo revisan el código, sugieren mejoras, y se aseguran de que el código cumpla con los estándares.

4. `Desplegar para probar (opcional pero recomendado)`: Idealmente, el PR se despliega a un entorno de **staging o pre-producción** para pruebas finales.

5. `Fusionar en main`: Una vez que el código ha sido revisado, probado y aprobado, **se fusiona la rama de característica en main**.

6. `Eliminar la rama de característica`: Una vez fusionada y desplegada, **la rama de característica se elimina**.

> Ventajas

1. Integración continua: Promueve la integración frecuente de cambios, reduciendo el riesgo de "integraciones grandes y dolorosas".
2. Despliegue continuo (CD): Facilita los despliegues frecuentes y automáticos, ya que main siempre está lista.
3. Colaboración centrada en PRs: Los Pull Requests son el eje central de la comunicación y la revisión.

> Desventajas
1. Menos control sobre versiones: No tiene un proceso explícito para lanzar versiones mayores o menores.

- ¿Cuándo usarlo? Proyectos web, aplicaciones móviles, SaaS, equipos que practican el CI/CD, startups, o cualquier proyecto que necesite iterar y desplegar rápidamente.

<a id="trunk-based-development"></a>
#### Trunk-based development
Trunk-Based Development (TBD) es una estrategia de control de versiones donde **los desarrolladores integran sus cambios en una única rama principal** (el "tronco" o main) **al menos una vez al día**. El objetivo es mantener esta rama principal siempre en un estado "desplegable" y funcional, evitando ramas de larga duración y fusiones complejas.

> Principios clave de Trunk-Based Development

1. `Una sola rama principal`: Solo existe una rama principal (main o trunk) que es la fuente de la verdad.

2. `Ramas de corta duración`: Los desarrolladores crean ramas muy pequeñas y de muy corta duración (a menudo solo por unas horas) para sus cambios, o incluso trabajan directamente en la rama principal para cambios muy pequeños

3. `Integración Continua (CI) intensa`: La integración es constante. Los cambios se fusionan en main muy rápidamente, a menudo múltiples veces al día. **Las pruebas automatizadas son esenciales para detectar problemas de inmediato**.

4. `Despliegue Continuo (CD)`: Dado que la rama principal siempre debe ser desplegable, TBD es ideal para pipelines de CI/CD que despliegan a producción con alta frecuencia.

5. `Reversibilidad`: Los cambios deben ser pequeños y fáciles de revertir si causan problemas.


> Flujo de Trabajo (simplificado)

1. `Actualizar la rama principal`: Los desarrolladores siempre hacen `git pull` de main antes de empezar a trabajar.

2. `Cambios pequeños y frecuentes`:

- Para cambios muy pequeños: **trabajar directamente en main y confirmar**.

- Para cambios un poco más grandes: **crear una rama de característica** de MUY corta duración, hacer los cambios, **abrir un PR (ligero y rápido), y fusionar en `main`** en horas.

3. `Pruebas automatizadas`: El CI se ejecuta en cada confirmación o PR en `main`.

4. `Despliegue frecuente`: La `main` se despliega a producción con alta frecuencia.

> Ventajas

1. `Máxima integración continua`: Reduce drásticamente los conflictos de fusión y los problemas de integración al integrar constantemente.
2. `Historial lineal y limpio`: El historial es muy fácil de seguir, ya que la mayoría de los cambios van directamente a la rama principal.

> Desventajas

1. `Requiere alta disciplina`: Los desarrolladores deben hacer commits pequeños y frecuentes y **confiar mucho en las pruebas automatizadas**.
2. `Dependencia de Feature Flags`: Para características grandes, la gestión de feature flags añade una complejidad adicional.

- ¿Cuándo usarlo? Equipos de desarrollo ágiles y maduros, proyectos con alta frecuencia de despliegue, microservicios, o cualquier equipo que busque maximizar la velocidad y la integración continua.


<a id="conceptos-avanzados-de-git"></a>
## Conceptos Avanzados de Git

<a id="revertir-cambios"></a>
### Revertir cambios
Cuando se trabaja con Git, es común deshacer cambios. Git ofrece principalmente dos comandos para esto: `git revert` y `git reset`. Aunque ambos logran un objetivo similar, lo hacen de maneras fundamentalmente diferentes, lo que los hace adecuados para distintos escenarios.

<a id="comando-git-revert"></a>
#### git revert: Crear una nueva confirmación y deshacer una confirmación anterior
El comando `git revert <commit-hash>` se utiliza para **deshacer los cambios introducidos por una confirmación específica**.

> [!IMPORTANT]
>
>  - La clave aquí es que `git revert` **no elimina la confirmación original del historial**; en su lugar, crea una nueva confirmación que **anula los cambios de la confirmación que se está revirtiendo**.

- ¿Cuándo usarlo?

1. Cuando se necesita deshacer una confirmación que **ya ha sido empujada a un repositorio remoto** y es pública.

2. Si quieres revertir cambios en una rama compartida sin afectar el historial de otros colaboradores.

3. Para deshacer accidentalmente una confirmación en `main` o una rama principal.

<a id="comando-git-reset"></a>
#### git reset: Mover el puntero del HEAD a una confirmación anterior
El comando `git reset <modo> <commit-hash>` es mucho más potente y **puede ser destructivo**, ya que **reescribe el historial del repositorio**. Mueve el puntero `HEAD` a una confirmación anterior, eliminando efectivamente las confirmaciones posteriores de la rama actual.

> Modos de git reset:

* `--soft`: Mueve `HEAD` al commit-hash especificado. **Los cambios** de las confirmaciones que se están "deshaciendo" **permanecen en el área de staging**. Es útil si se quiere combinar varias confirmaciones recientes en una sola.

* `--mixed (por defecto)`: Mueve `HEAD` al commit-hash especificado y también **restablece el área de staging para que coincida con esa confirmación**. **Los cambios de las confirmaciones "deshechas" se mueven al directorio de trabajo (archivos no preparados)**. Es útil para deshacer una confirmación y seguir trabajando en esos cambios.

> [!IMPORTANT]
>
> * `--hard`: Es el más drástico. Mueve HEAD al commit-hash especificado, **restablece el área de staging y modifica tu directorio de trabajo para que coincida exactamente con la confirmación de destino**
>   
> Todos los cambios no confirmados y no registrados después del commit-hash **se perderán permanentemente**

- ¿Cuándo usarlo?

1. Es ideal para **limpiar un historial de confirmaciones** antes de empujar los cambios a un repositorio remoto
   
2. Para deshacer confirmaciones erróneas que aún no han sido compartidas

3. Para reorganizar confirmaciones locales 

<a id="stashing"></a>
### Stashing
A menudo, uno está trabajando en una función y de repente surge algo más urgente que necesita tu atención. Pero no se quiere confirmar el trabajo a medias que estabas realizando antres porque no está listo. Aquí es donde entra `git stash`.

<a id="comando-git-stash"></a>
#### git stash: Guardar temporalmente cambios no confirmados

`git stash` es un comando útil que te permite guardar **temporalmente** los cambios no confirmados (tanto los **archivos modificados como los archivos en el área de staging***) y luego volver a un estado de directorio de trabajo limpio. Es como poner tu trabajo en pausa, sin tener que crear una confirmación incompleta.

- ¿Cómo funciona?

Cuando se ejecuta `git stash`, Git toma los cambios modificados y no confirmados, los guarda en una "pila" interna de stashes, y luego limpia tu directorio de trabajo y el área de staging, **volviéndolos al estado de la última confirmación.**

> Comandos útiles de git stash:

1. `git stash save "Mensaje opcional" o simplemente git stash`: Guarda los cambios actuales. Se puede añadir un mensaje para describir el stash.

2. `git stash list`: Muestra una lista de todos los stashes que se han guardado. **Cada stash se identifica con un índice** (por ejemplo, stash@{0}, stash@{1}).

3. `git stash apply <stash-id>`: Aplica los cambios de un stash específico al directorio de trabajo actual. **Los cambios se aplican, pero el stash permanece en la lista**. Si no especificas un <stash-id>, aplica el stash más reciente (stash@{0}).

4. `git stash pop <stash-id>`: Similar a apply, pero elimina el stash de la lista después de aplicarlo. Generalmente es la opción preferida si estás seguro de que ya no se necesitará ese stash.

5. `git stash drop <stash-id>`: Elimina un stash específico de la lista **sin aplicarlo**.

6. `git stash clear`: Elimina **todos** los stashes de la lista.

<a id="cherry-picking"></a>
### Cherry-picking
A veces, no se quiere fusionar toda una rama, pero hay una o dos confirmaciones específicas de esa rama que sí se quiere traer a la rama actual. Aquí es donde `git cherry-pick` brilla.

<a id="comando-git-cherry-pick"></a>
#### git cherry-pick: Aplicar una confirmación específica de una rama a otra
El comando `git cherry-pick <commit-hash>` te **permite aplicar los cambios introducidos por una confirmación existente de cualquier rama a la rama actual**. Git toma el parche de la confirmación especificada y lo aplica como una nueva confirmación en la rama actual.

> Características y consideraciones:

- Es útil para replicar correcciones de errores o nuevas características **específicas** en diferentes ramas sin tener que fusionar ramas enteras.

- Usar cherry-pick de forma extensiva puede llevar a un historial de confirmaciones más complejo y con cambios duplicados, lo que a veces puede dificultar el seguimiento.

- Al igual que con merge o rebase, **pueden surgir conflictos** si los cambios que intentas aplicar entran en conflicto con el código de la rama actual. 

¿Cuándo usarlo?

1. Si se ha corregido un error crítico en una rama de desarrollo y se necesita aplicar rápidamente esa corrección a una rama de producción sin fusionar todas las demás características en desarrollo.

2. Cuando solo unas pocas confirmaciones de una rama son relevantes para otra, y una fusión completa sería demasiado grande o incluiría cambios no deseados.

<a id="reflog"></a>
### Reflog
En ocasiones por carga de trbajo tiende uno preguntarse: "¿Qué demonios hice en Git hace cinco minutos?". O, "Acabo de hacer un reset --hard y ahora no sé dónde estaba mi HEAD." Si tienes estás situaciones, `git reflog` es de suma importancia.

<a id="comando-git-reflog"></a>
#### git reflog: El historial del repositorio
El comando `git reflog` (abreviatura de "reference logs") es una herramienta que registra cada vez que la punta de una rama o `HEAD` se actualiza en el repositorio local. Esto significa que registra casi cualquier acción que modifique el historial del repositorio, como confirmaciones, fusiones, rebase, resets, cherry-picks y stashes.

> Ejemplo de uso:

1. Imaginemos que accidentalmente se hizo un `git reset --hard HEAD~2` y se perdieron algunas confirmaciones.

2. Se ejecuta el comando `git reflog`.

3. Se verán una lista de entradas, como:
  ```
    a1b2c3d HEAD@{0}: reset: moving to HEAD~2
    e4f5g6h HEAD@{1}: commit: Add new feature X
    i7j8k9l HEAD@{2}: commit: Fix bug Y
    ...
  ```

4. Se identifica la confirmación `e4f5g6h` o `i7j8k9l` como el estado al que se quiere volver antes del reset.

5. Se ejecuta `git reset --hard e4f5g6h` (o el hash de la confirmación deseada del reflog) para restaurar la rama a ese punto.

> [!IMPORTANT]
> 
> - El reflog es local para tu repositorio. No se comparte cuando empujas cambios a un repositorio remoto. Esto significa que si eliminas o clonas de nuevo un repositorio, perderás su reflog.

<a id="colaboracion-con-github"></a>
## Colaboración con Git y GitHub
GitHub no es Git; **es un servicio de alojamiento de repositorios Git** basado en la web que añade una capa de funcionalidades sociales y de gestión de proyectos sobre Git.

<a id="repositorios-remotos"></a>
### Repositorios remotos
Un repositorio remoto **es una versión de un proyecto** que reside en un servidor en internet o en una red, en lugar de estar en una máquina local. Actúa como el centro neurálgico para que múltiples colaboradores trabajen en el mismo proyecto.

<a id="repositorios-en-github"></a>
#### Repositorios en GitHub
GitHub es el servicio de alojamiento de repositorios remotos más popular. Cuando se crea un repositorio en GitHub, se está creando una copia de algún proyecto que está accesible para otros (**si es público**) o para tu equipo (si es privado). Este repositorio remoto sirve como la "fuente de la verdad" del proyecto.

> Algunos beneficios

1. Permite que varios desarrolladores trabajen en el mismo proyecto, fusionando sus cambios sin problemas.

2. El código está almacenado de forma segura fuera de una máquina local, protegiéndolo de pérdidas.

3. Permite gestionar quién tiene permiso para leer o escribir en un repositorio.

4. GitHub ofrece funcionalidades como Issues (para seguimiento de errores y tareas), Pull Requests (para revisión de código), Wikis y Pages.

<a id="configuracion-de-conexion"></a>
#### Configuración de conexión
Para que el repositorio Git local se comunique con un repositorio remoto en GitHub, se necesita que configurar una conexión. Esto generalmente implica el uso de protocolos SSH o HTTPS.

1. HTTPS
Solo se necesita eñ nombre de usuario y contraseña (o un token de acceso personal si se tiene la autenticación de dos factores activada) para autenticarte. Es conveniente porque funciona a través de la mayoría de los cortafuegos y proxies.

2. SSH:
Ofrece una mayor seguridad y comodidad una vez configurado. En lugar de usar tu nombre de usuario y contraseña en cada operación, se utilizan un par de claves SSH (una pública y una privada). La clave pública se añade a tu cuenta de GitHub, y la clave privada permanece segura en la máquina local.

Esto permite una autenticación sin contraseña para las operaciones de Git. Aunque su configuración inicial es un poco más compleja, es preferido para desarrolladores que realizan muchas interacciones con repositorios remotos.

<a id="comandos-para-repositorios-remotos"></a>
### Comandos para repositorios remotos
Estos comandos son esenciales para interactuar con repositorios en GitHub.

<a id="comando-git-remote"></a>
#### git remote: Gestionar repositorios remotos
`git remote` permite gestionar las conexiones del repositorio local con los repositorios remotos.

> Comandos

1. `git remote`: Lista los nombres de los repositorios remotos configurados

2. `git remote -v`: Muestra los nombres de los remotos junto con sus URLs

3. `git remote add <nombre_remoto> <URL`>: Añade un nuevo repositorio remoto a la configuración local. `Por ejemplo, git remote add upstream https://github.com/proyecto/repo.git`

4. `git remote rm <nombre_remoto>`: Elimina una **conexión** a un repositorio remoto.

5. `git remote rename <nombre_antiguo> <nombre_nuevo>`: Cambia el nombre de un repositorio remoto existente

<a id="comando-git-clone"></a>
#### git clone: Clonar un repositorio existente de GitHub

El comando `git clone <URL_del_repositorio>` es el punto de partida para la mayoría de los proyectos en los que deseas colaborar. Cuando clonas un repositorio:

1. Descarga una copia completa del repositorio remoto (incluyendo todo su historial de confirmaciones, ramas, etc.) a la máquina local.

2. Crea una nueva carpeta con el nombre del repositorio (a menos que se especifique otro).

3. Configura automáticamente el remoto origin **apuntando a la URL desde donde ha sido clonado**.

4. Configura la rama local main (o master) para rastrear la rama remota correspondiente.

```
Ejemplo: git clone https://github.com/usuario/mi-proyecto.git
```

<a id="comando-git-push"></a>
#### git push: Subir cambios locales a un repositorio remoto

El comando `git push <nombre_remoto> <nombre_rama>` se utiliza para enviar las confirmaciones locales a un repositorio remoto. Es cómo se comparte el trabajo local con el resto del equipo para la actualización del repositorio central.

> [!IMPORTANT]
> 
> - Si el repositorio remoto tiene cambios que no se tienen en el local, Git pedirá que se haga un `pull` antes de hacer el `push` (para evitar sobrescribir el trabajo de otros).


<a id="comando-git-pull"></a>
#### git pull: Descargar cambios de un repositorio remoto y fusionarlos
El comando `git pull <nombre_remoto> <nombre_rama>` es una operación de dos pasos que:

1. `git fetch`: Descarga los cambios (confirmaciones, ramas, etc.) del repositorio remoto al repositorio local. Estos cambios se almacenan en las "ramas de seguimiento remoto" (ej., origin/main).

2. `git merge`: Fusiona esos cambios descargados de la rama de seguimiento remoto en la rama local actual.

> [!IMPORTANT]
> 
> 1. Si se tiene cambios locales no confirmados, Git te pedirá que los guardes (stash) o los confirmes antes de hacer pull.
> 
> 2. Pueden ocurrir conflictos de fusión si los cambios remotos chocan con tus cambios locales. Deberás resolverlos manualmente.

<a id="comando-git-fetch"></a>
#### git fetch: Descargar cambios de un remoto sin fusionarlos
A diferencia de `git pull`, el comando `git fetch <nombre_remoto> <nombre_rama>` **solo descarga los cambios del repositorio remoto al repositorio local, pero no los fusiona automáticamente** en la rama de trabajo.

- Estos cambios se almacenan en las ramas de seguimiento remoto (por ejemplo, origin/main).

> ¿Por qué usar git fetch en lugar de git pull?
> 
> - Si no se está seguro de si los cambios remotos causarán conflictos, **fetch** te da la oportunidad de revisarlos y preparar la rama local antes de una fusión.
> - Una vez que has hecho fetch, se puede decidir cómo integrar esos cambios: `merge`, `rebase`, o incluso `cherry-pick` si solo se quieren algunas confirmaciones.

<a id="github-como-plataforma"></a>
## GitHub como plataforma
GitHub se ha consolidado como una plataforma integral para el desarrollo de software colaborativo. Ofrece un conjunto robusto de herramientas que facilitan la gestión de proyectos, la comunicación en equipo y la automatización del flujo de trabajo.

<a id="issues"></a>
### Issues
Los Issues son una funcionalidad central de GitHub que actúa como **un sistema de seguimiento y gestión de tareas dentro de un repositorio**. 

<a id="seguimiento-de-tareas-errores"></a>
#### Seguimiento de tareas, errores y mejoras
En esencia, los Issues **son la forma en que los equipos organizan y priorizan el trabajo**. Cada Issue es una entrada que puede representar:

1. `Errores (Bugs`): Cuando algo no funciona como se espera, se crea un Issue para describir el problema, reproducirlo y asignar a alguien para que lo corrija.

2. `Tareas (Tasks)`: Para desglosar proyectos grandes en piezas más pequeñas y manejables, cada una con su propio Issue. Por ejemplo, "Implementar la página de inicio de sesión".

3. `Mejoras (Enhancements/Features)`: Para proponer y discutir nuevas funcionalidades o mejoras al código existente. Por ejemplo, "Añadir un modo oscuro a la interfaz de usuario".

4. `Preguntas o discusiones`: A veces, un Issue puede ser simplemente un lugar para hacer una pregunta o iniciar una discusión sobre una parte del código o una decisión de diseño.

> Características clave de los Issues

1. `Título y descripción`: Un título conciso y una descripción detallada que explica el propósito del Issue.

2. `Asignados (Assignees)`: Personas responsables de trabajar en el Issue.

3. `Etiquetas (Labels)`: Para categorizar los Issues (por ejemplo, bug, feature, documentation, help wanted, priority: high)

4. `Milstones (Milestones)`: Para agrupar Issues relacionados en objetivos a un mayor plazo o en lanzamientos específicos del producto.

5. `Comentarios`: Un hilo de discusión donde los colaboradores pueden dejar comentarios, hacer preguntas, compartir capturas de pantalla o actualizaciones de progreso.

![image](https://github.com/user-attachments/assets/120c68de-74e6-43c7-9cd2-9b9f0c121805)


<a id="pull-request"></a>
### Pull Requests (PRs)
Son la forma estándar de proponer cambios a un repositorio y solicitar que esos cambios sean revisados y fusionados en una rama principal.

<a id="proceso-de-revision-de-codigo"></a>
#### Proceso de revisión de código
Un `Pull Request` es mucho más que una simple solicitud para fusionar código; es el inicio de un proceso de revisión de código colaborativo y estructurado:

1. `Creación del PR`: Un desarrollador crea una nueva rama, realiza sus cambios, los confirma y los sube a su repositorio (o a su fork del repositorio). Luego, abre un Pull Request **desde esa rama hacia la rama base** (comúnmente main o master) del repositorio. 

- El PR incluye: un título, una descripción (explicando los cambios y su propósito) y muestra las diferencias (diff) entre la rama propuesta y la rama base.

2. `Revisión por pares`: Otros miembros del equipo (revisores) examinan el código propuesto. Pueden dejar comentarios línea por línea, sugerir cambios, hacer preguntas o señalar posibles problemas (bugs, ineficiencias, violaciones de estándares de codificación)

3. `Iteración`: El autor del PR responde a los comentarios, realiza las modificaciones sugeridas y sube nuevas confirmaciones a su rama. 
- El PR **se actualiza automáticamente con estos nuevos cambios**.

4. `Aprobación y fusión`: Una vez que los revisores están satisfechos con los cambios y se han resuelto todas las discusiones, el PR es aprobado. En este punto, **se puede fusionar (merge) la rama del PR en la rama base**. GitHub ofrece diferentes estrategias de fusión (merge commit, squash and merge, rebase and merge).

5. `Cierre`: Una vez fusionado, **el PR se cierra automáticamente**, lo que indica que los cambios han sido integrados en la base de código principal. **La rama del PR puede eliminarse, ya que sus cambios ya forman parte del historial principal**. 

<a id="ci/cd-con-pull-request"></a>
#### Integración continua/Despliegue continuo (CI/CD) con PRs

<a id="ci/actions"></a>
### Actions

<a id="automatizacion-de-flujos-de-trabajo"></a>
#### Automatización de flujos de trabajo

<a id="gestion-de-proyectos"></a>
### Funcionalidades para la gestión de proyectos
GitHub, como plataforma, va más allá del control de versiones y la revisión de código. Ofrece un conjunto de funcionalidades robustas diseñadas para la gestión integral de proyectos, ayudando a los equipos a organizar tareas, documentar información, colaborar en ideas y comunicarse de manera efectiva

<a id="wikis"></a>
#### Wikis
Una Wiki en GitHub **es una sección integrada en cada repositorio** que permite a los colaboradores crear y mantener documentación directamente dentro del proyecto. Esencialmente, **es un sitio web simple y colaborativo donde se puede escribir contenido utilizando un formato de marcado ligero (como Markdown) para crear páginas, enlazarlas entre sí**.

> Propósito y usos comunes

1. `Documentación del proyecto`: Es un lugar ideal para almacenar información que no encaja directamente en el código o en los archivos README. Esto puede incluir:

- `Guías de inicio rápido`: Cómo configurar el entorno de desarrollo, cómo correr las pruebas, cómo desplegar el proyecto.

- `Arquitectura del sistema`: Diagramas, explicaciones de los componentes clave y sus interacciones.

- `Glosarios`: Definiciones de términos específicos del proyecto.

2. `Conocimiento compartido`: Las Wikis facilitan que los miembros del equipo compartan conocimientos y mantengan la información actualizada.

![image](https://github.com/user-attachments/assets/d8b2902c-8fad-49ad-8565-b6ee4b8b167f)

<a id="projects"></a>
#### Projects
La funcionalidad Projects (anteriormente **Project Boards**) **es una herramienta avanzada para la gestión de proyectos en GitHub**.Por una parte tenemos a los Issues, son elementos individuales de trabajo (tareas, bugs), los Projects son la herramienta para organizar y visualizar esos Issues en un flujo de trabajo. Un Issue puede existir por sí solo, pero un Project agrupa múltiples Issues (y PRs) para dar una visión macro del progreso.

> Propósito y usos comunes:

1.  Permiten visualizar el flujo de trabajo de un proyecto en un formato de tablero, con columnas que representan diferentes estados (por ejemplo, "To Do", "In Progress", "Done" o etapas personalizadas).

2.  Permiten asignar tareas a personas, establecer prioridades y marcar tareas como completadas.

3. Se pueden añadir Issues y PRs como "tarjetas" en el tablero y arrastrarlas entre columnas a medida que avanzan en el flujo de trabajo.


> Tipos de Projects

- `Tablas`: Son los tableros Kanban/Scrum clásicos, con columnas y tarjetas.

- `Hojas de cálculo`: Permiten una vista de tabla más tradicional, útil para listas grandes de elementos y para filtrar y ordenar.

- `Roadmaps`: Para visualizar hitos y el progreso de alto nivel.

![image](https://github.com/user-attachments/assets/f95fd77c-9602-4be2-9c5e-7f1032b74e6e)



<a id="discussions"></a>
#### Discussions
Las Discussions (Discusiones) son una funcionalidad más reciente de GitHub, diseñada para **fomentar conversaciones comunitarias que no son necesariamente sobre errores o características específicas (como en los Issues), sino más bien sobre ideas, preguntas generales, etc**.

> Características clave

1. `Categorías`: Las discusiones se pueden organizar en categorías predefinidas (por ejemplo, "General", "Ideas", "Q&A", "Announcements") para mantener el orden.

2. `Marcado como "Answered"`: Las preguntas pueden marcarse como resueltas, ayudando a otros usuarios a encontrar respuestas rápidamente.

3. `Suscripción`: Los usuarios pueden suscribirse a discusiones específicas o categorías para recibir notificaciones sobre nuevas publicaciones.

4. `Integración con Issues`: Las discusiones pueden convertirse en Issues si una idea madura lo suficiente como para requerir trabajo de desarrollo.

<a id="flujos-de-trabajo-colaborativo"></a>
### Flujos de trabajo colaborativos

<a id="forks"></a>
#### Fork: Contribuir a proyectos de código abierto
El flujo de trabajo de `Fork (bifurcación)` es el modelo predominante para la contribución a proyectos de código abierto en plataformas como GitHub. A diferencia del flujo de trabajo centralizado donde todos envían a un mismo repositorio, en el flujo de Fork, **cada colaborador trabaja en su propia copia independiente del repositorio original**.

Cuando se hace un fork de un repositorio, **GitHub crea una copia de ese repositorio bajo la cuenta del usuario (o organización)**. Esta copia es completamente propia de la cuenta, y permite hacer todos los cambios que se quieran hacer en ella sin afectar el repositorio original.

> Flujo de trabajo de Fork

El flujo de trabajo de Fork es el estándar de oro para proyectos de código abierto y cualquier escenario donde los colaboradores no tienen acceso directo de escritura al repositorio principal, o donde se desea un proceso de revisión de código estricto antes de la integración.


> Ventajas

- Los colaboradores pueden trabajar de forma independiente sin permisos de escritura en el repositorio original. Esto es fundamental para proyectos de código abierto.

- Los cambios de cada colaborador están contenidos en su propio fork hasta que son revisados y aceptados en el repositorio original.

- El repositorio original está protegido, ya que solo los mantenedores tienen permisos para fusionar código.


> Desventajas

- El flujo de trabajo puede ser más complejo de entender para los principiantes

- Cada fork es una copia completa, lo que puede ocupar espacio y requiere gestión
