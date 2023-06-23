# Desafio DevOps

## Vagrant

Escrever um Vagrantfile que configure duas máquinas virtuais utilizando as imagens do Alma Linux 8 e do Debian 12 respectivamente, estas box são definidas no site [Vagrant Cloud](https://app.vagrantup.com/boxes/search). Para cada VM deve ser criado um bloco onde será informado os comandos a serem executados, que serão descritos nas instruções. Lembre-se de manter a organização dos blocos e utilização das variáveis,  seguindo a sintaxe da linguagem Ruby. Adicione uma configuração para criar um usuário chamado "**devops**" com um diretório home e com o shell padrão "**bash**", em ambas as máquinas.

##### Instruções:

1. Crie um arquivo chamado "**Vagrantfile**".

2. Abra o arquivo em um editor de texto.

3. Utilize a estrutura de configuração do Vagrantfile para definir as duas máquinas virtuais. Lembre-se de utilizar o formato correto do Ruby para especificar a versão do Vagrant, e suas variáveis.

4. Para a primeira máquina virtual, que deverá ter o nome **AlmaLinux**, defina as seguintes configurações:
   - Utilize a imagem do **Alma Linux 8**.
   - Provisione a máquina utilizando um script shell (no mesmo bloco de configurações da VM), que realize as seguintes ações:
     - Instale o pacote do **Apache2**, utilizando o gerenciador de pacotes conforme a distribuição citada.
     - *Habilite* e *inicie* o serviço do **Apache2** com o comando para gerenciar serviços no linux.

5. Para a segunda máquina virtual, que deverá ter o nome **Debian12**, defina as seguintes configurações:
   - Utilize a imagem do **Debian 12** (codinome bookworm).
   - Provisione a máquina utilizando um script shell (no mesmo bloco de configurações da VM), que realize as seguintes ações:
     - Atualize o repositório de pacotes disponíveis, utilizando o gerenciador de pacote do sistema.
     - Instale o pacote do **Apache2**, utilizando o gerenciador de pacotes conforme a distribuição citada.

6. Adicione uma configuração global para criar um usuário chamado "**devops**" com um diretório home e com o shell padrão "**bash**". Utilize o comando responsável para criar o usuário com as opções apropriadas.

7. Salve o arquivo.

Sua tarefa é criar um novo arquivo Vagrantfile do zero*, seguindo as etapas descritas.

###### Obs: Pode ser utilizado o comando mostrado em aula, para criar uma estrutura inicial do arquivo Vagrantfile, para realizar as demais configurações.


##### Teste se o seu arquivo foi configurado com sucesso

###### Comando para validar a configuração e sintaxe:
> Certifique-se de estar no mesmo diretório que o seu arquivo Vagrantfile.
```bash
vagrant validate
```

>Saída esperada: 
>>	**Vagrantfile validated successfully.**



###### Para subir as máquinas utilizando o seu código criado:
> Certifique-se de estar no mesmo diretório que o seu arquivo Vagrantfile.

```bash
vagrant up
```
