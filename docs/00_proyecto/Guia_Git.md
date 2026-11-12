# Guía de Git para el equipo (repositorio `samed`)

Versión: v1 · 2026-11-12 · Para Juan, Germán, Neyls y Terry

## 1. Una sola vez
1. Cuenta de GitHub y aceptar la invitación al repo `samed`.
2. Instalar git y configurar identidad (la misma que está en CODEOWNERS):
   `git config --global user.name "Tu Nombre"` y `git config --global user.email "tu-correo-de-github"`
3. Crear clave SSH: `ssh-keygen -t ed25519 -C "tu-correo"`; copiar el contenido de `~/.ssh/id_ed25519.pub` en GitHub → Settings → SSH keys. La clave privada (sin .pub) no se comparte nunca por chat ni OneDrive.
4. Clonar fuera de OneDrive: `git clone git@github.com:<org>/samed.git C:\dev\samed`

## 2. Cada tarea
1. `git checkout develop && git pull`
2. `git checkout -b feat/RF-004-prescripcion` (tipos: feat, fix, docs, test; con el ID)
3. Trabaja con tu agente; ejecuta las pruebas.
4. `git add <archivos>` y `git commit -m "feat(api): crear prescripción [RF-004][RSK-003]"`
5. `git push -u origin feat/RF-004-prescripcion`
6. En GitHub abre un Pull Request hacia `develop` llenando la plantilla. Otra persona revisa; Terry fusiona.
Nunca hagas push directo a `main` ni a `develop`. Nunca subas `.env`, contraseñas ni tokens.

## 3. Cuando alguien sube el trabajo de otro (acordado por el equipo)
Se hace solo para destrabar, con autoría visible:
- Quien escribió el contenido figura como autor y quien lo subió lo declara:
  `git commit --author="Juan <correo-de-juan>" -m "feat(web): ... [RF-004]" -m "Subido por Terry a pedido de Juan"`
- Si el trabajo es conjunto: añade la línea `Co-authored-by: Juan <correo-de-juan>` al final del mensaje.
- Usa la clave de otra persona solo con su permiso, en tu máquina, y solo en su rama `feat/*`. Cada uno debe poder explicar lo que figura a su nombre (defensa individual).
- Registra en `docs/14_errores_lecciones/` cuántos commits se subieron así y por qué, para ser transparentes en el informe.
- Al terminar la etapa, cada dueño elimina esa clave de GitHub y crea otra.

## 4. Si algo sale mal
- Conflicto al fusionar: no borres nada; avisa a Terry. Es material para la evidencia del conflicto controlado (Etapa 4).
- Subiste un secreto: avisa de inmediato; hay que cambiarlo, no solo borrarlo del commit.
