FROM mcr.microsoft.com/dotnet/core/sdk:3.1 as build
WORKDIR /app
COPY *.csproj . 
RUN dotnet restore
COPY . .
RUN dotnet publish AspNetCoreMVC.csproj -c Release -o out
FROM mcr.microsoft.com/dotnet/aspnet:3.1
WORKDIR /app
COPY --from=build /app/out .
ENV ASPNETCORE_URLS="http://*:4500"
ENV ASPNETCORE_ENVIRONMENT="DEVELOPMENT"
ENV MySqlCon="uzak sunucu veritabanư yolu"
ENTRYPOINT ["dotnet","AspNetCoreMVC.dll"]