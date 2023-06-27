# Ansible

### Comandos Ad-Hoc

1. Execute o comando ad-hoc que faça um ping no endereço google.com.br
```bash
ansible localhost -m ping -a "data=google.com.br"

ansible localhost -m shell -a "ping -c 4 google.com.br"
```


2. Execute o comando ad-hoc que visualize o tempo que a máquina está ligada
```bash
ansible localhost -m command -a "uptime"

ansible localhost -m shell -a "uptime"
```


3. Execute o comando ad-hoc que faça a instalação do pacote neofetch 
```bash
ansible localhost -m apt -a "name=neofetch state=present"

ansible localhost -m yum -a "name=neofetch state=present"

ansible localhost -m package -a "name=neofetch state=present"
```


4. Execute o comando ad-hoc que faça a remoção do pacote neofetch
```bash
ansible localhost -m apt -a "name=neofetch state=absent"

ansible localhost -m yum -a "name=neofetch state=absent"

ansible localhost -m package -a "name=neofetch state=absent"
```


5. Execute o comando ad-hoc que adicione um usuário
```bash
ansible localhost -m user -a "name=tux password=4linux createhome=yes"
```


### Playbooks

#### Realize os mesmos desafios anteriores, mas agora criando playbooks

1. Crie uma playbook que faça um ping no endereço google.com.br

Crie o arquivo **ping-google.yml**

```bash
---
- name: Ping google.com.br
  hosts: localhost
  tasks:
    - name: Ping google.com.br
      shell: ping -c 4 google.com.br
      register: saida_comando
    - name: Exibe a saida
      debug: 
        var: saida_comando
```


2. Crie uma playbook que visualize o tempo que a máquina está ligada

Crie o arquivo **verificar-tempo.yml**

```bash
---
- name: Verificar tempo de atividade
  hosts: localhost
  tasks:
  - name: Obter tempo de atividade
    command: uptime
    register: saida_comando

  - name: Exibe a saida
    debug: 
      var: saida_comando
```


3. Crie uma playbook que faça a instalação do pacote neofetch 

Crie o arquivo **instalar-neofetch.yml**

```bash
---
- name: Instalar o pacote neofetch
  hosts: localhost
  tasks:
  - name: Atualizar cache de pacotes
    apt:
      update_cache: yes
  - name: Instalar o pacote neofetch
    apt:
      name: neofetch
      state: present
```


4. Crie uma playbook que faça a remoção do pacote neofetch

Crie o arquivo **remover-neofetch.yml**

```bash
---
- name: Remover pacote neofetch
  hosts: localhost
  tasks:
  - name: Remover o pacote neofetch
    package:
      name: neofetch
      state: absent
```


5. Crie uma playbook que que adicione um usuário

Crie o arquivo **adicionar-usuario.yml**

```bash
---
- name: Adicionar usuário
  hosts: localhost
  tasks:
  - name: Adicionar usuario devops
    user: 
      name: devops 
      state: present 
      shell: /bin/bash 
      createhome: yes
      password: "12345"
    register: saida_comando
  - name: Exibe a saida
    debug: 
      var: saida_comando
```


### Documentações dos módulos:

#### ping
https://docs.ansible.com/ansible/2.9/modules/ping_module.html#ping-module

#### shell
https://docs.ansible.com/ansible/2.9/modules/shell_module.html#shell-module

#### command
https://docs.ansible.com/ansible/2.9/modules/command_module.html#command-module

#### apt
https://docs.ansible.com/ansible/2.9/modules/apt_module.html#apt-module

### yum
https://docs.ansible.com/ansible/2.9/modules/yum_module.html#yum-module

### package
https://docs.ansible.com/ansible/2.9/modules/package_module.html#package-module

### user
https://docs.ansible.com/ansible/2.9/modules/user_module.html#user-module

### debug
https://docs.ansible.com/ansible/2.9/modules/debug_module.html#debug-module