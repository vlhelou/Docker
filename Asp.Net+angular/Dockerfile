FROM aspnpm AS build
WORKDIR /src
COPY ["*.csproj", "./"]
RUN dotnet restore 
COPY . ./
RUN dotnet publish -c Release -o out --self-contained false --runtime linux-x64


FROM mcr.microsoft.com/dotnet/aspnet:5.0
WORKDIR /app
EXPOSE 80
ENV ASPNETCORE_URLS=http://+:80
COPY --from=build /src/out .
ENTRYPOINT ["dotnet", "InstallDocker.dll"]


