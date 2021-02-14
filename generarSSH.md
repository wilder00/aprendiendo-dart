Generar una nueva llave SSH: (Cualquier sistema operativo)
```
ssh-keygen -t rsa -b 4096 -C "youremail@example.com"
```
Comprobar proceso y agregarlo (Windows)
```
eval $(ssh-agent - s)
ssh-add ~/.ssh/id_rsa
```
Comprobar proceso y agregarlo (Mac)

eval "$(ssh-agent -s)"
¿Usas macOS Sierra 10.12.2 o superior?
Haz lo siguiente:

cd ~/.ssh
Crea un archivo config…
Con Vim vim config
Con VSCode code config
Pega la siguiente configuración en el archivo…
Host *
  AddKeysToAgent yes
  UseKeychain yes
  IdentityFile ~/.ssh/id_rsa
Agrega tu llave

ssh-add -K ~/.ssh/id_rsa
