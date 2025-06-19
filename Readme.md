# Secuencia de comandos Git
## Configuraciones iniciales

Desactiva el administrador de credenciales para evitar almacenamiento automático de credenciales a nivel global.
```bash
git config --global credential.helper ""
```

Permite almacenar las credenciales en texto plano en el repositorio local.
```bash
git config --local credential.helper "store"
```

Define el editor de texto por defecto para Git (por ejemplo, `vim`, `emacs` o `nano`).
```bash
git config --local core.editor emacs
```

Establece los datos del usuario que se registrarán en los commits.
```bash
git config --local user.name "<nombre_usuario>"
git config --local user.email "<correo_usuario>"
```

Lista todas las configuraciones de Git activas.
```bash
git config --list
```

## Obtener ayuda

Muestra ayuda detallada para el comando especificado.
```bash
$ git <comando> --help
```

## Inicialización y estado del repositorio

Crea un nuevo repositorio local de Git.
```bash
$ git init
```

Muestra los archivos modificados, no rastreados y listos para commit.
```bash
$ git status
```

## Agregar y quitar archivos

Agregar archivos al área de staging. Prepara archivos para el próximo commit.
```bash
$ git add <archivo o carpeta>
```

Agregar todos los archivos modificados
```bash
$ git add .
```

Quita archivos del área de staging sin eliminarlos del sistema de archivos.
```bash
$ git rm --cached <archivo>
```

## Commits e historial

Crear un commit. Guarda los cambios del área de staging al historial del repositorio.
```bash
$ git commit -m "<mensaje del commit>"
```

Ver el historial de commits. Muestra el historial completo de commits.
```bash
$ git log
```

Mostrar historial en forma de gráfico
```bash
$ git log --graph
```

Muestra el historial compacto en una sola línea por commit
```bash
$ git log --graph --pretty=oneline
```

Historial decorado y simplificado
```bash
$ git log --graph --decorate --all --oneline
```

Crear un alias (personalizado) para mostrar historial de forma gráfica
```bash
$ git config --local alias.tree "log --graph --decorate --all --oneline"
```

## Ignorar archivos

Crear archivo `.gitignore`. Este archivo debe incluir el nombre o patrón de los archivos a ignorar por Git.
```bash
# ejemplo de contenido .gitignore
*.log
node_modules/
.env
**/nombre.extencion
```

## Comparar cambios

Mostrar diferencias entre ramas o archivos
```bash
$ git diff
```

Comparar diferencias entre ramas
```bash
$ git diff <rama-1> <rama-2>
```

## Navegar en el historial

Moverse a un commit anterior (modo "detached HEAD")
```bash
$ git checkout <hash-del-commit>
```

Volver al último commit confirmado
```bash
$ git checkout HEAD
```

## Recuperación con `reset` y `reflog`

Restaurar el repositorio a un commit anterior (elimina cambios posteriores)
```bash
$ git reset --hard <hash>
```

Ver todo el historial de referencias (incluye cambios de HEAD)
```bash
$ git reflog
```

## Etiquetas (`tags`)

Crear una etiqueta (tag)
```bash
$ git tag prueba_uno
```

Ver todas las etiquetas existentes
```bash
$ git tag
```

Cambiarse a una etiqueta específica
```bash
$ git checkout tags/prueba_uno
```


## Ramas (`branches`)

Crear una nueva rama
```bash
$ git branch <nombre_rama>
```

Cambiar de rama
```bash
$ git switch <nombre_rama>
```

También puedes cambiar de rama con:
```bash
$ git checkout <nombre_rama>
```
También puedes crear una rama y cambiar a ella al mismo tiempo con:
```bash
$ git checkout -b <nombre_rama>
```
## Fusionar ramas

Para fusionar ramas usamos el comando ```merge``` pero primero hay que ubicandonos en la rama en la que queremos hacer los cambios:
```bash
$ git merge <nombre_rama_a_fusionar>
```

Fusionar una rama con otra (e.g.: fusionar `main` en `login`)
```bash
$ git switch login
$ git merge main
```

> Si se abre un editor de texto (vim) para escribir el mensaje de merge:
- Presiona **i** para entrar en modo edición  
- Escribe tu mensaje (opcional)  
- Presiona **Esc**, luego escribe `:wq` (write y quit) y presiona **Enter**

## Manejo de conflictos

Cuando haya un conflicto de fusión:
- Git marcará el archivo con líneas conflictivas  
- Edita manualmente el archivo para resolver el conflicto  
- Luego realiza un commit normal:
```bash
$ git add <archivo>
$ git commit -m "Conflicto resuelto"
```

## Git Stash

Guarda cambios sin hacer commit, útil cuando necesitas cambiar de rama sin perder lo que estás haciendo.

Guardar cambios sin hacer commit
```bash
$ git stash
```

Ver lista de stashes
```bash
$ git stash list
```

Recuperar los cambios guardados y eliminarlos del stash
```bash
$ git stash pop
```

Eliminar un stash manualmente
```bash
$ git stash drop
```

## Eliminar ramas

Borrar una rama local
```bash
$ git branch -d <rama>
```

Forzar el borrado una rama local
```bash
$ git branch --delete --force <rama>
```
> Aunque se borre, los commits aún existen si hay referencias a ellos.

## Conectar con GitHub

#### Crear una cuenta y repositorio en GitHub
- Crea una cuenta en [https://github.com](https://github.com)
- Crea un nuevo repositorio

Añadir origen remoto con clave SSH
```bash
$ git remote add origin git@github.com:tu-usuario/mi-proyecto.git
```

Envía los commits locales a la rama `main` en el repositorio remoto.
```bash
$ git push -u origin main
```

Envía los cambios locales al remoto ya configurado.
```bash
$ git push
```

Actualiza el repositorio local con los cambios remotos.
```bash
$ git pull
```

Clonar un repositorio remoto. Copia el contenido completo del repositorio remoto en el equipo local.
```bash
$ git clone https://github.com/usuario/repositorio.git
```

Verificar repositorio remoto configurado. Muestra las URL del repositorio remoto configurado.
```bash
$ git remote -v
```

### Instalar GitHub CLI

ver la version de gh instalado
```bash
gh  --version
```
To authenticate to GitHub, run the following command from your terminal.
```bash
gh auth login
```
Select where you want to authenticate to:
```bash

```
