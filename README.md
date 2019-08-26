Inspired by https://github.com/anthonyraymond/rpi-minecraft-spigot, with many changes

## minecraft-spigot-java-bedrock

A (Java / non-Bedrock) Minecraft server with the ProtocolSupport plugin to extend to PE (Bedrock) clients.

### Building minecraft-spigot-java-bedrock
This downloads and build the latest ProtocolSupport:mcpenew, and the latest Spigot.

`docker build -t hinchliff/minecraft-spigot:1.14.3 -t hinchliff/minecraft-spigot-java-bedrock:latest .`

### Running minecraft-spigot-java-bedrock
`docker run -d -v /<PATH>/<TO>/<DATA>:/data -p 25565:25565 -p 25565:25565/udp --name="minecraft-server" hinchliff/minecraft-spigot-java-bedrock:1.14.3`

## minecraft-spigot-java-bedrock-rpi
(Coming Soon)

## What to put into the /data folder
Nothing is needed for the server to run.
Howether this is the place to put your minecraft config files, and realms if you already have these.

