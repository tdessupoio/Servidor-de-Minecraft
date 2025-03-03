# Servidor-de-Minecraft
Este repositório documenta o passo a passo de como configurei um servidor de Minecraft do zero. Desde a escolha da versão até a configuração final, explico cada etapa para quem deseja criar seu próprio servidor de forma simples e eficiente.
---

Bom, amigos, eu estava com um tempo ocioso em casa e resolvi realizar um sonho de infância que também vai me ajudar em projetos futuros: criei um servidor de Minecraft.

## Escolhendo a Máquina

O primeiro passo foi decidir em qual máquina rodar o servidor. Por sorte, eu tinha meu primeiro notebook, uma verdadeira bomba:

- **RAM:** 1GB

- **Processador:** ???

- **HD:** 250GB

Eu tentava usar esse notebook no curso técnico, mas era um verdadeiro teste de paciência, tanto que eu preferia usar o celular.

## Melhorando o Notebook

A segunda etapa foi tentar melhorar esse notebook de alguma forma. Eu tinha um outro laptop comprado com defeito para consertar e vi o que poderia aproveitar:

- Peguei dois pentes de **2GB de RAM DDR1.**

- Instalei uma **placa de rede wireless**, porque a original era ainda pior.

- Substituí o HD por um **SSD** que eu tinha sobrando.

- Troquei a **pasta térmica**, pois já fazia anos desde a última troca.

Depois de tudo instalado, liguei a máquina e, para minha felicidade, tudo estava funcionando bem!

## Criando um Pendrive Bootável

Para instalar o sistema operacional do servidor, criei um pendrive bootável e optei pelo **Ubuntu Server**, pois é fácil de instalar e configurar. Usei o **Ventoy** para criar o pendrive bootável, pois já uso esse programa há um tempo e gosto bastante.

## Instalando o Ubuntu Server

Conectei o pendrive e inicie a instalação:

