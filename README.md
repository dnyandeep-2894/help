docker pull ubuntu:22.04
docker run -dit --name temp_ubuntu ubuntu:22.04
docker ps
docker volume create backup_data
docker volume ls
docker run -dit --name container1 -v backup_data:/data ubuntu:22.04
docker exec container1 bash -c "echo 'This is backup data for 260840123037' > /data/260840123037.txt && ls -l /data"
docker stop container1
docker rm container1
docker run -dit --name container2 -v backup_data:/data ubuntu:22.04
docker exec container2 ls -l /data
docker exec container2 cat /data/260840123037.txt
docker exec container2 bash -c "apt-get update && apt-get install -y curl nano"
docker commit container2 260840123037:v2
docker images# help
