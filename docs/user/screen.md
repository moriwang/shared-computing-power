## 使用 Screen 煉丹
> 上次更新：{docsify-updated} 


本說明旨在講解訓練模型時最常用的指令，在 5 分鐘內快速上手。


### 創建 Screen 會話

``` bash
screen -S <your-screen-name>
```

### 退出 Screen 會話
如果程式正常跑起來了，直接把終端機關掉就可以了。

在當前 Screen 中，先按 `Ctrl + A` 組合鍵，鬆開再按 `D` 鍵，就可以回到 ssh 界面了。


### 重新進入 Screen 會話

```bash
screen -ls
screen -r <your-screen-name>
```


### 保存輸出到文件
在 screen 配置文件 `/etc/screenrc` 最後添加一行，指定保存日誌的路徑：

`logfile /tmp/screenlog_%t.log`

創建 screen 時，加上 `-L` 表示要輸出日誌到文件，使用 `-t` 指定路徑中的 `%t`, 

例如：指定 `file_%t` 为 bert，则输出文件为 `/tmp/sceenlog_bert.log`
```bash
screen -L -t <file_%t> -S <your-screen-name>
```
