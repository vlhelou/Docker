FROM mcr.microsoft.com/dotnet/aspnet:8.0 AS base
USER app
WORKDIR /app
EXPOSE 8080

FROM mcr.microsoft.com/dotnet/sdk:8.0 AS build
ARG BUILD_CONFIGURATION=Release
WORKDIR /src
COPY ["backFolder/back.csproj", "."]
RUN dotnet restore "./back.csproj"
COPY backFolder/. .
WORKDIR "/src/."
RUN dotnet build "./back.csproj" -c $BUILD_CONFIGURATION -o /app/build

FROM build AS publish
ARG BUILD_CONFIGURATION=Release
RUN dotnet publish "./back.csproj" -c $BUILD_CONFIGURATION -o /app/publish 

FROM node:latest as buildng
WORKDIR /usr/local/app
COPY front/ .
RUN npm install
RUN npm run build



FROM base AS final
WORKDIR /app
COPY --from=publish /app/publish .
COPY --from=buildng /usr/local/app/dist/front/browser ./wwwroot
ENTRYPOINT ["dotnet", "back.dll"]