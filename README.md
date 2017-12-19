## dotnet build + docker build
dotnet publish -c Release
cd ..
docker build -f asp.net-core-2.0/Dockerfile  -t samplewebapi --build-arg source=bin/Release/netcoreapp2.0/publish .

## docker tag

## aws ecr push
