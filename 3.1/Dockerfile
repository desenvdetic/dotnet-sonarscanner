FROM mcr.microsoft.com/dotnet/core/sdk:3.1

COPY ca-trust/*.crt /usr/local/share/ca-certificates/

RUN update-ca-certificates \
    && apt update -y && apt upgrade -y \
    && apt install -y default-jdk \
    && curl -sL https://deb.nodesource.com/setup_12.x | bash \
    && apt-get install -y --no-install-recommends dirmngr \
    && apt-get install -y --no-install-recommends nodejs \
    && export PATH="$PATH:/root/.dotnet/tools" \ 
    && dotnet tool install --global dotnet-sonarscanner