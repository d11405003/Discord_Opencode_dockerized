# OpenCode Dockerized - Discord Remote Control

在 Docker 容器中執行 OpenCode，並透過 Discord 遠端控制。

## 功能特色

- **Docker 隔離執行** - 安全地在容器中執行 OpenCode
- **Discord 遠端控制** - 從手機、平板或其他電腦透過 Discord 控制 OpenCode
- **支援語音訊息** - 傳送語音訊息，自動轉文字並處理
- **團隊協作** - 團隊成員可在 Discord 中觀看 AI 編碼過程

## 快速開始

### 第一次設定

```bash
# 1. 執行初始化腳本
./setup.sh

# 2. 建構 Docker 映像
./opencode-dockerized.sh build

# 3. 設定 Discord 機器人
./opencode-dockerized.sh discord setup

# 4. 啟動 Discord 機器人
./opencode-dockerized.sh discord start
```

### Discord 指令

機器人啟動後，在 Discord 中使用：

```bash
# 註冊專案路徑
/setpath alias:myproject path:/workspace

# 綁定頻道
/use alias:myproject

# 傳送指令給 AI
/opencode prompt:幫我新增一個登入功能

# 啟用對話模式（無需輸入斜線指令）
/code

# 建立 Git Worktree
/work branch:feature/new-feature description:新功能開發
```

## 指令總覽

### OpenCode 指令

```bash
./opencode-dockerized.sh run [DIR]      # 執行 OpenCode
./opencode-dockerized.sh auth           # OpenCode 認證
./opencode-dockerized.sh build           # 建構 Docker 映像
./opencode-dockerized.sh update         # 更新 OpenCode
./opencode-dockerized.sh version        # 顯示版本
./opencode-dockerized.sh config show    # 顯示設定
./opencode-dockerized.sh clean          # 清除 Docker 映像
```

### Discord 機器人指令

```bash
./opencode-dockerized.sh discord setup       # 互動式設定精靈
./opencode-dockerized.sh discord start       # 啟動機器人
./opencode-dockerized.sh discord stop        # 停止機器人
./opencode-dockerized.sh discord deploy     # 部署斜線指令
./opencode-dockerized.sh discord config     # 顯示機器人設定

# 允許名單管理
./opencode-dockerized.sh discord allow add <user_id>
./opencode-dockerized.sh discord allow remove <user_id>
./opencode-dockerized.sh discord allow list
```

## 環境變數

```bash
DRY_RUN=true ./opencode-dockerized.sh run   # 顯示 Docker 指令但不執行
```

##  Volume 掛載

| 主機路徑 | 容器路徑 | 模式 | 用途 |
|---------|---------|------|------|
| `$PROJECT_DIR` | `/workspace` | rw | 專案檔案 |
| `~/.config/opencode/` | `/home/coder/.config/opencode/` | ro | OpenCode 設定 |
| `~/.local/share/opencode/` | `/home/coder/.local/share/opencode/` | rw | 認證、工作階段 |
| `~/.cache/opencode/` | `/home/coder/.cache/opencode/` | rw | 快取 |
| `~/.remote-opencode/` | `/home/coder/.remote-opencode/` | rw | Discord 機器人設定 |

## 感謝作者

本專案基於以下兩個專案：

1. **[opencode-dockerized](https://github.com/glennvandevelde/opencode-dockerized)**
   - 作者：[Glenn Vandevelde](https://github.com/glennvandevelde)
   - 描述：Docker 隔離執行 OpenCode 的包裝脚本

2. **[remote-opencode](https://github.com/RoundTable02/remote-opencode)**
   - 作者：[RoundTable02](https://github.com/RoundTable02)
   - 描述：Discord 機器人，用於遠端存取 OpenCode CLI

## 授權

MIT License - 詳見 [LICENSE](LICENSE) 檔案

## 相關連結

- [OpenCode 文件](https://opencode.ai/docs)
- [OpenCode GitHub](https://github.com/sst/opencode)
- [remote-opencode GitHub](https://github.com/RoundTable02/remote-opencode)
- [opencode-dockerized GitHub](https://github.com/glennvandevelde/opencode-dockerized)
