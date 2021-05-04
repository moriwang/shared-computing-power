> 上次更新：{docsify-updated} 

### 申請條件
國立台北大學資管所學生，如有進行深度學習研究需求，皆可申請。

掌握以下技能可以幫助你更好的使用。
- ssh 遠程連線，[教學](how-to-use.md)
- 基本 linux 操作，如 `cd`、`ls` 等。

### 提交使用申請
> 具體申請方式與內容再請學弟妹商議決定。

在提交使用申請前，請思考以下問題。
1. 你的研究是否需要使用 GPU。如果是，請繼續參考第二條。
2. 你需要使用的 GPU Server。可用的 GPU Server 列表可以進入[這裡](overview.md)查看。
3. 用戶資料夾名稱，用於存放並持久化你的所有檔案：原始碼，資料集等。
4. 預計使用時間。

管理員根據使用申請，幫忙創建 Docker 容器，並將 ssh 連線端口提供給使用者。

### 公平使用
為維護大家順暢使用 GPU Server，請仔細閱讀以下內容。
#### 使用 GPU 加速的注意事項

* 請勿刪除或更新內建的 CUDA 環境與深度學習套件如 tensorflow、pytorch 等，否則將導致 GPU 加速失效。
* 需用 GPU 加速的程式，請添加按需使用 GPU 的代碼，避免影響他人正常使用。
    * tensorflow 具體代碼請參考 [https://www.tensorflow.org/guide/gpu](https://www.tensorflow.org/guide/gpu) 添加到程式中。