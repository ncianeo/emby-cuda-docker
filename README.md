1. Install nvidia-docker
2. Run following line
~~~sh
docker run -d --restart=always \
     --runtime=nvidia \ 
     --cpus=<NUMBER_OF_CPU_CORES_TO_USE> \
     --cpuset-cpus="<SPECIFIC_CPUS_TO_USE>" \
     -e <NVIDIA_VISIBLE_DEVICES>=<SPECIFIC_GPUS_TO_USE>\
     -e NVIDIA_DRIVER_CAPABILITIES=compute,video,utility\
     -v YOUR_MEDIA_PATH:/data \
     -v YOUR_EMBY_CONFIG_PATH:/config \
     -p 8096:8096 \
     -p 8920:8920 \
     --name <CONTAINER_NAME> \
     emby/embyserver:3.6.0.56
~~~

For example,
~~~sh
docker run -d --restart=always \
     --runtime=nvidia \ 
     --cpus=4 \
     --cpuset-cpus="12-15" \
     -e NVIDIA_VISIBLE_DEVICES=0\
     -e NVIDIA_DRIVER_CAPABILITIES=compute,video,utility\
     -v /HDD:/HDD \
     -v /SSD/emby-config:/config \
     -p 8096:8096 \
     -p 8920:8920 \
     --name emby-cuda-server \
     emby/embyserver:3.6.0.56
~~~

emby 3.6.0.56 seems to be the latest version which supports nvenc without premiere account
