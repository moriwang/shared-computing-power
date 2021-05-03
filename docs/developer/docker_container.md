## 管理容器
> 上次更新：{docsify-updated} 

### 新建帶 GPU 的容器
替換 `<your-name>` 爲你的名字。
```
docker run --name="<your-name>" \
--shm-size=1g --ulimit memlock=-1 \
--gpus all \
-d \
-P \
--restart=always \
-v /home/mis/Documents/<your-name>:/root/<your-name> \
ntpu-mis-tensorflow:20.10-tf1-py3
```

### 新建不帶 GPU 的容器
替換 `<your-name>` 爲你的名字。
```
docker run --name="<your-name>" \
--shm-size=1g --ulimit memlock=-1 \
-d \
-P \
--restart=always \
-v /home/mis/Documents/<your-name>:/root/<your-name> \
ntpu-mis-tensorflow:20.10-tf1-py3
```

### 使用容器
進入 `http://120.126.146.97:9000` 後點擊帶鯨魚圖案的列表，再點擊左側的 Containers，查看剛剛創建的 ssh port(22)。