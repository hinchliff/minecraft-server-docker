Inspired by https://github.com/anthonyraymond/rpi-minecraft-spigot, with many changes

## TODO:
* Figure out Docker Volumes vs. User configured locations vs. writing a Plugin inside that Volume

## minecraft-spigot-java-bedrock

A (Java / non-Bedrock) Minecraft server with the ProtocolSupport plugin to extend to PE (Bedrock) clients.

### Building minecraft-spigot-java-bedrock
This downloads and build the latest ProtocolSupport:mcpenew, and the latest Spigot.

`docker build -t hinchliff/minecraft-spigot-java-bedrock:1.14.3 -t hinchliff/minecraft-spigot-java-bedrock:latest .`

### Running minecraft-spigot-java-bedrock
`docker run -d -p 25565:25565 -p 25565:25565/udp --name=minecraft-server hinchliff/minecraft-spigot-java-bedrock:1.14.3`

Or maybe with a data volume:
`docker run -d -v /<PATH>/<TO>/<DATA>:/data -p 25565:25565 -p 25565:25565/udp --name=minecraft-server hinchliff/minecraft-spigot-java-bedrock:1.14.3`

## minecraft-spigot-java-bedrock-rpi
A (Java / non-Bedrock) Minecraft server for Raspberry Pi (arm32v7) with the ProtocolSupport plugin to extend to PE (Bedrock) clients.

### Building minecraft-spigot-java-bedrock-rpi
This downloads and build the latest ProtocolSupport:mcpenew, and the latest Spigot.

`docker build -t hinchliff/minecraft-spigot-java-bedrock-rpi:1.14.3 -t hinchliff/minecraft-spigot-java-bedrock-rpi:latest .`

### Running minecraft-spigot-java-bedrock-rpi
`docker run -d -p 25565:25565 -p 25565:25565/udp --name=minecraft-server hinchliff/minecraft-spigot-java-bedrock-rpi:1.14.3`

Or maybe with a data volume:
`docker run -d -v /<PATH>/<TO>/<DATA>:/data -p 25565:25565 -p 25565:25565/udp --name=minecraft-server hinchliff/minecraft-spigot-java-bedrock-rpi:1.14.3`


## What to put into the /data folder
Nothing is needed for the server to run.
Howether this is the place to put your minecraft config files, and realms if you already have these.

## Links
* https://github.com/ProtocolSupport/ProtocolSupport
  * https://github.com/ProtocolSupport/ProtocolSupport/pull/972
* https://www.spigotmc.org
* https://minecraft.gamepedia.com/Bedrock_Edition_server_software#Protocol_Translator_list
