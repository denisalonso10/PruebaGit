# Prueba Git

## Preparación inicial

Crear directorio y archivos de trabajo:
```bash
$ mkdir prueba_git
$ cd prueba_git
$ nano texto.txt
$ nano script.sh
```

## Inicialización

### Inicializar repositorio
```bash
$ git init
Initialized empty Git repository in C:/Users/Denís/prueba_git/.git/
```

Se crea un directorio `.git` donde se guarda toda la información del histórico del repositorio.

### Ver estado del repositorio
```bash
Denís@PC MINGW64 ~/prueba_git (master)
$ git status
On branch master

No commits yet

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        script.sh
        texto.txt

nothing added to commit but untracked files present (use "git add" to track)
```

### Cambiar nombre de rama
```bash
$ git branch -m main
```

## Añadiendo archivos

### Añadir archivo al área de preparación
```bash
Denís@PC MINGW64 ~/prueba_git (master)
$ git add script.sh
warning: in the working copy of 'script.sh', LF will be replaced by CRLF the next time Git touches it

Denís@PC MINGW64 ~/prueba_git (master)
$ git status
On branch master

No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
        new file:   script.sh

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        texto.txt
```

### Confirmar cambios
```bash
Denís@PC MINGW64 ~/prueba_git (master)
$ git commit -m "Confirmación inicial"
[master (root-commit) 9add33d] Confirmación inicial
 1 file changed, 2 insertions(+)
 create mode 100644 script.sh

Denís@PC MINGW64 ~/prueba_git (master)
$ git status
On branch master
Untracked files:
  (use "git add <file>..." to include in what will be committed)
        texto.txt

nothing added to commit but untracked files present (use "git add" to track)
```

## Modificando archivos

### Modificar archivo y ver cambios
```bash
Denís@PC MINGW64 ~/prueba_git (master)
$ git status
On branch master
Changes not staged for commit:
  (use "git add/rm <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   texto.txt

no changes added to commit (use "git add" and/or "git commit -a")

Denís@PC MINGW64 ~/prueba_git (master)
$ git status
On branch master
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        modified:   texto.txt

Changes not staged for commit:
  (use "git add/rm <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   texto.txt
```

### Confirmar modificaciones
```bash
Denís@PC MINGW64 ~/prueba_git (master)
$ git commit -m "Añadido archivo texto.txt"
[master 53faf1d] Añadido archivo texto.txt
 1 file changed, 3 insertions(+), 4 deletions(-)
```

## Información del repositorio

### Ver última versión confirmada
```bash
Denís@PC MINGW64 ~/prueba_git (master)
$ git show
commit 53faf1d3ee3303f53991bea2085403b75f6a72cb (HEAD -> master)
Author: Denís <denisalonsoo10@gmail.com>
Date:   Thu Oct 30 18:26:12 2025 +0100

    Añadido archivo texto.txt

diff --git a/texto.txt b/texto.txt
index faeb7aa..23c83ff 100644
--- a/texto.txt
+++ b/texto.txt
@@ -1,6 +1,5 @@
 uno
-dos
-
+dos
+tres
 cuatro
-seis
-siete
+cinco
```

### Ver histórico de cambios
```bash
Denís@PC MINGW64 ~/prueba_git (master)
$ git log
commit 53faf1d3ee3303f53991bea2085403b75f6a72cb (HEAD -> master)
Author: Denís <denisalonsoo10@gmail.com>
Date:   Thu Oct 30 18:26:12 2025 +0100

    Añadido archivo texto.txt

commit edeaaee66f7387c47065c8bd338083a0e10461f3 (tag: v0.7)
Author: denis alonso <hornet>
Date:   Thu Oct 30 11:49:57 2025 +0100

    Añadidos fuentes en java y archivos importantes

commit 8ce6ce7ce594d5a005ab3e493a4591374294fdfa
Author: denis alonso <hornet>
Date:   Thu Oct 30 11:05:20 2025 +0100

    Probando diff

commit 1711e5d66c5f8873d8f76e3b07519b62536fa4d1
Author: denis alonso <hornet>
Date:   Thu Oct 30 10:50:15 2025 +0100

    Ampliada la explicacion del texto

commit b49767fe97db93b6a4bd585a78c6234ba20a6d2b (tag: v0.3)
Author: denis alonso <hornet>
Date:   Thu Oct 30 09:42:32 2025 +0100

    Confirmacion inicial
```

