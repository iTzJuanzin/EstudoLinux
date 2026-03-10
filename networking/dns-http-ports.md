# dns, http e portas (básico)

### DNS (Domain Name System)
* DNS serve para usar nomes fáceis (domínios) em vez de decorar o IP.
* O que acontece quando acessa um site :
    - Seu PC resolve o domínio via DNS (pega um IP).
    - Seu PC abre conexão com esse IP (em uma porta específica, ex.: 443).
    - Depois disso, começa o HTTP/HTTPS.

```bash
# resolve domínio (mostra IP)
dig example.com +short

# resolve usando o "resolver" do sistema
getent hosts example.com

# ver DNS configurado
cat /etc/resolv.conf
```
### HTTP (Hypertext Transfer Protocol)
* É um protocolo de aplicação em que o cliente envia uma requisição e o servidor devolver uma resposta. Isso inclui métodos (GET/POST/PUT/DELETE), status codes (200/404/500), headers e corpo.
* Porta do padrão do HTTP e HTTPS
    - "http" é associado à porta 80 no registro da IANA
    - Para HTTPS (HTTP sobre TLS), a porta padrão é 443

```bash
curl -I http://example.com
curl -v https://example.com
```
* -I pega só headers
* -v mostra detalhes da conexão (muito útil para entender o fluxo)

### Ports (portas)
* Uma porta é um número (0 a 65535) usado para "multiplexar" serviços do mesmo IP:
    - IP identica a máquina (ou interface)
    - porta identifica o serviço dentro daquela máquina (web, ssh, banco, etc.)
* Faixas de portas(padrão IANA/RFC)
    - 0-1023: System /Well-known ports 
    - 1024-49151: User /Registered ports 
    - 49152-65535: Dynamic /Private (Ephemeral/ Porta Temporária) ports (muito usadas como "porta de saída" do cliente) 

