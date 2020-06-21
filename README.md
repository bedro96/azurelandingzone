# azurelandingzone


- CentOS VM
신규 CentOS 7.5 VM 설치
https://github.com/bedro96/tf-centos
 
- CentOS VM에 Docker 설치하기
$ sudo yum install -y yum-utils

$ sudo yum-config-manager \
    --add-repo \
    https://download.docker.com/linux/centos/docker-ce.repo
    
$ sudo yum install docker-ce docker-ce-cli containerd.io
$ sudo systemctl start docker
$ sudo usermod -aG docker $USER

logoff and login again.
    
- rover 
https://hub.docker.com/r/aztfmod/rover/tags
```
docker pull docker pull aztfmod/rover:2005.1510
```

- landing zone
git clone https://github.com/Azure/caf-terraform-landingzones.git

- docker image run with volume mount
```
docker run -v /home/centadmin/caf-terraform-landingzones/landingzones:/tf/caf/landingzones -it --name rover aztfmod/rover:2005.1510
```

-- run this command
rover login microsoft.com 05be085b-86ea-4336-addc-38fd56051a9e


