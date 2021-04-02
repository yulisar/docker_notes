#Change docker image location on Windows docker for desktop:

The WSL 2 docker-desktop-data vm disk image would normally reside in: 

```%USERPROFILE%\AppData\Local\Docker\wsl\data\ext4.vhdx```

1. List existing WSL:

```wsl --list -v```

You should be able to see, make sure the STATE for both is Stopped.
```
  NAME                   STATE           VERSION
* docker-desktop         Stopped         2
  docker-desktop-data    Stopped         2
  
```  

2. Export docker-desktop-data into a file

```wsl --export docker-desktop-data "D:\Docker\wsl\data\docker-desktop-data.tar"```

3. wsl --import docker-desktop-data "D:\Docker\wsl\data" "D:\Docker\wsl\data\docker-desktop-data.tar" --version 2

4. Unregister docker-desktop-data from wsl, note that after this, your ext4.vhdx file would automatically be removed (so back it up first if you have important existing image/container):

Start the Docker Desktop again and it should work

You may delete the D:\Docker\wsl\data\docker-desktop-data.tar file (NOT the ext4.vhdx file) if everything looks good for you after verifying.


https://stackoverflow.com/questions/62441307/how-can-i-change-the-location-of-docker-images-when-using-docker-desktop-on-wsl2
