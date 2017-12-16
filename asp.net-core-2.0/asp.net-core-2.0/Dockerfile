FROM microsoft/aspnetcore:2.0 AS base
WORKDIR /app
EXPOSE 80

FROM microsoft/aspnetcore-build:2.0 AS build
WORKDIR /src
COPY *.sln ./
COPY asp.net-core-2.0/asp.net-core-2.0.csproj asp.net-core-2.0/
RUN dotnet restore
COPY . .
WORKDIR /src/asp.net-core-2.0
RUN dotnet build -c Release -o /app

FROM build AS publish
RUN dotnet publish -c Release -o /app

FROM base AS final
WORKDIR /app
COPY --from=publish /app .
ENTRYPOINT ["dotnet", "asp.net-core-2.0.dll"]
