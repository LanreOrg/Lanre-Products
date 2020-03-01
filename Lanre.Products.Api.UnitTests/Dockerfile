FROM mcr.microsoft.com/dotnet/core/aspnet:3.1-alpine AS base
WORKDIR /app
EXPOSE 80
EXPOSE 443

FROM mcr.microsoft.com/dotnet/core/sdk:3.1-alpine AS build
WORKDIR /src
COPY ["Lanre.Products.Api/Lanre.Products.Api.csproj", "Lanre.Products.Api/"]
COPY ["Lanre.Products.Api.UnitTests/Lanre.Products.Api.UnitTests.csproj", "Lanre.Products.Api.UnitTests/"]
RUN dotnet restore "Lanre.Products.Api/Lanre.Products.Api.csproj"
RUN dotnet restore "Lanre.Products.Api.UnitTests/Lanre.Products.Api.UnitTests.csproj"
COPY . .
WORKDIR "/src/Lanre.Products.Api.UnitTests/"
RUN dotnet build "Lanre.Products.Api.UnitTests.csproj" -c Release -o /app


FROM build as unittest
WORKDIR /src/Lanre.Products.Api.UnitTests
