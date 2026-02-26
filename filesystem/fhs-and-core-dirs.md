# Título do assunto
Hierarquia dos diretórios (não está na ordem de importancia)
## Objetivo

- " / " : Pasta raiz, deve conter o minimo para boot e reparo.
- " /etc " : Configuração do sistema e dos serviços, especifica daquele host.
- " /var " : Dados variáveis (logs, spool, cache, estado de apps).
- " /var/log " : Logs (auth, syslog, serviços).
- " /home" : Pastas dos usuários (Documentos, configs do usuário). É "seu espaço".
- " /tmp " : Diretório para armazenamento de arquivos temporários criado por programas. Geralmente são excluidos sempre que o sistema é reiniciado.
- " /proc " : interface para dados internos do kernels/initramfs.
- " /usr " : Onde fica a maior parte dos programs e bibliotecas do sistema.  
-  /usr/bin " : Contém arquivos de programas (binários) do sistema.
- " /run " : Dados de runtime (PID files, sockets etc.) relevantes para processos rodando agora.

## Conceito
FHS ( Filesytem Hierarchy Standard) é um guia padrão que visa organizar as pastas do linux,
ficando previsivel saber onde encontrar o que precisa.

- config ( /etc )
- logs e dados que mudar ( /var )
- arquivos e usuários ( /home )
- programas e bibliotecas ( /usr )
- dados temporários ( /tmp )
- dados de runtime ( /run )

## Comandos que eu usei

1 - Você tenta iniciar um serviço e ele falha.

```bash

sudo systemctl status <serviço> --no-pager

sudo journalctl -u <serviço> -b --no-pager | tail -n 80

ls -la /etc | grep -i <serviço>

ls -la /etc/<serviço> 2>/dev/null

ls -la /run | grep -i <serviço>

```
2 - Preciso achar logs de um serviço.

```bash

systemctl status <serviço> --no-pager

ls /var/log | grep -i <serviço>

ls -la /var/log/<serviço> 2>/dev/null

#Se não tiver nada claro va no journal

```



