# Prodigious Day #2 - Tutorial para MAC, WINDOWS e LINUX

## Tutorial de instalação Homestead Mac 

### Baixar e instalar o [virtual box](https://www.virtualbox.org/wiki/Downloads) e [vagrant](https://www.vagrantup.com)

Para verificar se o vagrant foi instalado corretamente basta utilizar o código abaixo no terminal:
```
vagrant --version
```

### Composer
```
php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
```
```
php -r "if (hash_file('sha384', 'composer-setup.php') === '48e3236262b34d30969dca3c37281b3b4bbe3221bda826ac6a9a62d6444cdb0dcd0615698a5cbe587c3f0fe57a54d8f5') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;"
```
```
php composer-setup.php
```
```
php -r "unlink('composer-setup.php');"
```
```
mv composer.phar /usr/local/bin/composer
```
#### Verificar a instalação
```
composer -V
```

### Homestead
```
vagrant box add laravel/homestead
```
Vamos verificar se funcionou, digite o comando abaixo:
```
vagrant box list
```
Deve ter aparecido algo como isso:
```
laravel/homestead   (virtualbox, 7.2.1)
```
Agora vamos para a home:
```
cd ~
```
Iremos clonar o repositório do homestead:
```
git clone https://github.com/laravel/homestead.git ~/Homestead
```
Entreremos na pasta que foi criada com o nome de Homestead:
```
cd Homestead
```
Vamos iniciar o homestead
```
bash init.sh
```
Voltaremos para a home:
```
cd ~
```
Aqui iremos gerar a chave ssh para acessar o homestead, nesse exemplo iremos deixar o nome do arquivo padrão e sem senha, então é só digitar o comando abaixo e apertar enter 4 vezes.
```
ssh-keygen -t rsa -C "seu-email@exemplo.com"
```
Seu terminal deve ter mostrado algo parecido com o exemplo abaixo
```
Your identification has been saved in /Users/seu-username/.ssh/id_rsa.
Your public key has been saved in /Users/seu-usermame/.ssh/id_rsa.pub.
The key fingerprint is:
SHA256:YyMboVNV7XR1ED99wNFEJQJlTpDvGIA4b07KAKrdtGs seu-email@exemplo.com
The key's randomart image is:
+---[RSA 2048]----+
|     . ...+*=.*OB|
|.   o ... .+o.o++|
|..   oo  . +.. .+|
|. . .o+.  . o   o|
|.. =o*o S  +     |
|. . =..= o. .    |
|     ..          |
|    E            |
|   .             |
+----[SHA256]-----+
```
Bom, agora iremos criar uma pasta dentro de Documentos, você pode pode colocar qualquer nome, nesse exemplo o nome da pasta será dev.
Agora vamos entrar dentro da pasta dev
```
cd ~/Documents/dev
```
Feito isso nós iremos utilizar o composer para criar o projeto com laravel, a ultima palavra é o nome do projeto, que nesse caso é blog
```
composer create-project --prefer-dist laravel/laravel blog
```
Agora vamos ir para a pasta do Homestead que está na home e editaremos o arquivo Homestead.yaml
```
cd ~/Homestead
```
Abra o arquivo Homestead.yaml com algum editor de texto. 
Vamos editar os folders, não podemos esquecer que lá em documentos nós criamos uma pasta chamada dev e é dentro dela que está o nosso projeto e como o projeto que nós criamos tem o nome blog, o nosso folder ficaria assim:
```
folders:
    - map: ~/Documents/dev # Mapeando onde o projeto se encontra
      to: /home/vagrant/blog # Mapeando para onde iremos enviar o projeto dentro do Homestead
```
Agora iremos editar a parte de sites:
```
sites:
    - map: blog.code # endereço que iremos utilizar para acessar a nossa aplicação através do navegador
      to: /home/vagrant/blog/public # em folders nós colocamos o endereço e aqui nós estamos informando que o nosso index.php está dentro da pasta public
```
Para não precisarmos sempre ir até a pasta do homestead para executar os comandos, vamos fazer um simples configuracão, mas para isso precisamos ir na pasta do Homestead pela ultima vez, pois depois disso você pode executar comandos como homestead up ou homestead ssh de qualquer lugar do seu sistema.
```
cd ~/Homestead
```
Agora que estamos dentro da pasta, vamos executar o comando abaixo
```
function homestead() {
    ( cd ~/Homestead && vagrant $* )
}
```
Pronto, agora não precisamos mais voltar aqui e sempre que formos utilizar um comando, não mais usaremos o vagrant e sim o homestead.
Estamos quase terminando, como nós alteramos o arquivo Homestead.yaml precisamos fazer um reload do Homestead.

```
homestead up
```
Então para finalizarmos, precisamos editar o arquivo hosts do nosso sistema para informar que blog.dev é uma url local, para fazer isso é só abrir o arquivo hosts que fica na pasta etc. Não podemos esquecer que o ip e o endereço(é o "-map" que defimos em "sites:") tem que ser o mesmo que está no arquivo Homestead.yaml. Ao abrir esse arquivo nós vamos adicionar mais uma linha com o conteúdo abaixo: 
```
192.168.10.10	blog.code
```
Pronto, agora você já pode abrir o seu navegador e acessar a url blog.dev
### Informações adicionais
Para desligar o servidor é só utilizar o comando:
```
homestead halt
```
Para inicar:
```
homestead up
```
Para entrar na maquina virtual:
```
homestead ssh
```
Em caso de alteração do arquivo Homestead.yaml:
```
homestead reload --provision
```
Visualizar o status das maquinas:
```
homestead global -status
```

