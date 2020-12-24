# Exemplo de um Dockerfile para um projeto asp.net + angular
O arquivo deve estar no mesmo diretório do arquivo .csproj. 
## observação
A `FROM aspnpm AS build` a imagem _aspnpm_ foi criada previamente  com o docker 'Asp.Net+Node'
## alteração
`ENTRYPOINT ["dotnet", "InstallDocker.dll"]` lembrar de mudar essa linha, apontando para a dll gerada pelo seu projeto