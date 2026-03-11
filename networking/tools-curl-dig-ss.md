## curl
* curl faz requisições para URLs. É o jeito mais rápido de testar uma API/serviço sem navegador.
* Testa HTTP/HTTPS (camada aplicação)
* Comandos mais usuais :
```bash
#Ver só headers(rápido)
curl -I https://example.com

#Modo "verbosa"(debug de conexão)
curl -v https://example.com

#GET retornando body
curl https://example.com

#GET com JSON
curl -H "Accept: application/json" https://api.exemplo.com/users

#POST JSON(muito usado em testes de API)
curl -X POST https://api.exemplo.com/login \
  -H "Content-Type: application/json" \
  -d '{"email":"a@a.com","password":"123"}'
```
## dig
* dig responde: "esse dominio resolve? para qual IP? "
* Se o DNS não resolve, HTTP nem começa
* Testa DNS (resolução de nomes)
* Comandos mais usuais :
```bash
#Achar IP rapidamente
dig example.com +short
#Ver detalhes (resposta completa)
dig example.com
#Consultar um DNS específico
dig example.com @8.8.8.8 +short
```
## ss
* ss mostra conexões e sockets.
* Testa sockets/portas no Linux (camada do sistema: quem está "escutando" e em que porta)
* Comandos mais usuais :
    - -l listening (escutando)
    - -n não resolver nomes (mais rapido, mostra números)
    - -t TCP
    - -p mostra o processo (precisa sudo para ver tudo)
```bash
#Ver portas TCP escutando + processo 
sudo ss -lntp
#Filtrar uma porta 
sudo ss -lntp | grep ':8000'
#Ver UDP escutando
sudo ss -lnup
#Ver conexões estabelicidas
ss -tn estabilished | head
```