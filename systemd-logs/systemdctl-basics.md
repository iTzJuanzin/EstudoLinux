# O que é systemd
* systemd é o sistema de init/gerenciador de serviços mais comum em distros modernas. Ele inicia o sistema, sobe serviços e gerencia processos "de sistema". 

### Quando você usa systemctl (casos mais usuais)
*Ver se um serviço está rodando (ou por que falhou)
*Iniciar, parar, reiniciar um serviço 
*Configurar para subir no boot
*Checar quais serviços estão ativos no momento

### Comandos essenciais (o kit básico de trabalho)

1. Ver status (o comando nº 1)

```Bash

systemctl status <service> --no-pager
```

2. Iniciar / parar / reiniciar

* Quando usar cada um
    - start: o serviço está parado e você quer subir
    - stop: quer parar o serviço
    - restart: você alterou config ou quer “resetar” o serviço

```Bash

sudo systemctl start <service>
sudo systemctl stop <service>
sudo systemctl restart <service>
```
3. Recarregar configuração sem derrubar (quando suportado)

```Bash

sudo systemctl reload <service>
# E existe um meio-termo muito usado:
sudo systemctl reload-or-restart <service>
# Tradução: “se der para recarregar, recarregue; se não, reinicie”.
```
4. Habilitar para iniciar no boot
* Diferença importante
    - start/stop mexe agora
    - enable/disable mexe no comportamento no boot (persistente)

```Bash

sudo systemctl enable <service>
sudo systemctl disable <service>
#Comando útil:
systemctl is-enabled nginx
```

5. Ver se está ativo (bom pra scripts)

```Bash

systemctl is-active ssh
#Isso retorna texto e um exit code útil para automação.
```
6. Listar serviços rodando

```Bash

systemctl list-units --type=service --state=running
#Listar serviços que falharam:
systemctl --failed
```
### Como "pensar" quando um serviço falha (o fluxo padrão)

1. Status :
    - systemctl status <service> --no-pager

2. logs detalhados:
    - sudo journalctl -u <service> -n 80 --no-pager

3. corrigir config/permissão/porta e reiniciar:
    - sudo systemctl restart <service>


