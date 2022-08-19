# docker 紀錄使用DOCKER的各種事項  
# windows 10, wsl2, docker desktop

## 今天利用 docker desktop 的環境建立一個可以使用 GPU 來做 yolo 訓練的環境 

### step1 : docker run --gpus all -v <volume name>:<容器內的映射路徑> --name <container name> <image> 
> docker run --gpus all -v prediction:/home --name yoloenv 10.1-cudnn7-devel-ubuntu18.04
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
> -d : 在背景執行
