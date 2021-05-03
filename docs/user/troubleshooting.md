## 故障排除
> 上次更新：{docsify-updated} 

### 🤯 不小心玩壞了？

進入 Portainer，進入你的 container，點擊 `Recreate` 即可恢復初始狀態。如果不小心誤刪了 container，請聯繫管理員重新創建。

### Docker 全都停止了，也無法重新啟動

首先確認 GPU 驅動是否工作正常。管理員通過 22 端口 ssh 進入主機後，輸入 `nvidia-smi` 指令檢查，如沒有顯示以下畫面，則需重新安裝 GPU 驅動。

