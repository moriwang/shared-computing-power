## 管理容器
> 上次更新：{docsify-updated} 


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