# Atividade Linux Compass PB 
- Criado por: Rodrigo Pacheco de Almeida | Estagiário de DevSecOps na Compass.uol

- Objetivo: Documentar todo processo de instalação do Oracle Linux 8.6

- Download Oracle Linux versão 8.6 - https://yum.oracle.com/oracle-linux-isos.html

*A versão utilizada, apesar de não ser a última, é a mais estável no momento que foi escrito este repositório*

## Instalação
A instalação do Oracle Linux é bastante semples. Para que não ocorra nenhum problema durante o processo de instalação, irei detalhar o que deve ser feito.
Abaixo poderá ser visto cada seção da instalação e a explicação do que deve, ou não, ser feito

### *Especificação das VM's* 
*RAM: 2mb*

*HD: 40GB*

----------------------------------------------------------------------------------------------------------------------------------------------------------
### LOCALIZATION
- Keyboard: Selecionar a versão  do seu teclado
- Language Support: English
- Time & Date: Americas/Sao Paulo timezone

### USER SETTINGS
- Root Password: adicionar senha para o usuário root (caso esteja fraca é só clickar em “DONE” duas vezes)
- User Creation: Adicionar um usuário comum (pode ser criado posteriormente com o comando “adduser nome_do_usuario”) 

### SOFTWARE
- Instalation Source: a ISO já foi adicionada na máquina virtual 
- Software Selection: Minimal Install **(Sem interface gráfica)**

### SYSTEM

- Installation Destination: Existem dois tipos, “automatic” e “custom”. Para garantir que ocorra tudo certo, vamos selecionar “custom”

Custom -> DONE

*Lembrando que o espaço para cada partição deve ser escrito em MB*

Standard Partition -> /swap (4000MB) -> file system: swap

Standard Partition -> /boot (4000MB) -> file system: ext4

Standard Partition -> /home (10000MB) -> file system: ext4

LVM -> / (Vazio para pegar o restante da memória do armazenamento) -> file system: ext4

### NETWORK & HOST NAME

Nessa seção a configuração deve ser feita para que o servidor identifique um IP e conecte automaticamente quando iniciar 

- Ethernet -> ON 
- Configure -> General -> Habilitar “Connect automatically with priority” -> Save
- Host Name: Opcional (Padrão: localhost)


------------------------------------------------------------------------------------------------------------------------------------------------------------
Por fim, é só clickar em “BEGIN INSTALLATION” para começar a instalação com todas as customizações feitas. 

## Terminal Linux

Agora que o Oracle Linux foi devidamente instalado, algumas alterações precisam ser feitas para que o funcionamento ocorra bem!

- Digite o comando "sudo yum update" para que o kernel do linux esteja totalmente atualizado



