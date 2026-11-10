# Ambientes Vagrant com VMware Workstation

Este repositório reúne configurações do Vagrant para criar e gerenciar máquinas virtuais Linux locais com o VMware Workstation. Os exemplos servem como ambientes de laboratório e compatibilidade; cada sistema operacional tem seu próprio diretório, box e instruções de uso.

## Ambientes disponíveis

- [CentOS 7](centos/README.md): VM baseada na box `centos/7`, sem provisionamento automático.
- [Ubuntu 20.04](ubuntu/README.md): VM baseada na box `lavabit/magma-ubuntu2004`, com provisionamento que executa `apt-get update`.

Ambas as configurações usam o provider `vmware_desktop`, habilitam a interface gráfica e configuram uma rede pública em bridge. Para criar ou iniciar uma VM, entre no diretório correspondente e execute `vagrant up`; os READMEs de cada ambiente documentam os demais comandos e detalhes.

## VMware

Consulte [Setup Vagrant VMware Workstation](Setup%20Vagrant%20VMware.%20Workstation) para as notas de instalação do VMware provider e inicialização do serviço Vagrant VMware Utility no Windows.

## Observações

A rede bridge pode tornar a VM acessível por outros dispositivos na rede local. Os sistemas usados nos exemplos estão fora da manutenção de segurança padrão; consulte os avisos nos READMEs antes de usá-los e evite expor serviços em redes não confiáveis.
