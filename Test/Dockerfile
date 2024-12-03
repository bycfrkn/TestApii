# Build aşaması için .NET Framework SDK kullanıyoruz
FROM mcr.microsoft.com/dotnet/framework/sdk:4.8 AS build-env
WORKDIR /app

# Proje dosyasını ve bağımlılıklarını kopyala
COPY Test/. ./
RUN nuget restore

# Projeyi derle
RUN msbuild /p:Configuration=Release /p:OutputPath=out

# Çalıştırma aşaması için .NET Framework ASP.NET imajını kullanıyoruz
FROM mcr.microsoft.com/dotnet/framework/aspnet:4.8
WORKDIR /app

# Derlenmiş dosyaları çalışma ortamına kopyala
COPY --from=build-env /app/out .

# IIS üzerinde çalıştır



