
```bash
sudo apt update && \
sudo apt install apt-transport-https ca-certificates curl software-properties-common -y && \
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt update
sudo apt install docker-ce -y
sudo apt install docker-compose -y
sudo systemctl status docker
```

- Paste the environment files

```bash
nano .env
```

```bash
docker login
```

- Compose

```bash
docker-compose up -d
```

In your local machine:

To rebuild the docker files with new changess:
```commandline
sudo docker build -t syntaxsurge/autoblogger:latest .
```

To push the docker files
```commandline
sudo docker push syntaxsurge/autoblogger:latest
```

To stop and remove the docker processes
```commandline
docker-compose down
```

To pull the latest changes:
```commandline
docker-compose pull
```

To compose new changes
```commandline
docker-compose up -d
```

To check if processes health
```commandline
docker-compose ps
```

To see processes logs
```commandline
docker-compose logs
```