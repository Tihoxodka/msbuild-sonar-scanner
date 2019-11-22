# msbuild-sonar-scanner for docker
inspired by: https://github.com/burakince/docker-dotnet-sonarscanner

# If you want build your own docker image
Just clone my repo, after use this:

```
docker build -t ${YOUR_REGISTRY}/${YOUR_PROJECT_PATH}:latest

```

# This Image Using

|                | Name          | Version       |
| -------------- |:-------------:| -------------:|
| OS             | Debian        |   Stretch (9) |
| Java           | OpenJDK       |  8 Update 171 |
| .NET Framework | Mono          |    6.4.0.198  |
| .NET SDK       | .NET Core SDK | 2.1 (2.1.301) |
| Sonar Scanner  | CLI           |      4.2      |
| Sonar Scanner  | MS Build      |    4.7.1.2311 |
| NodeJS         | NodeJS        |    12.X       |

# Using Example

Just set $pwd == your working directory

```
docker run --name dotnet-scanner -it --rm -v $(pwd):/project \
  -e PROJECT_KEY=ConsoleApplication1 \
  -e PROJECT_NAME=ConsoleApplication1 \
  -e PROJECT_VERSION=1.0 \
  -e PROJECT_FILE=YourProject.sln
  -e SONAR_VERBOSE=true
  -e HOST=http://localhost:9000 \
  -e LOGIN_KEY=YOUR_SONAR_PROJECT_TOKEN \
  tihoxodka/msbuild-sonar-scanner
  
```

# SSL is a trouble?

NO! Just copy your CA into image or Dockerfile:

```
cp YOUR_CA.crt //usr/local/share/ca-certificates/YOUR_CA.crt
update-ca-certificates

```
