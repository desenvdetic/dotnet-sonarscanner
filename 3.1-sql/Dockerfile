FROM mcr.microsoft.com/mssql/server:2019-latest

ENV TZ "America/Porto_Velho"

USER 0
COPY ca-trust/*.crt /usr/local/share/ca-certificates/
RUN update-ca-certificates

RUN wget https://packages.microsoft.com/config/ubuntu/18.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
RUN dpkg -i packages-microsoft-prod.deb

RUN apt-get -y update && apt-get -y upgrade; \
  apt-get install -y apt-transport-https default-jdk jq curl nodejs dirmngr && \
  apt-get -y update && apt-get -y upgrade;

RUN apt-get install -y dotnet-sdk-3.1 && \
  apt-get install -y aspnetcore-runtime-3.1 && \
  apt-get install -y dotnet-runtime-3.1

RUN export PATH="$PATH:/root/.dotnet/tools"
RUN dotnet tool install --global dotnet-sonarscanner