1. Escolhi o **idioma** em inglês, pois a maioria dos comandos são em inglês e, em português, isso poderia mudar a estrutura dos comandos.
![image](https://github.com/user-attachments/assets/316d8f3f-e4fe-4608-b5dc-6474344cd93a)

2. Configurei o **teclado** em português para evitar problemas.
![image](https://github.com/user-attachments/assets/c3648047-e703-474c-9947-740bf81bfc0a)

3. Instalei a versão **minimalista** do Ubuntu Server para evitar programas desnecessários e manter o sistema leve, lembre ele é uma bomba ksksksks
   
4. Conectei à rede **Wi-Fi** (e, incrivelmente, a instalação foi bem rápida!).
   
5. Escolhi formatar o disco e usar exclusivamente para o servidor.
   
6. Defini o **nome do servidor, usuário e senha.**
![image](https://github.com/user-attachments/assets/4d0eeba8-4e35-4903-b1c1-c5bb7175846d)

## Instalando o OpenSSH

Durante a instalação, ativei a opção de instalar o **OpenSSH Server**, pois todas as configurações serão feitas remotamente, a partir do meu PC principal.

![image](https://github.com/user-attachments/assets/bdc50df8-e036-43a2-8be3-79f895511a28)

Não vamos instalar com nenhuma autenticidade, para instalar ja funcionando.
E agora começou a instalação!!!

## Acessando o Servidor via SSH

Com o Ubuntu Server instalado, fiz login e instalei algumas ferramentas úteis:

````
sudo apt install htop btop

````
Proximo passo foi pegar o ip da maquina para conseguir acessar pelo SSH:
````
ip address

````

Com o IP em mãos, fui para meu PC principal e conectei via SSH pelo CMD:
````
ssh (usuario@ipdoserver)

````
Ele pediu confirmação de segurança e a senha do usuário. Com isso, a conexão estava estabelecida!

## Instalando o Crafty Controller

O **Crafty Controller** é um excelente programa para gerenciar servidores de Minecraft. Segui o passo a passo da documentação oficial:
[Instalação do Crafty](https://docs.craftycontrol.com/pages/getting-started/installation/linux/)

Finalizando os passos, vai dar uma sequência de solicitações para você aceitar.

![image](https://github.com/user-attachments/assets/50a246ed-5017-4d44-b3a6-d0674164a23d)
![image](https://github.com/user-attachments/assets/91579dfe-73fe-4723-847a-321cda023a61)
![image](https://github.com/user-attachments/assets/d6a48883-697a-4934-8055-2ff3f3fc0f79)
![image](https://github.com/user-attachments/assets/d0515162-b11d-4db0-9864-6d28b7103e84)

Depois de finalizar os passos, executei os comandos necessários para criar o serviço no sistema (assim como um serviço do **Windows**, ele inicializa automaticamente).

Fazemos login como esta especificado no documento:
[Getting-started](https://docs.craftycontrol.com/pages/getting-started/access/)
Fiz login no Crafty acessando o IP do servidor:

````
https://192.168.0.15:8443

````
Agora esta rodando o Crafty Controller

![image](https://github.com/user-attachments/assets/3ac324a6-9d7b-4300-9441-3c5c387e46b4)

Para descobrir o usuário e senha gerados automaticamente:
````
sudo cat /var/opt/minecraft/crafty/crafty-4/app/config/default-creds.txt
````
Com isso ele vai buscar qual usuario e senha foi criado para você.

![image](https://github.com/user-attachments/assets/e0010d40-f854-4da9-a05a-5b7c44974426)

Agora, é só criar um novo servidor dentro do Crafty, definindo:

- **Server Type** - Minecraft Servers
- **Server Select** - Vanilla ou com Mods
- **Server Version** - Versão desejada
- **Server Name** - Nome do servidor

Configura a memoria ram dependendo do seu server
Agora ele vai baixar as informações do servidor da Microsoft / Mojang

![image](https://github.com/user-attachments/assets/f3bfb7df-3caa-4672-a854-11b1884b1e26)

![image](https://github.com/user-attachments/assets/5407af63-4926-4051-8cfc-ecb7a723fc5c)

Caso apareça erro de Java, instale o Java 21:

````
sudo apt install openjdk-21-jdk
````
Após o carregamento, basta entrar no servidor via IP e jogar!

## Permitindo Jogadores com Minecraft Pirata

Se quiser permitir jogadores com versão alternativa do Minecraft, altere a configuração do server.properties:
![image](https://github.com/user-attachments/assets/23115fe9-19a4-4369-b5ac-d3cd8265c6ab)
````
online-mode=false
````

Se deixar True so funcionar Minecraft original.
**Atenção**: Com essa opção ativada, qualquer jogador pode entrar com o nome de outro, pegando seus itens. Recomendo instalar um plugin de autenticação para evitar problemas.

## Abertura do Servidor para Jogadores Externos 

Beleza, seu server ja ta funcionando em modo local. Eu quero abrir de forma Não local, o que fazer? 
Ai ja engrossa mais o angu.

Se quiser que o servidor funcione fora da sua rede local, você precisa abrir a porta do seu roteador.

1. Acesse meuip.com.br e verifique seu **IP público**.
2. Se o IP público e o IP da WAN no roteador forem **iguais**, basta abrir a porta para o servidor.
3. Se forem **diferentes**, você está no CGNAT (rede compartilhada com outros clientes). 
![image](https://github.com/user-attachments/assets/88d40e00-29a9-444b-bc1a-af14a96182be)

Como podemos ver na imagem, estamos(meu caso também) em um roteador onde é dividida com outras casas e depois vamos para o acesso da internet.
Nesse caso, as soluções são:
- Criar uma **VPN**
- Usar o **Hamachi**
- Utilizar o **Playit.gg** (foi minha escolha para jogar rapidamente)

No **Playit.gg**, a versão gratuita fornece um endereço de conexão. Basta instalar o plugin e colocá-lo na pasta plugins do Crafty. Quando o servidor iniciar, ele fornecerá uma URL para login e configuração.
![image](https://github.com/user-attachments/assets/b648a41e-3d1c-45ee-ad6e-e4e5d9fac383)
![image](https://github.com/user-attachments/assets/56685a79-aa7b-4ea0-b552-1b9e322c2952)

Agora, é só conectar no Minecraft e jogar! 🎮🚀
---
Agora você tem um servidor de Minecraft totalmente funcional!