## Diferencias

### Ver diferencias entre archivo modificado y último commit
```bash
Denís@PC MINGW64 ~/prueba_git (master)
$ git diff
diff --git a/.gitignore b/.gitignore
deleted file mode 100644
index 7a78820..0000000
--- a/.gitignore
+++ /dev/null
@@ -1,7 +0,0 @@
-# ignora los archivos terminados en .class
-*.class
-# ignora los archivos terminados en ~
-*~
-# pero no importante~, aun cuando había ignorado los archivos
-terminados en ~ en la linea anterior
-!importante~
diff --git a/Hola.java b/Hola.java
deleted file mode 100644
index 70f7bfc..0000000
--- a/Hola.java
+++ /dev/null
@@ -1,5 +0,0 @@
-class Hola {
-       public static void main(String[] args){
-               System.out.println("Welcome to the Java World");
-       }
-}
diff --git a/importante~ b/importante~
deleted file mode 100644
index e69de29..0000000
```

### Confirmar todos los cambios
```bash
Denís@PC MINGW64 ~/prueba_git (master)
$ git commit -a -m "Probando diff"
[master b8988c4] Probando diff
 3 files changed, 12 deletions(-)
 delete mode 100644 .gitignore
 delete mode 100644 Hola.java
 delete mode 100644 importante~

Denís@PC MINGW64 ~/prueba_git (master)
$ git diff
warning: in the working copy of 'texto.txt', LF will be replaced by CRLF the next time Git touches it
diff --git a/texto.txt b/texto.txt
index 23c83ff..346084f 100644
--- a/texto.txt
+++ b/texto.txt
@@ -3,3 +3,4 @@ dos
 tres
 cuatro
 cinco
+siete
```

## Ignorar archivos

### Crear archivo .gitignore
```bash
Denís@PCPRIME MINGW64 ~/prueba_git (master)
$ touch .gitignore

Denís@PC MINGW64 ~/prueba_git (master)
$ nano .gitignore

Denís@PC MINGW64 ~/prueba_git (master)
$ rm -r Hola.java

Denís@PC MINGW64 ~/prueba_git (master)
$ touch Hola.java

Denís@PC MINGW64 ~/prueba_git (master)
$ nano Hola.java

Denís@PC MINGW64 ~/prueba_git (master)
$ touch temporal~

Denís@PC MINGW64 ~/prueba_git (master)
$ touch importante~

Denís@PC MINGW64 ~/prueba_git (master)
$ ls -a
./  ../  .git/  .gitignore  Hola.java  importante~  mensaje.txt/  script.sh  temporal~  texto.txt

Denís@PC MINGW64 ~/prueba_git (master)
$ git status
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   texto.txt

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        .gitignore
        Hola.java
        importante~

no changes added to commit (use "git add" and/or "git commit -a")
```

Evita que Git gestione ciertos archivos.

### Añadir todo lo pendiente
```bash
Denís@PC MINGW64 ~/prueba_git (master)
$ git add .
warning: in the working copy of 'texto.txt', LF will be replaced by CRLF the next time Git touches it
warning: in the working copy of '.gitignore', LF will be replaced by CRLF the next time Git touches it
warning: in the working copy of 'Hola.java', LF will be replaced by CRLF the next time Git touches it
```

### Confirmar cambios
```bash
Denís@PC MINGW64 ~/prueba_git (master)
$ git commit -m "Añadidos fuentes en java y archivos importantes"
[master 6088a62] Añadidos fuentes en java y archivos importantes
 4 files changed, 13 insertions(+)
 create mode 100644 .gitignore
 create mode 100644 Hola.java
 create mode 100644 importante~
```

### Ver archivos en el último commit
```bash
Denís@PC MINGW64 ~/prueba_git (master)
$ git ls-tree --name-only -r HEAD
.gitignore
Hola.java
importante~
script.sh
texto.txt
```

## Tags y gestión de versiones

