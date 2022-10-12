FROM mcr.microsoft.com/dotnet/sdk:6.0-alpine as build
WORKDIR /app
COPY . .
RUN dotnet restore
RUN dotnet publish -o /app/published-app

FROM mcr.microsoft.com/dotnet/aspnet:6.0-alpine as runtime
WORKDIR /app
COPY --from=build /app/published-app /app
ENTRYPOINT [ "dotnet", "/app/DockerNetExample.dll" ]



# FROM mcr.microsoft.com/dotnet/aspnet:6.0 AS base
# WORKDIR /app
# EXPOSE 80
# EXPOSE 443

# FROM mcr.microsoft.com/dotnet/sdk:6.0 AS build
# WORKDIR /src
# COPY ["Dummies.DummyB.csproj", "Dummies.DummyB/"]
# RUN dotnet restore "Dummies.DummyB/Dummies.DummyB.csproj"
# COPY . .
# WORKDIR "/src/Dummies.DummyB"
# RUN dotnet build "Dummies.DummyB.csproj" -c Release -o /app/build

# FROM build AS publish
# RUN dotnet publish "Dummies.DummyB.csproj" -c Release -o /app/publish

# FROM base AS final
# WORKDIR /app
# COPY --from=publish /app/publish .
# ENTRYPOINT ["dotnet", "Dummies.DummyB.dll"]
