# Minecraft Server
This repository documents the step-by-step process of how I set up a Minecraft server from scratch. From choosing the version to the final configuration, I explain each step for those who want to create their own server simply and efficiently.
---

Well, friends, I had some free time at home and decided to fulfill a childhood dream that will also help me with future projects: I created a Minecraft server.

## Choosing the Machine

The first step was deciding which machine to run the server on. Luckily, I had my first laptop, which was quite outdated:

- **RAM:** 1GB
- **Processor:** ???
- **HDD:** 250GB

I tried using this laptop during my technical course, but it was a real test of patience, to the point that I preferred using my phone instead.

## Upgrading the Laptop

The second step was to try improving this laptop in some way. I had another laptop bought as defective to repair, and I checked what I could salvage:

- Took two **2GB DDR1 RAM sticks.**
- Installed a **wireless network card** because the original one was even worse.
- Replaced the HDD with an **SSD** I had available.
- Changed the **thermal paste**, as it had been years since the last replacement.

After installing everything, I powered up the machine, and to my delight, everything was working fine!

## Creating a Bootable USB Drive

To install the server's operating system, I created a bootable USB drive and opted for **Ubuntu Server** because it is easy to install and configure. I used **Ventoy** to create the bootable USB, as I've been using this tool for a while and really like it.

## Installing Ubuntu Server

I plugged in the USB drive and started the installation:

1. Chose the **English** language since most commands are in English, and using Portuguese could change the command structure.
![image](https://github.com/user-attachments/assets/316d8f3f-e4fe-4608-b5dc-6474344cd93a)

2. Set the **keyboard** to Portuguese to avoid issues.
![image](https://github.com/user-attachments/assets/c3648047-e703-474c-9947-740bf81bfc0a)

3. Installed the **minimal** version of Ubuntu Server to avoid unnecessary programs and keep the system lightweight.

4. Connected to **Wi-Fi**, and surprisingly, the installation was quite fast!

5. Chose to format the disk and use it exclusively for the server.

6. Set the **server name, user, and password.**
![image](https://github.com/user-attachments/assets/4d0eeba8-4e35-4903-b1c1-c5bb7175846d)

## Installing OpenSSH

During the installation, I enabled the option to install **OpenSSH Server** since all configurations would be done remotely from my main PC.

![image](https://github.com/user-attachments/assets/bdc50df8-e036-43a2-8be3-79f895511a28)

We will install it without authentication so that it works right away.
Now the installation begins!

## Accessing the Server via SSH

With Ubuntu Server installed, I logged in and installed some useful tools:

````
sudo apt install htop btop
````

The next step was to get the machine's IP to access it via SSH:

````
ip address
````

With the IP in hand, I went to my main PC and connected via SSH using CMD:

````
ssh (user@server-ip)
````

It asked for security confirmation and the user password. With that, the connection was established!

## Installing Crafty Controller

**Crafty Controller** is an excellent program for managing Minecraft servers. I followed the official documentation steps:
[Crafty Installation](https://docs.craftycontrol.com/pages/getting-started/installation/linux/)

After completing the steps, you will go through a series of prompts to accept.

![image](https://github.com/user-attachments/assets/50a246ed-5017-4d44-b3a6-d0674164a23d)
![image](https://github.com/user-attachments/assets/91579dfe-73fe-4723-847a-321cda023a61)
![image](https://github.com/user-attachments/assets/d6a48883-697a-4934-8055-2ff3f3fc0f79)
![image](https://github.com/user-attachments/assets/d0515162-b11d-4db0-9864-6d28b7103e84)

After completing the steps, I executed the necessary commands to create the service on the system (just like a **Windows** service, it starts automatically).

Log in as specified in the document:
[Getting Started](https://docs.craftycontrol.com/pages/getting-started/access/)
I logged into Crafty by accessing the server's IP:

````
https://192.168.0.15:8443
````

Now Crafty Controller is running!

![image](https://github.com/user-attachments/assets/3ac324a6-9d7b-4300-9441-3c5c387e46b4)

To find the automatically generated username and password:

````
sudo cat /var/opt/minecraft/crafty/crafty-4/app/config/default-creds.txt
````

This will retrieve the created user and password.

![image](https://github.com/user-attachments/assets/e0010d40-f854-4da9-a05a-5b7c44974426)

Now, create a new server within Crafty by defining:

- **Server Type** - Minecraft Servers
- **Server Select** - Vanilla or with Mods
- **Server Version** - Desired version
- **Server Name** - Server name

Configure the RAM according to your server needs.
Now it will download the server files from Microsoft / Mojang.

![image](https://github.com/user-attachments/assets/f3bfb7df-3caa-4672-a854-11b1884b1e26)
![image](https://github.com/user-attachments/assets/5407af63-4926-4051-8cfc-ecb7a723fc5c)

If a Java error appears, install Java 21:

````
sudo apt install openjdk-21-jdk
````

After loading, simply join the server via IP and play!

## Allowing Players with Cracked Minecraft

If you want to allow players with an alternative Minecraft version, modify the `server.properties` file:

![image](https://github.com/user-attachments/assets/23115fe9-19a4-4369-b5ac-d3cd8265c6ab)

````
online-mode=false
````

If set to **true**, only original Minecraft will work.
**Warning**: With this option enabled, any player can log in using another player's name and take their items. I recommend installing an authentication plugin to avoid issues.

## Opening the Server for External Players

Alright, your server is working locally. But what if you want to open it for external connections?

1. Visit [myip.com.br](https://www.myip.com/) to check your **public IP**.
2. If the public IP and the WAN IP on your router are **the same**, simply open the port for the server.
3. If they are **different**, you are on CGNAT (shared network with other clients).

Solutions:
- Create a **VPN**
- Use **Hamachi**
- Use **Playit.gg** (my choice for quick setup)

In **Playit.gg**, the free version provides a connection address. Simply install the plugin in Crafty's plugins folder. When the server starts, it will generate a URL for login and setup.

Now, just connect in Minecraft and play! 🎮🚀
