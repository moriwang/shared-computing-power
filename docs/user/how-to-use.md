> 上次更新：{docsify-updated} 

### 使用 ssh 連線操作遠端主機
想要成為一位煉丹大師，通過 ssh 連線操作遠端主機是通往成功的第一步！

#### 第一步、獲取 Docker 容器 IP 與連線端口 

**獲取方式**
- 向管理員提交[使用申請](user/apply.md)

- 自己創建 Docker 容器
  - > ⚠️ 請嚴格按照教學步驟操作，請勿進行額外的操作。

#### 第二步、使用 ssh 連線指令進入容器

> Mac 用戶：建議使用 [iterm2](https://iterm2.com) 或系統內建終端機。
> 
> Windows 用户：建議使用 [Windows Terminal](https://www.microsoft.com/zh-tw/p/windows-terminal/9n0dx20hk701?rtc=1)。

密碼默認值為 `goodgoodstudy` ，可進入 Docker 容器後，可自行修改（這個請你們自己 Google 吧）。

```bash
ssh root@<GPU_SERVER_IP> -p<SSH_PORT>

## 範例 
## GPU_SERVER_IP = 120.126.146.97 
## SSH_PORT = 32771
ssh root@120.126.146.97 -p32771
```

第一次連線會提示類似以下內容，請輸入 `yes`。
```bash
ECDSA key fingerprint is SHA256:eVIps0RHh6slPwJkJF127ssW8nMvwK938aMXhaWRE1M.
Are you sure you want to continue connecting (yes/no/[fingerprint])?
```

當終端機顯示如下內容時，代表已成功進入。

```
Welcome to Ubuntu 18.04.5 LTS (GNU/Linux 4.15.0-132-generic x86_64)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/advantage
This system has been minimized by removing packages and content that are
not required on a system that users do not log into.

To restore this content, you can run the 'unminimize' command.
Current image: ntpu-mis-tensorflow:20.10-tf1-py3
Last login: Tue May  4 12:42:38 2021 from 219.91.6.24
root@296e02bfc93d:~#
```

#### 第三步、安裝額外的套件

NTPU-MIS 鏡像已包含基本的套件，如需安裝其他套件，請按下面的步驟操作。

**linux 套件**

```bash
apt-get update
apt-get install <your-package1> <your-pacakge2>
```

**python 套件**

```bash
pip install <your-package1> <your-pacakge2>
```


#### 進階：配置 ssh 免密連線

配置 ssh 登入時無需輸入密碼，不用一直打 `goodgoodstudy`。在使用 VSCode 開發時，尤其方便。

首先，在你的電腦上產生公鑰和私鑰。

```bash
ssh-keygen -t rsa -P ""
```

按 `Enter`，成功的話，會看到類似的信息。
```
Generating public/private rsa key pair.
Enter file in which to save the key (/home/username/.ssh/id_rsa): 
Enter passphrase (empty for no passphrase): 
Enter same passphrase again: 
Your identification has been saved in /home/username/.ssh/id_rsa.
Your public key has been saved in /home/username/.ssh/id_rsa.pub.
The key fingerprint is:
SHA256:Up6KjbnEV4Hgfo75YM393QdQsK3Z0aTNBz0DoirrW+c username@your-computer
The key's randomart image is:
+---[RSA 2048]----+
|    .      ..oo..|
|   . . .  . .o.X.|
|    . . o.  ..+ B|
|   .   o.o  .+ ..|
|    ..o.S   o..  |
|   . %o=      .  |
|    @.B...     . |
|   o.=. o. . .  .|
|    .oo  E. . .. |
+----[SHA256]-----+
```

產生的公鑰和私鑰位於 `~/.ssh/` 下，下一步將其傳送到目標主機上。

```bash
ssh-copy-id -i ~/.ssh/id_rsa.pub root@<GPU_SERVER_IP> -p<SSH_PORT>
```

之後使用 ssh 連線就無需再輸入密碼了，更多資料請參考 [ssh-keygen - Generate a New SSH Key](https://www.ssh.com/ssh/keygen/)。