### Ver versión específica por hash
```bash
Denís@PC MINGW64 ~/prueba_git (master)
$ git show 1711e5d66c5f8873d8f76e3b07519b62536fa4d1
commit 1711e5d66c5f8873d8f76e3b07519b62536fa4d1
Author: denis alonso <hornet>
Date:   Thu Oct 30 10:50:15 2025 +0100

    Ampliada la explicacion del texto

diff --git a/texto.txt b/texto.txt
new file mode 100644
index 0000000..42fa975
--- /dev/null
+++ b/texto.txt
@@ -0,0 +1,4 @@
+uno
+dos
+tres
+cuatro
```

### Ver histórico resumido
```bash
Denís@PC MINGW64 ~/prueba_git (master)
$ git log --oneline
6088a62 (HEAD -> master) Añadidos fuentes en java y archivos importantes
b8988c4 Probando diff
53faf1d Añadido archivo texto.txt
edeaaee (tag: v0.7) Añadidos fuentes en java y archivos importantes
8ce6ce7 Probando diff
1711e5d Ampliada la explicacion del texto
b49767f (tag: v0.3) Confirmacion inicial
```

### Ver versión por tag
```bash
Denís@PC MINGW64 ~/prueba_git (master)
$ git show v0.3
commit b49767fe97db93b6a4bd585a78c6234ba20a6d2b (tag: v0.3)
Author: denis alonso <hornet>
Date:   Thu Oct 30 09:42:32 2025 +0100

    Confirmacion inicial

diff --git a/script.sh b/script.sh
new file mode 100644
index 0000000..273df79
--- /dev/null
+++ b/script.sh
@@ -0,0 +1,2 @@
+echo Listado completo
+ls -l
```

### Navegar a versión antigua
```bash
Denís@PC MINGW64 ~/prueba_git (master)
$ git checkout v0.3
Note: switching to 'v0.3'.

You are in 'detached HEAD' state. You can look around, make experimental
changes and commit them, and you can discard any commits you make in this
state without impacting any branches by switching back to a branch.

If you want to create a new branch to retain commits you create, you may
do so (now or later) by using -c with the switch command. Example:

  git switch -c <new-branch-name>

Or undo this operation with:

  git switch -

Turn off this advice by setting config variable advice.detachedHead to false

HEAD is now at b49767f Confirmacion inicial
```

### Volver a la versión más reciente
```bash
Denís@PC MINGW64 ~/prueba_git ((v0.3))
$ git checkout master
Previous HEAD position was b49767f Confirmacion inicial
Switched to branch 'master'
```

## Ramas

### Crear y ver ramas
```bash
Denís@PC MINGW64 ~/prueba_git (master)
$ git log --oneline
6088a62 (HEAD -> master, Prueba) Añadidos fuentes en java y archivos importantes
b8988c4 Probando diff
53faf1d Añadido archivo texto.txt
edeaaee (tag: v0.7) Añadidos fuentes en java y archivos importantes
8ce6ce7 Probando diff
1711e5d Ampliada la explicacion del texto
b49767f (tag: v0.3) Confirmacion inicial

Denís@PC MINGW64 ~/prueba_git (master)
$ git branch
  Prueba
* master
```

### Cambiar de rama
```bash
Denís@PC MINGW64 ~/prueba_git (master)
$ git switch Prueba
Switched to branch 'Prueba'

Denís@PC MINGW64 ~/prueba_git (Prueba)
$ git branch
* Prueba
  master

Denís@PC MINGW64 ~/prueba_git (Prueba)
$ git log --oneline
6088a62 (HEAD -> Prueba, master) Añadidos fuentes en java y archivos importantes
b8988c4 Probando diff
53faf1d Añadido archivo texto.txt
edeaaee (tag: v0.7) Añadidos fuentes en java y archivos importantes
8ce6ce7 Probando diff
1711e5d Ampliada la explicacion del texto
b49767f (tag: v0.3) Confirmacion inicial
```

