# Ambiente CentOS com Vagrant

Este diretório configura uma máquina virtual CentOS 7 usando o Vagrant e o VMware Workstation.

## Pré-requisitos

- Vagrant instalado no Windows.
- VMware Workstation instalado.
- Provider do Vagrant para VMware e o serviço Vagrant VMware Utility instalados e funcionando. As instruções de instalação estão em <https://developer.hashicorp.com/vagrant/downloads/vmware>.

No Windows, se o serviço da Utility não estiver iniciado, abra um terminal com privilégios adequados e execute:

```powershell
net.exe start vagrant-vmware-utility
```

## Configuração da máquina

- Box: `centos/7`.
- Provider: `vmware_desktop`.
- Interface gráfica do VMware habilitada (`gui = true`).
- Rede pública habilitada (`public_network`), usando uma interface de rede em bridge. O Vagrant/VMware pode solicitar que você escolha a interface do host.
- Sem provisionamento automático, portas encaminhadas ou pastas sincronizadas adicionais configuradas.
- Não há endereço IP fixo definido; a configuração de rede é obtida conforme a rede bridge selecionada.

## Uso

Execute os comandos abaixo neste diretório (`centos`):

```powershell
# Criar/iniciar a máquina
vagrant up

# Consultar o estado
vagrant status

# Conectar via SSH
vagrant ssh

# Desligar a máquina
vagrant halt

# Remover a máquina virtual e seus dados associados
vagrant destroy
```

`vagrant destroy` solicita confirmação e remove a VM criada por este ambiente. Os arquivos do projeto não são removidos.

## Rede e suporte do sistema

A rede `public_network` conecta a VM à rede física por bridge. Dependendo da rede, a VM pode ficar acessível a outros dispositivos nela; use essa configuração somente em uma rede confiável e não exponha serviços sem configurar o firewall e os controles de acesso necessários.

CentOS 7 chegou ao fim de vida em 30 de junho de 2024 e não recebe atualizações regulares de segurança. Esta box pode continuar útil para testes de compatibilidade, mas não é recomendada para novos ambientes ou serviços expostos à rede. Considere uma distribuição suportada se não precisar especificamente do CentOS 7.
