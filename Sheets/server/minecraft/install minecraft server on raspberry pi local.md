# Install minecraft server on raspberry pi local

## Install RASPBERRY PI OS LITE(64-BIT)

// TODO

## Log on to your raspy via ssh

// TODO

## Handle packages

On your raspberry pi start with these two commands.

```bash
sudo apt update
sudo apt upgrade
```

This will update all your installed packages as well as your package manager. This may take a while, but no worries this doesn't mean it wont work :).

### Install java

Next we need java, it is important that you have installed the 64 bit os (And you have an raspberry pi 3 or newer, the older ones won't support 64bit)

Sadly at this day, i am writing this, a simple installation with apt isn't quite working yet. So we will install it with adding the azul repository to our pi.

1. First we need the package to set up Azul

   ```bash
   sudo apt install curl gnupg ca-certificates
   ```

2. Next we will download and save the Azul GPG key to our system.

   ```bash
   curl -s https://repos.azul.com/azul-repo.key | sudo gpg --dearmor -o /usr/share/keyrings/azul.gpg
   ```

3. Next we add the azul repository to our list of sources, so we get access to the latest version of Java(openjdk).

   ```bash
   echo "deb [arch=arm64 signed-by=/usr/share/keyrings/azul.gpg] https://repos.azul.com/zulu/deb stable main" | sudo tee /etc/apt/sources.list.d/zulu.list
   ```

4. Next just refresh your packages


   ```bash	
   sudo apt update
   ```

5. Now the time has come just install OpenJDK with the following command.

   ```bash
   sudo apt install zulu21-jdk-headless
   ```

6. Last but not least, lets test if everything worked the way it should.

   ```bash
   java --version
   ```

it should output something like:

```bash
openjdk 21.0.3 2024-04-16 LTS
OpenJDK Runtime Environment Zulu21.34+19-CA (build 21.0.3+9-LTS)
OpenJDK 64-Bit Server VM Zulu21.34+19-CA (build 21.0.3+9-LTS, mixed mode, sharing)
```

This should have installed java version 21. If you will use an older Version of minecraft you won't need this new version, everything from 1.20 and down will work with java 17 (And 32 bit, as well as the older raspberry pis).

## Download Minecraft Server

Visit the webpage: https://getbukkit.org/

Here you can choose between Spigot, Bukkit and Vanilla. If you want to install plugins inform yourself about if you should use spigot or bukkit. But since i am going to play the default minecraft i will install Vanilla.

If you found your download link copy it instead of click on it. As an example here is my link:

```https://piston-data.mojang.com/v1/objects/450698d1863ab5180c25d7c804ef0fe6369dd1ba/server.jar```

### wget to your raspberry pi

The command `wget` will download something from the web, we will use this to accelerate the process. But if you want to you can just use scp etc. But we will continue with wget.



I will install my server into a new folder, if you want to as well just run:

```bash
mkdir minecraft-server
cd minecraft-server
```



In your raspberry pi (ssh), run the following:

```bash
wget https://piston-data.mojang.com/v1/objects/450698d1863ab5180c25d7c804ef0fe6369dd1ba/server.jar
```

Now look if you installed it correct by using `ls`. If it shows **server.jar** everything worked.

### start your server

by running: 

```bash
java -Xmx1024M -Xms1024M -jar server.jar nogui
```

You will run your server for the first time, but it wont work yet. You need to accept the Eula. 

Open the eula.txt, with:

```bash
nano eula.txt
```

Change `eula=false` to `eula=true` to agree to Minecraft's End User License Agreement. Save and exit (`Ctrl+O`, then `enter`, then `Ctrl+X`). 

Now start your server again. 

```bash
java -Xmx1024M -Xms1024M -jar server.jar nogui
```

You can change `-Xmx1024M`  and `-Xms1024M` to whatever ram you would like to give your Minecraft server, but be careful to not use all the ram your raspberry pi has. 

If you did everything correct, the world should now render. And you can join. 

## connect to your new server

Quit the server with `Ctrl+C` and enter

```bash
hostname -I
```

this will give you, the ip-address of your raspberry pi. This will output a large address, because we install the server locally just copy the first address. It should look something like `192.168.xxx.xxx`. 

Add this to your minecraft client as Server address. Now start the server again with: 

```bash
java -Xmx1024M -Xms1024M -jar server.jar nogui
```

Join and et voilà, you have your own, more or less free minecraft server.
