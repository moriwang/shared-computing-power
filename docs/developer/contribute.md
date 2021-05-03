
## 加入共享計畫
> 上次更新：{docsify-updated} 

### 添加新的 GPU 算力
如果購置新的機器或者有限制的 GPU 算力，可以通過以下指南加入本計畫。

操作系統版本建議 Ubuntu 18.04 LTS 。確保已安裝 Nvidia Graphic Driver 與 Docker > 19.03。
ubuntu 重啟後驅動遺失。
表現為 `nvidia-smi` 提示

https://download.nvidia.com/XFree86/Linux-x86_64/460.32.03/README/installdriver.html


#### 安装 Nvidia Graphic Driver
> 下载地址：[https://www.nvidia.com/Download/index.aspx?lang=en-us](https://www.nvidia.com/Download/index.aspx?lang=en-us)

選擇符合的顯卡型號，作業系統選擇 `Linux 64-bit`，下載類型選擇 `Linux Long Lived`。

安裝指令
```bash
sudo bash NVIDIA-Linux-x86_64-460.32.03.run
```

#### 安裝 Docker
> 參考：[https://docs.docker.com/engine/install/ubuntu/](https://docs.docker.com/engine/install/ubuntu/)

非 root 用戶，運行以下指令即可操作 docker。
``` bash
sudo groupadd docker
sudo usermod -aG docker $USER
```

### 招募管理員

管理員需通過 ssh 在 GPU server 中按照使用者申請創建 container，並在 Portainer 中管理使用者賬號、指派 container 權限。平時需進行 NTPU-MIS 鏡像製作與操作手冊維護。

**所需技能**

- 熟悉 linux 指令操作。
- 熟悉 docker 指令。
- 熱於助人。