# Tutorial de instalação Homestead Windows

### Baixar e instalar o [virtual box](https://www.virtualbox.org/wiki/Downloads) e [vagrant](https://www.vagrantup.com)

Para verificar se o vagrant foi instalado corretamente basta utilizar o código abaixo no terminal:
```
vagrant --version
```
### Baixar e instalar o [composer](https://getcomposer.org/download/)
#### Verificar a instalação
reinicie o terminal e execute o comando abaixo:
```
composer -V
```

### Homestead
```
vagrant box add laravel/homestead
```
Vamos verificar se funcionou, digite o comando abaixo:
```
vagrant box list
```
Deve ter aparecido algo como isso:
```
laravel/homestead   (virtualbox, 7.2.1)
```
Fazer o download do [git](https://git-scm.com/downloads)

Verficar se o git foi instalado corretamente
```
git --version
```
Agora vamos para a home
```
cd C:\
```
Iremos clonar o repositório do homestead:
```
git clone https://github.com/laravel/homestead.git /Homestead
```
Entreremos na pasta que foi criada com o nome de Homestead:
```
cd Homestead
```
Vamos iniciar o homestead
```
init.bat
```
Voltaremos para a home:
```
cd C:\
```
Aqui iremos gerar a chave ssh para acessar o homestead, nesse exemplo iremos deixar o nome do arquivo padrão e sem senha, então é só digitar o comando abaixo e apertar enter 4 vezes.
```
ssh-keygen -t rsa -C "seu-email@exemplo.com"
```
Seu terminal deve ter mostrado algo parecido com o exemplo abaixo
```
Your identification has been saved in /Users/seu-username/.ssh/id_rsa.
Your public key has been saved in /Users/seu-usermame/.ssh/id_rsa.pub.
The key fingerprint is:
SHA256:YyMboVNV7XR1ED99wNFEJQJlTpDvGIA4b07KAKrdtGs seu-email@exemplo.com
The key's randomart image is:
+---[RSA 2048]----+
|     . ...+*=.*OB|
|.   o ... .+o.o++|
|..   oo  . +.. .+|
|. . .o+.  . o   o|
|.. =o*o S  +     |
|. . =..= o. .    |
|     ..          |
|    E            |
|   .             |
+----[SHA256]-----+
```
Bom, agora iremos criar uma pasta dentro de Documentos, você pode pode colocar qualquer nome, nesse exemplo o nome da pasta será dev.
Agora vamos entrar dentro da pasta dev
```
cd C:\Users\%username%\Documents\dev
```
Feito isso nós iremos utilizar o composer para criar o projeto com laravel, a ultima palavra é o nome do projeto, que nesse caso é blog
```
composer create-project --prefer-dist laravel/laravel blog
```
Agora vamos ir para a pasta do Homestead que está na home e editaremos o arquivo Homestead.yaml, se você tiver somente o arquivo Homestead.yaml.example não tem problema, pode usar ele, mas terá que renomear para Homestead.yaml
```
cd C:\Homestead
```
Abra o arquivo Homestead.yaml com algum editor de texto. 
Vamos editar os folders, não podemos esquecer que lá em documentos nós criamos uma pasta chamada dev e é dentro dela que está o nosso projeto e como o projeto que nós criamos tem o nome blog, o nosso folder ficaria assim:
```
folders:
    - map: ~/Documents/dev/blog # Mapeando onde o projeto se encontra
      to: /home/vagrant/blog # Mapeando para onde iremos enviar o projeto dentro do Homestead
```
Agora iremos editar a parte de sites:
```
sites:
    - map: blog.code # endereço que iremos utilizar para acessar a nossa aplicação através do navegador
      to: /home/vagrant/blog/public # em folders nós colocamos o endereço e aqui nós estamos informando que o nosso index.php está dentro da pasta public
```
Estamos quase terminando, como nós alteramos o arquivo Homestead.yaml precisamos fazer um reload do Homestead, para isso precisar ir na pasta do homestead
```
cd C:\Homestead
```
Agora vamos executar o comando para iniciar
```
vagrant up 
```
Então para finalizarmos, precisamos editar o arquivo hosts do nosso sistema para informar que blog.dev é uma url local, para fazer isso é só abrir o bloco de notas em modo administrador e depois vamos em aquivo -> abrir.. e procuramos o endereço C:\Windows\System32\drivers\etc\hosts ao abrir, na parte de localhost name,  a gente adiciona a linha abaixo que é referente ao ip e endereço que configuramos no homestead.yaml, Não podemos esquecer que o ip e o endereço(é o "-map" que defimos em "sites:")
```
192.168.10.10 blog.code
```
Pronto, agora você já pode abrir o seu navegador e acessar a url blog.dev

### Informações adicionais, sempre dentro da pasta do Homestead
Para desligar o servidor é só utilizar o comando:
```
homestead halt
```
Para inicar:
```
vagrant up
```
Para entrar na maquina virtual:
```
vagrant ssh
```
Em caso de alteração do arquivo Homestead.yaml:
```
vagrant reload --provision
```
Visualizar o status das maquinas:
```
vagrant global -status
```




