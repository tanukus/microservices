FROM mcr.microsoft.com/dotnet/sdk:5.0 AS build
#RUN dotnet dev-certs https --clean --import ${HOME}/certs/aspnetcore.pfx -p Password123
WORKDIR /src
COPY backend.csproj .
RUN dotnet restore
COPY . .
RUN dotnet publish -c release -o /app

FROM aspnetcore-5.0-https As final
ENV ASPNETCORE_ENVIRONMENT=Production
COPY --from=build /app .
ENTRYPOINT ["dotnet", "backend.dll"]