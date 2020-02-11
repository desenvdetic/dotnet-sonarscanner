FROM mcr.microsoft.com/dotnet/core/sdk:2.2

COPY ca-trust/*.crt /usr/local/share/ca-certificates/

RUN update-ca-certificates \
&& echo "deb http://ppa.launchpad.net/linuxuprising/java/ubuntu bionic main" | tee /etc/apt/sources.list.d/linuxuprising-java.list \
&& apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys EA8CACC073C3DB2A \
&& echo oracle-java12-installer shared/accepted-oracle-license-v1-2 select true | /usr/bin/debconf-set-selections \
&& curl -sL https://deb.nodesource.com/setup_12.x | bash \
&& apt-get update \
&& apt-get install -y --no-install-recommends \
    dirmngr \
    oracle-java12-set-default \
    oracle-java12-installer \
    nodejs \
&& export PATH="$PATH:/root/.dotnet/tools" \
&& dotnet tool install --global dotnet-sonarscanner
