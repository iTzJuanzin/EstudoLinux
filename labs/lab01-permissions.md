# Objetivo

* Simular um “Permission denied” e resolver.

* Passos

```Bash

mkdir -p ~/lab-perms
cd ~/lab-perms

echo "segredo" > segredo.txt
chmod 600 segredo.txt
ls -l segredo.txt
```

* Agora tente “simular” acesso de outro usuário:

   - Se você tiver um usuário de teste (recomendado):

```Bash

    sudo adduser testeuser
    sudo -u testeuser cat ~/lab-perms/segredo.txt
```

Vai dar erro (esperado).

* Correção (exemplo)

```Bash

chmod 644 segredo.txt
sudo -u testeuser cat ~/lab-perms/segredo.txt
```


