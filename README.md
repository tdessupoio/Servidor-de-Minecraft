# Servidor-de-Minecraft
Este repositório documenta o passo a passo de como configurei um servidor de Minecraft do zero. Desde a escolha da versão até a configuração final, explico cada etapa para quem deseja criar seu próprio servidor de forma simples e eficiente.

Bom amigos, eu to com um tempo ocioso em casa então aproveitei para realizar um sonho que eu tinha quando criança e que vai me ajudar a concluir projetos futuros, fiz um servidor de Minecraft.
Primeiro passo foi pensar em qual maquina eu iria criar isso, por sorte eu tenho meu primeiro notebook, uma verdadeira bomba, Ram: 1GB, Processador:, HD de 250GB. Eu tentava usar esse notebook no curso técnico mas era um verdadeiro teste de paciencia, fazendo eu preferir usar o celular mesmo.

Segundo passo era melhorar esse note de alguma forma, eu tinha um outro notebook que tinha comprado com defeito para consertar e fui ver o que eu poderia utilizar, primeiro foi a ram, peguei dois pentes de 2GB, e por sorte era o era DDR1 tambem, uma placa rede wireless porque o para o nosso servidor era bem pior. E para adiantar a parte do HD, peguei um SSD que eu tinha parado aqui e coloquei. Aproveitei e troquei a pasta termica por esta muito tempo sem trocar(papo de anos).
Liguei para ver se tudo ocorreu bem, e tudo certo!

Terceiro passo foi criar um pendrive bootavel com o sistema operacional para o server, eu prefiri usar o ubuntu server por se algo facil de instalar e configurar. Usei o Ventoy para criar esse pendrive bootavel, por se um programa que uso a bastante tempo e por prefencia pessoal, coloquei a iso dentro do pendrive e vamos para o proximo passo.

