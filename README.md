# fileshare-info-containers

---

## Tools

```bash
wget https://packages.microsoft.com/config/ubuntu/20.10/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb

sudo apt-get update; \
  sudo apt-get install -y apt-transport-https && \
  sudo apt-get update && \
  sudo apt-get install -y dotnet-sdk-5.0
```

## Files

- docker
  - backend
    - src
      - _some C# project_ \( to regenerate, run `cd docker/backend/ && dotnet new webapi -n BackendApp -o src && cd ../..` \)
  - frontend
    - src
      - _some Blazor project_ \( to regenerate, run `cd docker/frontend/ && dotnet new blazorwasm -n FrontendApp -o src && cd ../..` \)
- docker-compose.yml
- README.md

## Run

```bash
docker-compose up -d --build
```

- [Frontend](http://localhost:8000)
  - ex: http://localhost:8000/counter
- [Backend](http://localhost:8080)
  - ex: http://localhost:8080/WeatherForecast
