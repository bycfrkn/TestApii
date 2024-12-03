# Build aþamasý
FROM mcr.microsoft.com/dotnet/core/sdk:3.1 AS build-env
WORKDIR /app

# Proje dosyalarýný kopyala ve baðýmlýlýklarý yükle
COPY *.csproj .
RUN dotnet restore

# Tüm dosyalarý kopyala ve yayýnla
COPY . ./
RUN dotnet publish -c Release -o out

# Runtime aþamasý
FROM mcr.microsoft.com/dotnet/core/aspnet:3.1
WORKDIR /app
COPY --from=build-env /app/out .

# Çalýþtýrýlacak komut
ENTRYPOINT ["dotnet", "Test.dll"]