Quarto passo colocar o pendrive de instalação com pendrive e escolher a iso do ubuntu server, Hora de escolher o idioma, preferi o inglês, por muito dos comandos serem inglês e colocando em portugues vai mudar muito a arquitetura dos comandos.
![image](https://github.com/user-attachments/assets/316d8f3f-e4fe-4608-b5dc-6474344cd93a)

Configuração do teclado em portugues para nao termos problema.
![image](https://github.com/user-attachments/assets/c3648047-e703-474c-9947-740bf81bfc0a)

Instalei o ubuntu server minimalized, porque nao quero que instale recursos desnecessarios para o server, acabando deixando ele lento, lembre ele é uma bomba ksksksks
Questao da rede, coloquei no wifi mesmo e por incrivel que pareça foi bem rapido.
Ele vai te perguntar o que fazer com o disk, eu preferir formatar para ter ele so para isso, depois disso ele te expecifica as particiçoes que ele vai criar, tudo certo.
Logo apos ele pede para inserir o seu nome, nome para o server, nome de usuario e a senha. Abaixo um exemplo:
![image](https://github.com/user-attachments/assets/4d0eeba8-4e35-4903-b1c1-c5bb7175846d)

Logo após vem uma parte importante, instalar o OpenSSH Server. Porque toda a configuração vamos fazer de outro computador, para facilitar.
![image](https://github.com/user-attachments/assets/bdc50df8-e036-43a2-8be3-79f895511a28)

Não vamos instalar com nenhuma autenticidade, para instalar ja funcionando.
E agora começou a instalação!!!

Ele instalado, fiz o login e comecei a instalar o  HTOP e o BTOP, que são como se fosse o gerenciador de tarefas do Windows.
````
sudo apt install htop btop

````
Abrindo o BTOP, ele ficará assim: 

Proximo passo foi pegar o ip da maquina para conseguir acessar pelo SSH
````
ip address

````

Certo, com isso vim para o meu computador principal com o windows. Fui no CMD e fiz a conexão pelo SSH
````
ssh (usuario@ipdoserver)

````
Ele vai te perguntar se você confia, sim. Vai te pedir a senha do usuario e pronto.

Proximo passo é baixar o crafty controler( que por sinal é otimo programa, os caras fizeram algo muito bem feito)
Eu vou seguir o passo a passo que ele tem no git hub mesmo:

https://docs.craftycontrol.com/pages/getting-started/installation/linux/

Finalizando os passos, vai dar uma sequência de solicitações para você aceitar.
![image](https://github.com/user-attachments/assets/50a246ed-5017-4d44-b3a6-d0674164a23d)
![image](https://github.com/user-attachments/assets/91579dfe-73fe-4723-847a-321cda023a61)
![image](https://github.com/user-attachments/assets/d6a48883-697a-4934-8055-2ff3f3fc0f79)
![image](https://github.com/user-attachments/assets/d0515162-b11d-4db0-9864-6d28b7103e84)
(Nesse caso ele esta criando um serviço como se fosse no windowns, para não precisarmos iniciar sempre, vai iniciar sozinho)
Você vai seguir colocando os comandos que ele pede para criar o serviço

Fazemos login como esta especificado no documento:
https://docs.craftycontrol.com/pages/getting-started/access/
Colocamos o ip do server e a porta.
No meu caso foi:

````
https://192.168.0.15:8443

````
Agora esta rodando o crafty
![image](https://github.com/user-attachments/assets/3ac324a6-9d7b-4300-9441-3c5c387e46b4)

Você vai jogar esse comando no seu server ou ssh:
````
sudo cat /var/opt/minecraft/crafty/crafty-4/app/config/default-creds.txt
````
Com isso ele vai buscar qual usuario e senha foi criado para você.

![image](https://github.com/user-attachments/assets/e0010d40-f854-4da9-a05a-5b7c44974426)

Agora você vai em create new server
Server Type - Minecraft Servers
Server select - se vai ser vanila ou com Sistemas de mod
Server version - a versão do Minecraft
Server name - o nome que você quer deixar no Crafty

Configura a memoria ram dependendo do seu server
Agora ele vai baixar as informações do servidor da microsoft / mojang

![image](https://github.com/user-attachments/assets/5407af63-4926-4051-8cfc-ecb7a723fc5c)
ja podemos estartar o nosso servidor
Caso aparece algum erro de Java, aconselho fazer a instalação do Java 21 no server:

````
sudo apt install openjdk-21-jdk
````
Após o carregando do crafty, é apenas entrar no seu servidor com o ip do server e correr para o abraço kkk

Consideração se quiser que rode jogadores com o Minecraft pirata, é necessario ir em files e trocar uma configuração do server:
![image](https://github.com/user-attachments/assets/23115fe9-19a4-4369-b5ac-d3cd8265c6ab)
Se deixar True so funcionar Minecraft original.
(lembrando no false, se alguem entrar com o mesmo nome de algum usuario, ele vai ficar com os itens do usuario, precisará colocar algum plugin de autenticação para reverter essa parte)


Beleza, seu server ja ta funcionando em modo local. Eu quero abrir de forma Não local, o que fazer? 
Ai ja engrossa mais o angu.

Primeira opção:
Vai no site meuip: https://meuip.com.br/
E vai nas configurações do seu roteador, Public IPv4 Address para verificar a Wan
Se estiver o mesmo IP, você consegue apenas abrir uma porta para o seu servidor e show de bola. Porque esta direto na sua companhia de internet.
Se os ips forem diferentes, você está no CGNAT -  Carrier-grade NAT
![image](https://github.com/user-attachments/assets/88d40e00-29a9-444b-bc1a-af14a96182be)

Como podemos ver na imagem, estamos(meu caso também) em um roteador onde é dividida com outras casas e depois vamos para o acesso da internet.
Bom o que você pode fazer, é: Criar uma VPN, usar o Hamashi, Playit.gg e diversas formas, ate mesmo verificar se a companhia de internet consegue fazer a ligação direta na internet(entre nós, não vão querer kkk).
No meu caso, criei uma conta no playit.gg porque queria começar a jogar logo. 

No playit para você criar um endereço de server totalmente customizado, precisa pagar um plano. Mas eu deixei quieto e utilizei a versão de graça onde vem um endereço proprio deles.
No site é muito facil vincular, você vai fazer a instalação do plugin e jogar na pasta plugin do Crafty. Quando você iniciar o server, vai te dar um url para fazer seu login e configurar o caminho. 
![image](https://github.com/user-attachments/assets/b648a41e-3d1c-45ee-ad6e-e4e5d9fac383)
![image](https://github.com/user-attachments/assets/56685a79-aa7b-4ea0-b552-1b9e322c2952)

Coloca o endereço no minecraft e pronto. 

Agora você tem um servidor de minecraft!!!