### Ver log completo
```bash
Denís@PC MINGW64 ~/prueba_git (Prueba)
$ git log
commit 6088a625e7e3ec54c1465fe5ddcda1ea35093ea7 (HEAD -> Prueba, tag: v0.7-Ent-Release, master)
Author: Denís <denisalonsoo10@gmail.com>
Date:   Thu Oct 30 18:52:05 2025 +0100

    Añadidos fuentes en java y archivos importantes

commit b8988c467e617169915df3729a127e709760e47c
Author: Denís <denisalonsoo10@gmail.com>
Date:   Thu Oct 30 18:35:51 2025 +0100

    Probando diff

commit 53faf1d3ee3303f53991bea2085403b75f6a72cb
Author: Denís <denisalonsoo10@gmail.com>
Date:   Thu Oct 30 18:26:12 2025 +0100

    Añadido archivo texto.txt

commit edeaaee66f7387c47065c8bd338083a0e10461f3 (tag: v0.7)
Author: denis alonso <hornet>
Date:   Thu Oct 30 11:49:57 2025 +0100

    Añadidos fuentes en java y archivos importantes

commit 8ce6ce7ce594d5a005ab3e493a4591374294fdfa
Author: denis alonso <hornet>
Date:   Thu Oct 30 11:05:20 2025 +0100

    Probando diff

commit 1711e5d66c5f8873d8f76e3b07519b62536fa4d1
Author: denis alonso <hornet>
Date:   Thu Oct 30 10:50:15 2025 +0100
```

### Volver a master y ver contenido
```bash
Denís@PC MINGW64 ~/prueba_git (Prueba)
$ git switch master
M       Hola.java
Switched to branch 'master'

Denís@PC MINGW64 ~/prueba_git (master)
$ cat Hola.java
class Hola {
        public static void main(String[] args){
                System.out.println("Welcome to the Java World");
        }
}
System.out.println("I have no more branches to commit, said the Ent");
```

## Eliminar y quitar de seguimiento

### Eliminar archivos
```bash
Denís@PC MINGW64 ~/prueba_git (master)
$ git rm importante~
rm 'importante~'

Denís@PC MINGW64 ~/prueba_git (master)
$ git status
On branch master
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        deleted:    importante~

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   Hola.java
```

## Repositorios remotos

### Clonar un proyecto
```bash
Denís@PC MINGW64 ~
$ git clone https://github.com/ColegioVivasCurro/HolaED
Cloning into 'HolaED'...
remote: Enumerating objects: 20, done.
remote: Total 20 (delta 0), reused 0 (delta 0), pack-reused 20 (from 1)
Receiving objects: 100% (20/20), 4.26 KiB | 4.26 MiB/s, done.
Resolving deltas: 100% (8/8), done.

Denís@PC MINGW64 ~
$ git clone https://github.com/denisalonso10/PruebaGit
Cloning into 'PruebaGit'...
remote: Enumerating objects: 4, done.
remote: Counting objects: 100% (4/4), done.
remote: Compressing objects: 100% (3/3), done.
remote: Total 4 (delta 0), reused 0 (delta 0), pack-reused 0 (from 0)
Receiving objects: 100% (4/4), done.
```

### Enviar cambios al repositorio remoto
```bash
Denís@PC MINGW64 ~/prueba_git (master)
$ git push -u origin master
info: please complete authentication in your browser...
Enumerating objects: 26, done.
Counting objects: 100% (26/26), done.
Delta compression using up to 16 threads
Compressing objects: 100% (18/18), done.
Writing objects: 100% (26/26), 2.48 KiB | 635.00 KiB/s, done.
Total 26 (delta 3), reused 0 (delta 0), pack-reused 0 (from 0)
remote: Resolving deltas: 100% (3/3), done.
remote:
remote: Create a pull request for 'master' on GitHub by visiting:
remote:       https://github.com/denisalonso10/PruebaGit/pull/new/master
remote:
To https://github.com/denisalonso10/PruebaGit.git
 * [new branch]      master -> master
branch 'master' set up to track 'origin/master'.

Denís@PC MINGW64 ~/prueba_git (master)
$ git push
Everything up-to-date
```

### Sincronizar con el remoto
```bash
Denís@PC MINGW64 ~/prueba_git (master)
$ git pull origin master --allow-unrelated-histories
From https://github.com/denisalonso10/PruebaGit
 * branch            master     -> FETCH_HEAD
Already up to date.
```
