# FROM mcr.microsoft.com/dotnet/aspnet:7.0
# WORKDIR /app
# COPY /bin/Release/net7.0/publish /app/
# ENTRYPOINT ["dotnet", "WebApp.dll"]

# FROM mcr.microsoft.com/dotnet/sdk:7.0
# WORKDIR /app
# COPY . .
# RUN dotnet restore
# RUN dotnet publish WebApp.csproj -c release -o out
# WORKDIR out
# ENV ASPNETCORE_URLS="http://*:4500"
# ENTRYPOINT ["dotnet", "WebApp.dll"]
# docker run -p 5000:4500 --name c-self-webapp self-webapp:1.0

FROM mcr.microsoft.com/dotnet/sdk:7.0 AS build
WORKDIR /app
COPY *.csproj .
RUN dotnet restore
COPY . .
RUN dotnet publish WebApp.csproj -c release -o out
FROM mcr.microsoft.com/dotnet/aspnet:7.0
WORKDIR /app
COPY --from=build /app/out .
ENV ASPNETCORE_URLS="http://*:4500"
ENTRYPOINT ["dotnet", "WebApp.dll"]


# docker login
# docker build -t <IMAGE NAME>:{x.x} . => image olustur
# docker images => tum image leri goster
# docker rmi <IMAGE ID> => image e bagli konteynar yok ise kaldir
# docker rmi <IMAGE ID> --force => image e bagli calisan konteynar yok ise kaldir
# docker create --name <CONTAINER NAME> <IMAGE NAME> => konteynar olustur
# docker ps -a                                          => tum konteynarlari goster
# docker ps => calisan konteynarlari goster
# docker start <CONTAINER NAME> => konteynari calistir
# docker stop <CONTAINER NAME> => konteynari durdur
# docker rm <CONTAINER NAME> => konteynari calismiyorsa kaldir
# docker rm <CONTAINER NAME> --force => konteynari calisiyorsa da kaldir
# docker attach <CONTAINER NAME> => konteynari izle
# docker run -p 5000:80 --name <CONTAINER NAME> <IMAGE NAME> => konteynar olustur ve calistir ve attach
# docker run --rm --name <CONTAINER NAME> <IMAGE NAME> => konteynar olustur ve calistir ve attach, kapatinca kaldir
# docker pull <IMAGE NAME> => hub dan image cekme
# docker tag <IMAGE NAME> <TAG FULLNAME> => mevcut image i referans alan image tag i olusturur
# docker push senfurkan92/console-app:tagname => docker hub a push


## PUSH
# önce mevcut image den tag alinir
# docker tag console-app:v1 senfurkan92/console-app:1.0
# sonra push edilir
# docker push senfurkan92/console-app:1.0
# yeni versiyon
# docker tag console-app:v1 senfurkan92/console-app:2.0
# docker push senfurkan92/console-app:2.0