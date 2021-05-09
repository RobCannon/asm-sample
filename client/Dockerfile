FROM mcr.microsoft.com/dotnet/sdk:5.0 AS build
WORKDIR /src

COPY *.csproj .
RUN dotnet restore

COPY . .
RUN dotnet publish -c Release -o /app

FROM nginx:alpine
WORKDIR /usr/share/nginx/html

COPY --from=build /app/wwwroot .
COPY nginx.conf /etc/nginx/nginx.conf