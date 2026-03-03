# Processos, sinais e controle de tarefas do terminal

## 1. Processes (processos)

* Um processo é um programa em execução(uma instância rodando). Cada processo tem um número chamada PID (Process ID).
* Comandos mais usados:
    - ps aux | grep python (ps aux mostra processos de todos os usúarios. Grep filtra.)
    - pgrep -a python (pgrep retorna PID(s). -a mostra a linhas de comando junto. Ajuda a encontrar o PID pelo nome. )

## 2. Signals (sinais)

* Um signal é uma mensagem/comando que você manda para um processo (pelo kernel) para pedir uma ação.
* Para "parar um programa" no Linux geralmente signfica mandar um signal.
* SIGTERM (15) "encerre educamente".
* SIGKILL (9) "encerre agora".
* SIGHINT (2) Quando você da Ctrl + C no terminal, envia SIGHINT para o processo em foreground.
* SIGHUP (1) "recarregue" muitos serviços interpretam como "recarregar configuração.
* SIGSTOP / SIGCONT - pausar/continuar (STOP para, CONT continua.)
* Comandos mais usado:
    - SIGTERM (15) "encerre educamente", SIGKILL (9) "encerre agora"
    - kill <PID> (por padrão envia SIGTERM (15))
    - kill -9 <PID> (O kernel mata direto, use quando o processo travar ou não responde ao SIGTERM).
    - kill -HUP <PID> "recarregue"
    - kill -STOP <PID> "para"
    - kill -CONT <PID> "continua"
    - pkill -KILL nome_processo 

## 3. Jobs (controle de tarefas do terminal)

* Um job é um processo (ou pipeline)  que está sendo controlado pela sessão do seu shell naquele terminal. 
* Os jobs são usados quando quer rodar algo no terminal demorado e sem "travar", pausar um comando e voltar depois, mandar pra background.
* exemplo prático: 
```bash
sleep 1000 #Ctrl + z (pausa)
jobs
bg nome_job
jobs
fg nome_job

