Documentação do Projeto que tem como objetivo desenvolver competências práticas em DevOps e Infraestrutura como Código (IaC) utilizando as ferramentas Vagrant e Ansible.

Este projeto visa a automação da configuração de servidores virtuais utilizando Vagrant e Ansible, abordando práticas de segurança, gerenciamento de usuários e configuração de SSH.

Integrantes: Helio Vieira e Jessica Cavalcante 
Disciplina: Administração de Sistemas Abertos

_______________________________________________________________________________________________

Descrição
O Vagrantfile foi projetado para configurar um ambiente virtual utilizando o Vagrant em conjunto com o provedor VirtualBox. Ele é baseado na imagem generic/debian12 e atende aos requisitos definidos para a infraestrutura, incluindo discos adicionais, rede privada e personalização do hostname.

Configuração do Ambiente

Box: generic/debian12 – Uma imagem genérica e leve baseada no Debian 12.
- Memória: 1024 MB de RAM alocados para a máquina virtual.
- Discos Virtuais:
diskp com capacidade de 10 GB.
disks com capacidade de 10 GB.
diskt com capacidade de 10 GB.
- Rede: Configuração de rede privada com o endereço IP 192.168.57.10.
- Hostname: O hostname da máquina virtual será definido como heliojessica.

_______________________________________________________________________________________________

Playbooks Ansible

1. Playbook: update.yml
O playbook do Ansible é usado para configurar automaticamente o sistema após o provisionamento da VM. Ele atualiza o sistema, instala pacotes essenciais, configura serviços necessários e aplica ajustes personalizados. O inventário host.ini define a máquina-alvo. O objetivo é deixar a VM pronta para uso, sem necessidade de configurações manuais.

Modo de uso: comando "ansible-playbook -i host.ini update.yml"

2. Playbook 









