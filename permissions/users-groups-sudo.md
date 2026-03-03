# Users, groups e sudo

1. Users: para que serve e onde fica
    * É uma identidade do sistema usada para identificar o que é do usuario e o que é do sistema, controlando permissões de quem pode ler/escrever/executar (r,w,x).
    * Cada usuário tem um número chamado UID. O root geralmente tem UID 0.
    * O arquivo /etc/passwd guarda os atributos básicos do usuário (login, UID, GID principal, home, shell). O formato tipico é "name:passwd:uid:gid:gecos:home:shell

2. Groups: para que serve 
    * Um é um jeito de dar a mesma permissão para várias pessoas (ou para serviços), sem precisar ficar mudando permissões por usuário.
    * Grupo tambem tem um número GID.
    * Grupo primario : aquele GID que aparece no /etc/passwd
    * Grupo suplementares: grupos "extras" em que o usuário participa e que aparecem em /etc/group (e no id).

3. sudo: para que serve
    * sudo permite rodar um comand com privilégios de outro usuário (normalmente root) de forma controlada.