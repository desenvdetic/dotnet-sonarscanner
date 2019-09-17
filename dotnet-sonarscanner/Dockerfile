FROM mcr.microsoft.com/dotnet/core/sdk:2.2

COPY ca-trust/*.crt /usr/local/share/ca-certificates/

RUN update-ca-certificates \
&& apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys EA8CACC073C3DB2A \
&& echo "deb http://ppa.launchpad.net/linuxuprising/java/ubuntu bionic main" | tee /etc/apt/sources.list.d/linuxuprising-java.list \
&& echo oracle-java12-installer shared/accepted-oracle-license-v1-2 select true | /usr/bin/debconf-set-selections \
&& apt-get update \
&& apt-get install -y --no-install-recommends \
    dirmngr \
    oracle-java12-installer \
    oracle-java12-set-default \
&& dotnet tool install --global dotnet-sonarscanner \
&& export PATH="$PATH:/root/.dotnet/tools"