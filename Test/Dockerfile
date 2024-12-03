FROM mcr.microsoft.com/dotnet/core/sdk:3.1 AS build-env
WORKDIR /app

# Proje dosyasını kopyala ve bağımlılıkları yükle
COPY Test/Test.csproj ./
RUN dotnet restore

# Kalan dosyaları kopyala ve yayımla
COPY Test/. ./
RUN dotnet publish -c Release -o out

# Runtime aşaması
FROM mcr.microsoft.com/dotnet/core/aspnet:3.1
WORKDIR /app
COPY --from=build-env /app/out .

ENTRYPOINT ["dotnet", "Test.dll"]


