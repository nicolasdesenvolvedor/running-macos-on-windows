⚙️ Pré-requisitos
- Download e Instalação do Oracle VM em: https://www.oracle.com/br/virtualization/technologies/vm/downloads/virtualbox-downloads.html
- Download e instalação do Oracle VM VirtualBox Extension Pack em: https://www.oracle.com/br/virtualization/technologies/vm/downloads/virtualbox-downloads.html#extpack
- Download Imagem OSX em https://olarila.com/topic/20143-macos-monterey-iso-for-virtual-machine/
	ou download direto do MCOSX Sequoia 15.2 (https://www.mediafire.com/file/cr0oo2h2iuky8gz/Install+macOS+Monterey+12.7.4_21H1123.iso/file)

⚙️ COMANDOS UTILIZADOS

🔎 Criar nova máquina virtual (VM)

-clicar em novo
-definir um <NOME_VM> para a máquina virtual
-tipo: Mac OS X
-versão: MacOS X (64-bit)
-Mémória base: 6144 mb
-Selecione 4 cores de processador
-Deixar marcado o Habilitar |EFI
-O HD pode ter 120 GB (Não marcar pré alocar, pois assim será assumido o padrão dinamicamente alocado)


🔎 Configurar Rede
Selecione a VM e clique em configurações
-Em Sistema, desmarque o boot via disket
-Em Monitor, aponte para 128 mb de mémória de vídeo
-Em Rede, selecione o modo NAT para isolar sua VM a localhost ou selecione o modo bridge se quiser identificar seu OS como uma nova máquina na rede.

💻  Configurações Pré-Instalação
-Mude <VM Name> para o <NOME_VM> inicialmente definido
-De acordo com o processador, abra o CMD em modo admnistrador e execute os comandos abaixo de acordo com a plataforma do seu processador (intel ou amd)
Dica: pós comando cd, pode ser copiado e colado todos os comandos de uma única vez.

# Intel Processor

cd "C:\Program Files\Oracle\VirtualBox\"
VBoxManage.exe modifyvm "VM Name" --cpuidset 00000001 000106e5 00100800 0098e3fd bfebfbff
VBoxManage setextradata "VM Name" "VBoxInternal/Devices/efi/0/Config/DmiSystemProduct" "iMac19,3"
VBoxManage setextradata "VM Name" "VBoxInternal/Devices/efi/0/Config/DmiSystemVersion" "1.0"
VBoxManage setextradata "VM Name" "VBoxInternal/Devices/efi/0/Config/DmiBoardProduct" "Iloveapple"
VBoxManage setextradata "VM Name" "VBoxInternal/Devices/smc/0/Config/DeviceKey" "ourhardworkbythesewordsguardedpleasedontsteal(c)AppleComputerInc"
VBoxManage setextradata "VM Name" "VBoxInternal/Devices/smc/0/Config/GetKeyFromRealSMC" 0
VBoxManage setextradata "VM Name" "VBoxInternal/TM/TSCMode" "RealTSCOffset"

# AMD Processor

cd "C:\Program Files\Oracle\VirtualBox\"
VBoxManage.exe modifyvm "VM Name" --cpuidset 00000001 000106e5 00100800 0098e3fd bfebfbff
VBoxManage setextradata "VM Name" "VBoxInternal/Devices/efi/0/Config/DmiSystemProduct" "iMac19,3"
VBoxManage setextradata "VM Name" "VBoxInternal/Devices/efi/0/Config/DmiSystemVersion" "1.0"
VBoxManage setextradata "VM Name" "VBoxInternal/Devices/efi/0/Config/DmiBoardProduct" "Iloveapple"
VBoxManage setextradata "VM Name" "VBoxInternal/Devices/smc/0/Config/DeviceKey" "ourhardworkbythesewordsguardedpleasedontsteal(c)AppleComputerInc"
VBoxManage setextradata "VM Name" "VBoxInternal/Devices/smc/0/Config/GetKeyFromRealSMC" 0
VBoxManage modifyvm "VM Name" --cpu-profile "Intel Core i7-6700K"
VBoxManage setextradata "VM Name" "VBoxInternal/TM/TSCMode" "RealTSCOffset"

💻  Execute a Máquina Virtual apontando o boot para a Imagem da VM baixada
Obs: Caso o seu PC apresente o problema VERR_INVALID_HANDLE, precisaremos desabilitar o Windows Hyper-V e a Verificação de Integridade de Memória.

Verificação de Integridade de Memória: Procure por Isolamento de Núcleo (Core Isolation) e desligue a funcionalidade.
Windows Hyper-V: abra o cmd como modo adm e insira o comando: bcdedit /set hypervisorlaunchtype off

Atenção!!!
Após este comando é necessário realizar o restart da máquina

Se ainda assim o erro persistir, então rode o comando
VBoxManage setextradata "MAC OS X Sonoma" "VBoxInternal/Devices/smc/0/Config/GetKeyFromRealSMC" 0

💻  Configuração do Sistema Operacional
-Selecione a language
-Selecione Utilitário de Disco
-Selecione a primeira media e após a seleção clique em apagar, definindo qualquer nome para a nova listagem de disco
-Feche o utilitário de disco
-Selecione Instalação do macOS Sonoma/Monterey/etc...
-Após os nexts, aguarde a instalação

📁 O Usuário não precisa ter um id apple no processo
-Selecione Configurar Mais Tarde
-O tempo de uso solicitado durante a instalação segue o mesmo princípio
-Desative pedir a Siri

⚙️ Parabéns. SO instalado com sucesso

💻  Caso queira mudar a resolução do vídeo e a quantidade de memória utilizada, visto que a resolução padrão vem como 1024 X 768
------------- Desligue o sistema operacional e execute os comandos abaixo ----------------
------------- Para tela cheia selecione a mesma resolução de tela do seu windows (Identificado em Sistema - Tela - Resolução de Tela) ----------------
cd "C:\Program Files\Oracle\VirtualBox\"
VBoxManage setextradata "VM Name" VBoxInternal2/EfiGraphicsResolution 1920x1080

Choose a Resolution:
  1280x720 | 1920x1080 | 2560x1440 | 2048x1080 | 3840x2160
    HD         FHD          QHD         2K          4K

VBoxManage modifyvm "VM Name" --vram 256