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
O playbook executa uma atualização completa do sistema operacional, garantindo que todos os pacotes estejam atualizados para as versões mais recentes, melhorando a segurança e a estabilidade da VM.
Modo de uso: comando "ansible-playbook -i host.ini update.yml"

_______________________________________________________________________________________________

2. Playbook: hostname.yml
O playbook altera o hostname do sistema e atualiza o arquivo /etc/hosts para assegurar que o novo nome seja corretamente refletido no sistema.
Modo de uso: comando "ansible-playbook -i host.ini hostname.yml"

Para verificar se o hostname foi alterado corretamente, você pode usar o comando "cat /etc/hosts" no terminal da máquina virtual.

_______________________________________________________________________________________________

3. Playbook users.yml
Este playbook cria dois usuários no sistema, um para cada integrante do grupo (helio e jessica), com base no primeiro nome de cada pessoa. A tarefa também inclui a configuração das senhas desses usuários, garantindo que eles possam acessar o sistema. 

Modo de uso: comando "ansible-playbook -i host.ini users.yml"

Para verificar a criação dos usuários você pode usar o comando: "getent passwd helio" "getent passwd jessica" 

_______________________________________________________________________________________________

4. Playbook saudacao.yml
Este playbook configura uma mensagem de saudação que será exibida automaticamente quando um usuário acessar o sistema via SSH. A mensagem informa ao usuário que o acesso é restrito a pessoas autorizadas e que a atividade está sendo monitorada.

Após a execução do playbook, ao se conectar ao sistema via SSH, a mensagem configurada será exibida no terminal. Para verificar se o arquivo foi atualizado, você pode visualizar o conteúdo do arquivo /etc/motd com o comando: "cat /etc/motd"

_______________________________________________________________________________________________

5. Playbook sudo.yml
Este playbook configura o acesso de usuários do grupo ifpb para que possam executar comandos com privilégios de root utilizando o programa sudo. Isso garante que os membros do grupo possam realizar tarefas administrativas no sistema, sem a necessidade de acesso direto à conta root.
A modificação é feita no arquivo /etc/sudoers, que gerencia as permissões de acesso e privilégios no sistema.

Passo 1: Para verificar se o grupo ifpb tem acesso ao sudo, adicione um usuário ao grupo ifpb ou utilize um existente com o comando: "sudo usermod -aG ifpb nome_do_usuario"
Passo 2: Faça login com o usuário do grupo ifpb e execute um comando com sudo para verificar o acesso: "sudo ls /root"

_______________________________________________________________________________________________

6. Playbook ssh.yml

Este playbook configura o serviço SSH para aumentar a segurança do sistema, desabilitando o login do usuário root, permitindo apenas autenticação por chave pública e restringindo o acesso ao SSH para usuários de um grupo específico.

Para rodar este playbook, use o comando: "ansible-playbook -i hosts.ini ssh.yml"
Para testar a configuração, acesse a máquina virtual via SSH com o comando: "ssh -i /home/helio/.ssh/id_rsa helio@192.168.57.10"

_______________________________________________________________________________________________

7. Playbook lvm.yml
Este playbook configura o LVM (Logical Volume Manager) para gerenciar os três discos de 10 GB, criando um Volume Group e Logical Volume para armazenamento, além de formatar e configurar a partição para ser montada automaticamente.

Para rodar este playbook, use o comando: "ansible-playbook -i hosts.ini lvm.yml"
Após executar o playbook, verifique as configurações com os seguintes comandos: 
Checar volumes físicos e grupamentos: "pvs" "vgs" "lvs"
Mostrar os dispositivos e pontos de montagem: "lsblk"

_______________________________________________________________________________________________


