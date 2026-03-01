# Básico de permissões 

## O que são permissões (e por que existem)

* As permissões controlam quem pode fazer o quê com arquivos e diretórios

    - owner (usuário dono)
    - group (grupo dono)
    - others (todo mundo que não é dono e nem do grupo)

* E para cada um há três permissões básicas:

    - r (read): ler
    - w (write): escrever/alterar
    - x (execute): executar (ou "entrar", no caso de diretórios)

Saída típica:

-rw-r--r-- 1 juan dev  123 Mar  1 12:00 arquivo.txt

* Quebrando isso:

    * O primeiro caractere indica o tipo:
        - '-' arquivo normal
        - 'd' diretório
        - 'l' link simbólico

    * Depois vêm 9 caracteres em 3 blocos:
        - rw- → permissões do owner
        - r-- → permissões do group
        - r-- → permissões de others

* Então -rw-r--r-- significa:

    - dono: lê e escreve
    - grupo: só lê
    - outros: só lê

## O siginificado de r/w/x em arquivos vs diretório

* Em arquivos
    - r -> permite ler o conteúdo (cat, abrir, etc.)
    - w -> permite alterar o conteúdo (editar, sobrescrever)
    - x -> permite executar como programa/script (./script.sh)

* Em diretórios 
    - r -> permite listar nomes (dependendo do x)
    - w -> permite criar/apagar/renomear itens dentro do diretório
    - x -> permite entrar no diretório (cd) e acessar itens dentr (transversal)

## chmod, chown e chgrp (junto com comando que usei)

* chmod: mudar permissões

    1. Você usa chmod para mudar r/w/x (Modo simbólico)
        - u (user/owner), g (group), o (others), a (all)

        * exemplos:
            chmod u+x script.sh 
            chmod g-w arquivo.txt
            chmod o-r arquivo.txt 
            chmod a+r arquivo.txt

    2. Modo numérico (Bem usado em servidor)
        - r = 4, w = 2, x = 1

        - Soma:
            - 7 = rwx
            - 6 = rw
            - 5 = rx
            - 4 = r
            - 0 = ---

        * exemplos:
            - chmod 644 arquivo.txt -> rw-r--r--
            - chmod 600 segredo.txt -> rw-------
            - chmod 755 script.sh -> rwxr-xr-x
            - chmod 700 pasta_privada -> rwx------

* chown: muda dono e/ou grupo
    * exemplos:
        - sudo chown juan arquivo.txt 
        - sudo chown juan:dev arquivo.txt

* chgrp: muda só o grupo
    * exemplos :
        - sudo chgrp dev arquivo.txt 
