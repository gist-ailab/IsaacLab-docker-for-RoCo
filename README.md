```bash
# Install Docker and nvidia-container-toolkit

# Also, Turn on the Foward X11
e.g.,
Host demo-com-raeyo
    HostName 172.27.183.203
    User demo-raeyo
    ForwardX11 yes
    ForwardX11Trusted yes
# or
export DISPLAY=:1

# First, clone the repository
git clone https://github.com/gist-ailab/IsaacLab-docker-for-RoCo.git

# Second, clone the RoCo repository
git clone https://github.com/rocochallenge/gearboxAssembly.git

# fix the user's autentication for docker
#도커 그룹에 유저 추가
$ sudo usermod -aG docker [user name]

#도커 재시작
$ sudo systemctl restart docker

#현재 사용자 재로그인
$ sudo su - [user name]

# Move into the isaaclab folder
cd IsaacLab-docker-for-RoCo

# Download the docker image.tar and import it
cp /ailab_mat/personal/yeonguk_yu/isaac-lab-base\:v2.tar ./
docker import isaac-lab-base\:v2.tar - isaac-lab-base:v2

# Launch the container in detached mode
# We don't pass an image extension arg, so it defaults to 'base'
./docker/container.py start

# If we want to add .env or .yaml files to customize our compose config,
# we can simply specify them in the same manner as the compose cli
# ./docker/container.py start --file my-compose.yaml --env-file .env.my-vars

# Enter the container
# We pass 'base' explicitly, but if we hadn't it would default to 'base'
./docker/container.py enter
```

After enter the container
```bash
#follow the installation and manual from https://github.com/rocochallenge/gearboxAssembly.git

# IF you have trouble in using git lfs, use the zip file from here
cp /ailab_mat/personal/yeonguk_yu/gearboxAssembly.zip
```
