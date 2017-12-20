## docker build
docker build -f asp.net-core-2.0/Dockerfile  -t samplewebapi .

## docker tag (aws ecr)
docker tag samplewebapi:latest 738010330285.dkr.ecr.us-east-1.amazonaws.com/samplewebapi:v5

## docker push (aws ecr)
docker push 738010330285.dkr.ecr.us-east-1.amazonaws.com/samplewebapi:v5
