# Ambiente Ubuntu com Vagrant

Este diretório configura uma máquina virtual Ubuntu 20.04 usando o Vagrant e o VMware Workstation.

## Pré-requisitos

- Vagrant instalado no Windows.
- VMware Workstation instalado.
- Provider do Vagrant para VMware e o serviço Vagrant VMware Utility instalados e funcionando. As instruções de instalação estão em <https://developer.hashicorp.com/vagrant/downloads/vmware>.

No Windows, se o serviço da Utility não estiver iniciado, abra um terminal com privilégios adequados e execute:

```powershell
net.exe start vagrant-vmware-utility
```

## Configuração da máquina

- Box: `lavabit/magma-ubuntu2004` (Ubuntu 20.04).
- Provider: `vmware_desktop`.
- Interface gráfica do VMware habilitada (`gui = true`).
- Rede pública habilitada (`public_network`), usando uma interface de rede em bridge. O Vagrant/VMware pode solicitar que você escolha a interface do host.
- Provisionamento shell executa `apt-get update`.
- A instalação do Nginx está comentada no Vagrantfile e, portanto, não é executada.
- Sem portas encaminhadas ou pastas sincronizadas adicionais configuradas.
- Não há endereço IP fixo definido; a configuração de rede é obtida conforme a rede bridge selecionada.

## Uso

Execute os comandos abaixo neste diretório (`ubuntu`):

```powershell
# Criar/iniciar a máquina
vagrant up

# Consultar o estado
vagrant status

# Conectar via SSH
vagrant ssh

# Executar novamente o provisionamento
vagrant provision

# Desligar a máquina
vagrant halt

# Remover a máquina virtual e seus dados associados
vagrant destroy
```

O provisionamento é executado na criação da VM e pode ser repetido com `vagrant provision`. `vagrant destroy` solicita confirmação e remove a VM criada por este ambiente; os arquivos do projeto não são removidos.

## Rede e suporte do sistema

A rede `public_network` conecta a VM à rede física por bridge. Dependendo da rede, a VM pode ficar acessível a outros dispositivos nela; use essa configuração somente em uma rede confiável e não exponha serviços sem configurar o firewall e os controles de acesso necessários.

A box especificada é mantida por um publicador no Vagrant Cloud, não pela Canonical. Ubuntu 20.04 saiu da manutenção de segurança padrão em maio de 2025; atualizações estendidas podem estar disponíveis via Ubuntu Pro, mas não presuma que essa box esteja inscrita nesse serviço. Para novos ambientes, prefira uma versão Ubuntu ainda em manutenção e verifique a procedência e atualização da box.
