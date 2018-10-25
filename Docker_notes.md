# Start docker on Windows
### Run the following as admin in Powershell

```
net stop com.docker.service
net start com.docker.service
& 'C:\Program Files\Docker\Docker\Docker for Windows.exe'
```

-----------------------------

# Build images from Dockerfile

+ `docker build -t mnh/ubuntu_python3 .`

-----------------------------

# Run containers from images

+ `docker run -it --rm --mount type=bind,source=c:\Massimo\Docker_stuff,target=/data mnh/ubuntu_python3`
