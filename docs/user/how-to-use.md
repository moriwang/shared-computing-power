## 基礎使用指南
> 上次更新：{docsify-updated} 

### 使用 ssh 連線

密碼默認值為 `goodgoodstudy` ，可進入主機後，自行修改。

```bash
ssh root@<GPU_SERVER_IP> -p<SSH_PORT>

## 範例 
## GPU_SERVER_IP = 120.126.146.97 
## SSH_PORT = 32771
ssh root@120.126.146.97 -p32771
```

#### 推荐程式
- Mac 用戶：(iterm2)[https://iterm2.com] 或自帶終端機。
- Windows 用户：(Windows Terminal)[https://www.microsoft.com/zh-tw/p/windows-terminal/9n0dx20hk701?rtc=1]。

### 安裝額外的套件

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



### 配置 ssh 免密連線

配置 ssh 登入時無需輸入密碼，不用一直打 `goodgoodstudy`。

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
