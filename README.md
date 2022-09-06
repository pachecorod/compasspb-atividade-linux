# Atividade Linux Compass PB 
- Criado por: Rodrigo Pacheco de Almeida | Estagiário de DevSecOps na Compass.uol

- Objetivo: Documentar todo processo de instalação do Oracle Linux 8.6

- Download Oracle Linux versão 8.6 - https://yum.oracle.com/oracle-linux-isos.html

*A versão utilizada, apesar de não ser a última, é a mais estável no momento que foi escrito este repositório*

## Instalação
A instalação do Oracle Linux é bastante semples. Para que não ocorra nenhum problema durante o processo de instalação, irei detalhar como deve ser feito.
Abaixo poderá ser visto cada seção da instalação e a explicação do que deve, ou não, ser feito

### *Especificação das VM's* 
*RAM: 2GB*

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

### Configurar IP fixo

O primeiro passo para configurar o IP fixo é acessar o diretório **/etc/sysconfig/network-scripts** e alterar o arquivo **ifcfg-enp0s3**

- Alterar BOOTPROTO=dhcp para BOOTPROTO=none
- Adicionar os seguintes valores no arquivo:

IPADDR0=192.168.0.135 (algum IP válido na sua rede)

PREFIX0=24 (prefixo da sua rede)

GATEWAY0=192.168.0.1 (gateway da sua rede)

NETMASK=255.255.255.0 (máscara da sua rede)

DNS1=192.168.1.0

DNS2=8.8.8.8

NETWORK=192.168.0.0 (sua rede)

*Salve o arquivo e reinicie a VM (ou usar o comando "systemctl restart NetworkManager")*



