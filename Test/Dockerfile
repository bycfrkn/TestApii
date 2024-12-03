# Build aşaması
FROM mcr.microsoft.com/dotnet/core/sdk:3.1 AS build-env
WORKDIR /app

# Proje dosyasını kopyala
COPY ./Test/Test.csproj ./
RUN dotnet restore

# Tüm dosyaları kopyala
COPY ./Test/. ./
RUN dotnet publish -c Release -o out

# Runtime aşaması
FROM mcr.microsoft.com/dotnet/core/aspnet:3.1
WORKDIR /app
COPY --from=build-env /app/out .

# Çalıştırılacak komut
ENTRYPOINT ["dotnet", "Test.dll"]
