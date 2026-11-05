🚀 Pré-requisitos

Docker
👉 https://www.docker.com/

Github - Página Oficial Subsistema macOS
👉 https://github.com/sickcodes/Docker-OSX

👉 wsl 2

🔎 Versão e Build do Windows
winver

⚙️ COMANDOS

🔎 Hyper-V e Subsistema do Windows para Linux
Ativar ou Desativar Recursos do Windows - 
Selecione o Hyper-V e o WSL para ativar. Caso não apareçam as opções, insira o comando abaixo:
bcdedit /set hypervisorlaunchtype on

💻  Lista Distros Disponíveis para Instalação
wsl --list --online 

💻  Instalação da Distro Ubuntu (Pode haver uma distro específica)
wsl --install Ubuntu
ou
wsl --install -d Ubuntu

💻 Atualiza os Repositórios do Ubuntu
sudo apt update

💻 Atualiza do Ubuntu
 sudo apt upgrade

💻 Requisitos para instalação do macOS

sudo apt install x11-apps -y

sudo apt -y install bridge-utils cpu-checker libvirt-clients libvirt-daemon

sudo apt install cpu-checker

💻 Verificar se o Sistema é Capaz de Virtualizar
kvm-ok

📁 Criar arquivo .wslconfig no Windows
%USERPROFILE%
Ou C:\Users\Seu usuário\.wslconfig

📁 Inserir em .wslconfig
[wsl2]
nestedVirtualization=true

📁 Instalar o docker
Abrir o docker e clicar no settings - Resources - WSL Integration - marcar o Ubuntu

💻 Abrir Subsistema Principal
wsl

💻 Lista Subsistemas Instalados
wsl --list

💻 Se tiver mais de um Wsl, pode executar o Subsistema Ubuntu
wsl -d ubuntu

💻 Ir na página do Github e escolher a versão.
Vou rodar de exemplo o Sonoma. Copie e cole o código abaixo.

docker run -it \
    --device /dev/kvm \
    -p 50922:10022 \
    -v /tmp/.X11-unix:/tmp/.X11-unix \
    -e "DISPLAY=${DISPLAY:-:0.0}" \
    -e GENERATE_UNIQUE=true \
    -e CPU='Haswell-noTSX' \
    -e CPUID_FLAGS='kvm=on,vendor=GenuineIntel,+invtsc,vmware-cpuid-freq=on' \
    -e MASTER_PLIST_URL='https://raw.githubusercontent.com/sickcodes/osx-serial-generator/master/config-custom-sonoma.plist' \
    -e SHORTNAME=sonoma \
    sickcodes/docker-osx:latest

# docker build -t docker-osx .

💻 Se quiser deixar em tela cheia 
ctrl + alt + f

💻 Se quiser deixar em tela cheia 
ctrl + alt + f



⚙️ Instalação do MACOS

🔎 Formatar o HD
selecionar o HD (Alto nível) - Clicar em Erase - Dê um novo nome - Fechar a janela
Clicar em Reinstall Mac OS ...


🔎 Hyper-V e Subsistema do Windows para Linux
Ativar ou Desativar Recursos do Windows

-----

