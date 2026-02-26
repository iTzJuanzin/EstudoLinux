# Básico de /proc

## O que é /proc (procfs)

* /proc é um pseudo-fylesystem ("filesystem virtual")

    - Ele não é uma pasta normal gravada no disco
    - Os "arquivos" em /proc são uma visão em tempo real de informações que o kernel mantém (processos, memória, CPU, rede, parâmetros do sistema). 
    - Ler /proc/... é como perguntart ao kernel "Qual o seu estado agora ?".

## Conceito 

/proc na prática é importante porque você precisa dele para:

1. Entender processos (o que está rodando, com quais argumentos, quais arquivos abriu)
2. Ver saúde do sistema (memória, CPU, load, uptime)
3. Investigar problemas "estranhos" (um processo travado, consumo alto, sockets/FDs demais, etc.)
4. Automatizar diagnósticos (scripts podem ler /proc sem depender de ferramentas externas)

#### Como /proc é organizado (a lógica)

PASTA COM NÚMEROS = PROCESSOS (PID)

- Tudo que é /proc/1234/ representa o processo com PID 1234.
- Dentro de /proc/<PID>/ tem "arquivos" muito úteis:
    - cmdline -> comando/argumentos com que o processo foi iniciado
    - status -> resumo(estado, memória, threads, etc.)
    - fd/ -> links para arquivos e sockets abertos pelo processo
    - environ -> variáveis de ambiente (muitas vezes precisa de sudo; cuidado com segredos)

 
## Comandos que eu usei 

1. Para ver quanto tempo o sistema está ligado

```bash

cat /proc/uptime

```
2. Load average (boa pista quando "tudo está demorando")

```bash

cat /proc/loadvg

```
