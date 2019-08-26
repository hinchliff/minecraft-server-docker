FROM gradle:jdk8 as builder

RUN cd / && \
    git clone --single-branch --branch mcpenew https://github.com/ProtocolSupport/ProtocolSupport.git && \
    cd ProtocolSupport && \
    ./gradlew jar

#FROM hypriot/rpi-java:jre-1.8.111
FROM openjdk:8-jre-slim

ENV SPIGOT_VER 1.14.3
#Download last version of spigot
        #&& wget -q https://cdn.getbukkit.org/spigot/spigot-1.12.2.jar -O /webserver/minecraft_server.jar \
RUN apt-get update \
	&& apt-get -y upgrade \
	&& apt-get -y install git curl \
        && mkdir -p /spigot \
	&& cd /spigot \
        && curl -Ss -o /spigot/BuildTools.jar https://hub.spigotmc.org/jenkins/job/BuildTools/lastSuccessfulBuild/artifact/target/BuildTools.jar \
	&& java -jar BuildTools.jar --rev $SPIGOT_VER \
        && rm -rf /spigot/BuildData /spigot/BuildTools.jar /spigot/Bukkit /spigot/CraftBukkit /spigot/Spigot /spigot/apache-maven-* /spigot/work \
        && apt-get -y autoremove --purge \
        && rm -rf /var/lib/apt/lists/*

#RUN git clone --single-branch --branch mcpenew https://github.com/ProtocolSupport/ProtocolSupport.git && \
#    cd ProtocolSupport && \
#    ./gradlew jar


EXPOSE 25565


# /data contains static files and database
VOLUME ["/data"]

WORKDIR /data

# add ProtocolSupport plugin
#RUN mkdir /data/plugins && \
#    curl -Ss -o /data/plugins/ProtocolSupport.jar https://build.true-games.org/job/ProtocolSupport/lastSuccessfulBuild/artifact/target/ProtocolSupport.jar
COPY --from=builder /ProtocolSupport/target/ProtocolSupport.jar /data/plugins/ProtocolSupport.jar

# start the server
#CMD ["java","-Xms512M","-Xmx1008M","-Dcom.mojang.eula.agree=true","-Dfile.encoding=UTF-8","-jar","/webserver/minecraft_server.jar","nogui"]
#CMD ["java","-Xms512M","-Xmx1008M","-Dcom.mojang.eula.agree=true","-Dfile.encoding=UTF-8","-jar","/spigot/spigot-${SPIGOT_VER}.jar","nogui"]
CMD java -Xms512M -Xmx1008M -Dcom.mojang.eula.agree=true -Dfile.encoding=UTF-8 -jar /spigot/spigot-${SPIGOT_VER}.jar nogui
