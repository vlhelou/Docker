FROM mcr.microsoft.com/dotnet/sdk:5.0
RUN apt update
RUN apt install curl
RUN cd ~
RUN curl -sL https://deb.nodesource.com/setup_15.x -o nodesource_setup.sh
RUN bash nodesource_setup.sh
RUN apt install nodejs --yes 
