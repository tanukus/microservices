FROM mcr.microsoft.com/dotnet/sdk:5.0 AS build
WORKDIR /src
COPY frontend.csproj .
RUN dotnet restore
COPY . .
RUN dotnet publish -c release -o /app

FROM aspnetcore-5.0-https:latest
WORKDIR /app
COPY --from=build /app .
ENTRYPOINT ["dotnet", "frontend.dll"]