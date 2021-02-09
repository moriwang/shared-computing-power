## 更新記錄
> 上次更新：{docsify-updated} 

#### 2020-12-29
- 解決 ssh 登入環境變量丟失的問題
- 新增 `ntpu-mis-pytorch:20.11-py3` 鏡像
    * 已 `nvcr.io/nvidia/pytorch:20.11-py3` 為底包。
- 更新 `ntpu-mis-tensorflow:20.10-tf1-py3` 鏡像

#### 2020-11-04

- 新增 `ntpu-mis-tensorflow:20.10-tf1-py3` 鏡像
    * 以 `nvcr.io/nvidia/tensorflow:20.10-tf1-py3` 為底包。
- 添加 ssh、screen、zsh、git 套件。
- 調整語言編碼為 `en_US.UTF-8` ，解決無法顯示中文字的問題。
- ssh 默認登入密碼為 `goodgoodstudy`。
- BUG: 無法使用 -it 模式運行，影響範圍：快速檢測鏡像可用性。