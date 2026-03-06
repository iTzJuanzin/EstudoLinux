# journalctl

### O que é journalctl ?

- O systemd-journald é o serviço que coleta os logs do sistema (kernel, serviços do system, e muitas vezes logs que antes iam para syslog).
- O journal é um banco de logs (binário) que pode ficar em :
    - /run/log/journal (tempoário)
    - /var/log/journal (persistente, se habilitado).
-journalctl é o comando para consultar esse journal com filtros.

### Parâmetros mais utilizados 
- -u NOME.service = Mostra só os logs desse serviço
- -b = Mostra logs só do boot atual (desde que ligou/reiniciou)
- -n "N" = Mostra só as ultimas N linhas.
- -f = Fica acompanhando ao vivo.
- --since / --until = Quero logs nesse periodo.
- -p = Mostra só warnings/erros pra cima
- --no-pager  = Não abre paginador. Imprime direto.

### Cheatsheet 

1. Primeiros socorros 
```bash
# logs do boot atual
sudo journalctl -b --no-pager

# erros importantes do boot atual
sudo journalctl -b -p err..alert --no-pager

# logs de um serviço
sudo journalctl -u NOME.service --no-pager

# últimas 50 linhas de um serviço
sudo journalctl -u NOME.service -n 50 --no-pager

# acompanhar ao vivo
sudo journalctl -u NOME.service -f

# logs da última hora
sudo journalctl --since "1 hour ago" --no-pager
```

2. Serviço não sobe 
```bash
systemctl status NOME.service --no-pager
sudo journalctl -u NOME.service -n 80 --no-pager
sudo journalctl -u NOME.service -b --no-pager
```
3. Descobrir boots anteriores
```bash
journalctl --list-boots
sudo journalctl -b -1 --no-pager     # boot anterior
```
