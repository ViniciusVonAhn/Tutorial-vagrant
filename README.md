# Tutorial de instalação Mac

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
Feito isso nós iremos utilizar o composer para criar o projeto em laravel, a ultima palavra é o nome do projeto, que nesse caso é blog
```
composer create-project --prefer-dist laravel/laravel blog
```
Agora vamos ir para a pasta do Homestead que está na home e editaremos o arquivo Homestead.yaml
```
cd ~/Homestead
```
Abra o arquivo Homestead.yaml com algum editor de texto





