
In your local machine:

To rebuild the docker files with new changes:
```commandline
sudo docker build -t syntaxsurge/autoblogger:latest .
```

To push the docker files
```commandline
sudo docker push syntaxsurge/autoblogger:latest
```

To rebuild and push without any cache
```bash
sudo docker build --no-cache -t syntaxsurge/autoblogger:latest . && sudo docker push syntaxsurge/autoblogger:latest
```

If you are experiencing timeouts it might be because you connected to VPN before, you can restart the docker
```commandline
systemctl restart docker
```

If you are still experiencing timeouts, then restart your computer.
If you are still experiencing timeouts, use VPN.

In Your UBUNTU server:

```bash
sudo apt update && \
sudo apt install apt-transport-https ca-certificates curl software-properties-common -y && \
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg && \
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null && \
sudo apt update && \
sudo apt install docker-ce -y && \
sudo apt install docker-compose -y && \
sudo systemctl status docker
```

```commandline
git clone https://github.com/syntaxsurge/autoblogger_docker.git
```

```commandline
cd /root/autoblogger_docker
```

...or if you already cloned it but just want to pull the latest changes:
```bash
git pull
```

- Paste the environment files

```bash
nano .env
```

```bash
docker login
```

To stop and remove the docker processes
```commandline
docker-compose down
```

To pull the latest changes:
```commandline
docker-compose pull
```

- To run the main services (-d flag means dettached, will run even though you closed the terminal)
To compose new changes (this will **stop** the current docker, so **you DON'T need to run** `docker-compose down`)
```commandline
docker-compose up -d
```

If you don't have any changes to your images, but you have changes to your `.yml` file, you can force compose it:
```commandline
docker-compose up -d --force-recreate
```

- To pull latest version and compose in one line
```bash
docker-compose pull && docker-compose up -d
```

To check if processes health
```commandline
docker-compose ps
```

To see processes logs
```commandline
docker-compose logs
```

To view real-time logs, change `service_name` to the name of the service whose logs you want to see.
```commandline
docker-compose logs -f service_name
```

available services in the docker-compose: `api`, `worker`, `nginx`

- For example, to see real-time celery worker logs
```commandline
docker-compose logs -f worker
```

To pull latest version from GitHub and docker and compose it in one line:
```bash
cd /root/autoblogger_docker && \
git pull && \
docker-compose down && \
docker-compose pull && \
docker-compose up -d
```