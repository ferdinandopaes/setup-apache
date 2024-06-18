# Step by Step Apache

#### Descrição

Projeto criado para auxiliar na criação de um servidor linux com apache para o Coninma.

**Pré-requisitos**

- Ter o virtual box instalado;

**Passos**

- Acesse https://ubuntu.com/download e baixe o Ubuntu versão Server;
- Abra o virtualbox;
- Clique em Novo;
- No campo nome adicione `first-sp-app`, e no campo Imagem ISO selecione a imagem baixada. Depois de selecionar a imagem, o VirtualBox ja'identificará o tipo e versão do S.O. para `Linux` e `Ubuntu (64-bit)`. Vá para a próxima tela;
- Configure os requisitos de Hardware (2CPU e 2GB de memória) e vá para a próxima tela;
- Ajuste o disco para ao menos 30G e vá para a tela de finalização. Depois disso, finalize;
- Clique em Iniciar;
- Clique em `Try or Install Ubuntu Server`
- Selecione o idioma Português;
- Instale a versão sem atualizções `Continue without update`;
- Nos próximos passos para configuração de teclado, instalação base, configuração de rede, repositório e disco, cliquem em `Próximo`;
- Entre com os dados de perfil;
- Pule o upgrade para o Ubuntu Pro;
- Habilite o Openssh server;
- Não selecione nenhum outro pacote;
- Após a finalização da execução do script, clique em Reboot;

Após o reboot, faça o login na máquina virtual e inicie a execução do script abaixo para a instalação do serviço do apache

```
sudo apt update
sudo apt install apache2
systemctl status apache2 ou /etc/init.d/apache2 status
```

Vamos explorar os arquivos de configuração

```
sudo vim /etc/apache2/apache2.conf
sudo vim /etc/apache2/sites-available/000-default.conf
```

Vamos criar o nosso primeiro vhost. Abra o arquivo com o comando abaixo e adicione o conteúdo que está disponivel em conf/app-sp.conf

```
sudo vim /etc/apache2/sites-available/app-sp.conf
```

Agora crie o arquivo html estático que será exibido ao acessar nosso servidor apache via web. Use o conteúdo disponível em html/index.html

```
sudo vim /var/www/html/app-sp/index.html
```

Executo o restart do serviço do apache para que ele carrega as novas configurações em memória

```
sudo systemctl restart apache2
```

Parabéns, você tem um servidor apache.