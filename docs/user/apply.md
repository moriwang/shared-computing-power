## 提交使用申請
> 上次更新：{docsify-updated} 

選擇一個鏡像，向管理員提出使用申請。獲得賬號密碼與 port 資料後，通過 ssh 登入使用。

### 🔧 所需技能
掌握以下技能可以幫助你更好的使用。
- ssh 遠程連線
- 基本 linux 操作


### ⚠️ 使用 GPU 加速的注意事項

* 請勿刪除或更新內建的 CUDA 環境與深度學習套件如 tensorflow、pytorch 等，否則將導致 GPU 加速失效。

* 需用 GPU 加速的程式，請添加按需使用 GPU 的代碼，避免影響他人正常使用。
    * tensorflow 具體代碼請參考 [https://www.tensorflow.org/guide/gpu](https://www.tensorflow.org/guide/gpu) 添加到程式中。