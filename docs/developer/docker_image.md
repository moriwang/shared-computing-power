> 上次更新：{docsify-updated} 

本章節介紹了如何從零開始製作一個鏡像。

> 此操作具有一定的難度和風險，請在自己的電腦上測試完成後，再新增於 GPU Server。

### Pull 官方鏡像

從 Nvidia NGC 下載需要的鏡像。以 tensorflow 為例：

[TensorFlow Release Notes :: NVIDIA Deep Learning Frameworks Documentation](https://docs.nvidia.com/deeplearning/frameworks/tensorflow-release-notes/index.html)

```bash
docker pull nvcr.io/nvidia/tensorflow:20.10-tf1-py3
```

### 製作 Dockerfile

可以參考下面這份 Dockerfile 模板。

```docker
# Maintainer zesheng <s710736501@gm.ntpu.edu.tw>
# Version 2020-12-28

# 替換成需要的鏡像
FROM nvcr.io/nvidia/tensorflow:20.10-tf1-py3

# 更改歡迎語句，Tag 保持與 Nvidia 原始鏡像相同
RUN echo "Current image: ntpu-mis-tensorflow:20.10-tf1-py3" > /etc/motd

# 以下內容勿動，除非你能理解
# Install packages
RUN apt-get update && apt-get install -y --no-install-recommends \
        openssh-server \
        screen \
        git \
        zsh \
        locales \
    && \
    rm -rf /var/lib/apt/lists/

# Set language profile
RUN sed -i 's/# en_US.UTF-8/en_US.UTF.8/g' /etc/locale.gen && \
    locale-gen && \
    echo "export LANG=en_US.UTF-8" >> /etc/profile
ENV LANG=en_US.UTF-8 \
    LC_ALL=en_US.UTF-8

# Set ssh-server
RUN mkdir /var/run/sshd && \
    echo 'root:goodgoodstudy' | chpasswd && \
    sed -i 's/#*PermitRootLogin prohibit-password/PermitRootLogin yes/g' /etc/ssh/sshd_config && \
    # SSH login fix. Otherwise user is kicked off after login
    sed -i 's@session\s*required\s*pam_loginuid.so@session optional pam_loginuid.so@g' /etc/pam.d/sshd

# 解決 ssh 登入環境變量丟失的問題
RUN env >> /etc/environment
RUN echo "export PATH=$PATH" >> /etc/profile

EXPOSE 22
CMD ["/usr/sbin/sshd", "-D"]
```

### build 鏡像

在 Dockerfile 相同目錄下，運行下面的指令 build 鏡像。

鏡像名稱請使用 `ntpu-mis` 開頭。

```bash
docker build -t ntpu-mis-tensorflow:20.10-tf1-py3 .
```

### 檢查鏡像

**選項一**

在 Portainer 內檢查。

**選項二**

在終端機內輸入以下指令，查看是否新建成功。

```bash
docker image ls
```

### 測試 GPU 加速

創建測試用 container。

```bash
docker run --name="test-image" \
--shm-size=1g --ulimit memlock=-1 \
--gpus all \
-d \
ntpu-mis-tensorflow:20.10-tf1-py3
```

```bash
docker exec test-image python test-gpu.py

docker container stop test-image
docker container rm  test-image
```