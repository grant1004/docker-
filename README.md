# docker 紀錄使用DOCKER的各種事項  
# windows 10, wsl2, docker desktop, nvidia/cuda:10.1-cudnn7-devel-ubuntu18.04

## 今天利用 docker desktop 的環境建立一個可以使用 GPU 來做 yolo 訓練的環境 

### step1 : docker run --gpus all -v <volume name>:<容器內的映射路徑> --name <container name> -itd <image> 
> docker run --gpus all -v prediction:/home --name yoloenv nvidia/cuda:10.1-cudnn7-devel-ubuntu18.04
>
> -v : 掛載主機的 volume，volume是對於主機的映射資料夾 
>
> --gpus : 使用本機的gpu，後面接gpu的編號(從0開始) all 代表全部 
> 
> -P : 自動設定container對於host的連接埠
> 
> -p 5000:5000 : 手動設定，格式本地的 5000 連接埠映射到容器的 5000 連接埠
> `ip:hostPort:containerPort | ip::containerPort | hostPort:containerPort` 
> * docker port <container name> 查看容器對於host的連接 port *
>
> -d : 在背景執行 \
  -t : start \ 
  -i : 開啟窗口terminal 
#### volume 使用方式 
> `docker volume create <VolName>` : 建立新的保存空間並命名 (可以用-d來指定位置)\
> `docker volume ls ` : 列出本機上所有的volume\
> `docker volume inspect` <VolName> 查看該volume相關\
> `docker volume prune` 刪除所有未被container使用到的volume\
> `docker volume rm <VolName>` 刪除volume\
> creat沒指定位置的話 : 
> 1. win : `\\wsl$\docker-desktop-data\version-pack-data\community\docker\volumes`
> 2. linux :` /var/lib/docker/volumes/`
