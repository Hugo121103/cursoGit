# Cursito de Git – Flujo básico con ramas, push/pull, merge y stash

## Objetivo
- Aprender a crear y cambiar de ramas.
- Hacer `add`, `commit`, `push`, `pull`.
- Practicar `merge` y resolver conflictos.
- Usar `git stash` para guardar cambios temporales.
- Eliminar ramas que ya no se necesiten.

## Requisitos
- Git instalado.
- Acceso al repositorio remoto (GitHub, GitLab, etc.).
- Configurar usuario:
```bash
git config --global user.name "Tu Nombre"
git config --global user.email "tu.email@dominio.com"
```
## Flujo de trabajo (por colaborador)
Cada colaborador deberá tomar en cuenta el siguiente flujo de trabajo, el cual 
puede ayudar como flijo de trabajo del día a día

### Clonar el repo:
```bash
git clone <URL_DEL_REPO>
cd git-cursito
```

### Cambiarte a tu rama (cada quien tiene su rama colabX):
```bash
git fetch
git checkout colabX
```

### Editar tu archivo colabX.txt, seguir las instrucciones internas y confirmar:

```bash
git add colabX.txt
git commit -m "ColabX: primera edición"
git push -u origin colabX
```

### Actualizarte antes de integrar:
```bash
git checkout main
git pull origin main
```

### Mezclar tu rama a main (opción A: Pull Request en la plataforma; opción B: local):

Opción A – PR (recomendado): abre Pull Request de colabX → main. Resuelve conflictos si aparecen, pide revisión y haz merge.

Opción B – Local:
```bash
git checkout main
git pull origin main
git merge --no-ff colabX
# Si hay conflictos, resuélvelos en el editor:
#   - Edita archivos marcados
#   - git add <archivos_resueltos>
#   - git commit
git push origin main
```

### Stash (cuando sea necesario):
Si estás a mitad de un cambio y necesitas cambiar de rama sin commitear:
```bash
git stash          # guarda cambios
git checkout otra-rama
# ...
git checkout colabX
git stash pop      # recupera cambios
```

### Eliminar rama local/remota (cuando ya se integró):
```bash
git branch -d colabX
git push origin --delete colabX
```

## Referencia rápida de comandos
### Estado y diferencias
git status
git diff

### Añadir y confirmar
git add .
git commit -m "mensaje"

### Sincronizar
git pull origin <rama>
git push origin <rama>

### Ramas
git branch
git checkout -b nueva-rama
git checkout rama-existente
git branch -d rama-local
git push origin --delete rama-remota

### Merge (desde main)
git checkout main
git pull origin main
git merge --no-ff <rama>
git push origin main

### Stash
git stash
git stash list
git stash pop


---

## 3) Comandos (instructor) para **crear repo, archivos y ramas**

### Ejecutar esto una sola vez para dejar todo listo. Ajusta el `origin` a tu URL.

```bash
# 0) Crear carpeta y repo
mkdir git-cursito && cd git-cursito
git init
``