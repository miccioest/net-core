## dotnet
mkdir -p $HOME/dotnet && tar zxf dotnet-sdk-2.1.3-linux-x64.tar.gz -C $HOME/dotnet
export PATH=$PATH:$HOME/dotnet

## vscode
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo sh -c 'echo -e "[code]\nname=Visual Studio Code\nbaseurl=https://packages.microsoft.com/yumrepos/vscode\nenabled=1\ngpgcheck=1\ngpgkey=https://packages.microsoft.com/keys/microsoft.asc" > /etc/yum.repos.d/vscode.repo'
yum check-update
sudo yum install code

## docker build
docker build -f asp.net-core-2.0/Dockerfile  -t samplewebapi .

## docker tag (aws ecr)
docker tag samplewebapi:latest 738010330285.dkr.ecr.us-east-1.amazonaws.com/samplewebapi:v5

## docker push (aws ecr)
docker push 738010330285.dkr.ecr.us-east-1.amazonaws.com/samplewebapi:v5
