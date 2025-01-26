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


