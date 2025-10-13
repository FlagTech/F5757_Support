# 旗標科技《Claude Code Vibe Coding 開發手冊》服務專區

## 第 1 章 Claude Code 簡介與安裝


### 1-2 在 Windows 安裝 Claude Code

- 安裝 scoop：

    允許執行從網路下載具有數位簽章的 PowerShell 腳本：

    ```
    Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser
    ```

    安裝 scoop：

    ```
    Invoke-RestMethod -Uri https://get.scoop.sh | InvokeExpression
    ```

- 安裝 git 工具：

    ```
    scoop install git
    ```

    確認 git-bash 路徑：

    ```
    where.exe bash
    ```

    > [!TIP]
    > 如果想要直接在命令行設定 `CLAUDE_CODE_GIT_BASH_PATH` 環境變數，可以如下下達指令：
    >
    > ```
    >  [Environment]::SetEnvironmentVariable("CLAUDE_CODE_GIT_BASH_PATH", "$home\scoop\shims\bash.exe", "user")
    > ```

- 安裝原生版本的 Claude Code

    ```
    irm https://claude.ai/install.ps1 | iex
    ```

    > [!TIP]
    > 如果要透過命令列直接設定 PATH 環境變數，可如下下達指令：
    > 
    > ```
    > [Environment]::SetEnvironmentVariable( "PATH", "$home\.local\bin" + [Environment]::GetEnvironmentVariable('PATH', 'user'), 'user')
    > ```

### 1-3 在 WSL（Linux/macOS）中安裝 Claude Code

- 安裝 WSL（macOS 請略過）

    ```
    wsl ––install
    ```

    更新套件資料庫：

    ```
    sudo apt update
    ```

    更新套件：

    ```
    sudo apt upgrade
    ```

- 安裝原生版本的 Claude Code

    ```
    curl -fsSL https://claude.ai/install.sh | bash
    ```

    更新 `PATH` 環境變數：

    - Linux

        ```
        echo 'export PATH="$HOME/.local/bin:$PATH"' >> ~/.bashrc && source ~/.bashrc
        ```
    - macOS

        ```
        echo 'export PATH="$HOME/.local/bin:$PATH"' >> ~/.zshrc && source ~/.zshrc
        ```
### 1-4 安裝後續章節所需的工具

#### Windows

- 安裝 Visual Studio Code：

    要先加入 extras 儲存庫：

    ```
    scoop bucket add extras
    ```

    再安裝 VSCode：

    ```
    scoop install vscode
    ```

    安裝 WSL 延伸模組：

    ```
    code --install-extention ms-vscode-remote.remote-wsl
    ```
- 安裝 Node.js

    先安裝 nvm：

    ```
    scoop install nvm
    ```

    檢視 nvm 版本：

    ```
    nvm --version
    ```

    安裝 Node.js 最新版：

    ```
    nvm install node
    ```

    啟用最新版本的 Node.js：

    ```
    nvm use node
    ```

    檢視 Node.js 版本：

    ```
    node --version
    ```

- 安裝 Python 環境管理工具 -- uv

    ```
    scoop install uv
    ```

#### WSL/Linux/macOS

- 安裝 Homebrew 套件管理工具

    ```
    /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
    ```

    修改設定檔：

    ```
    echo >> $HOME/.bashrc
    ```

    ```
    echo 'eval "$(/home/linuxbrew/.linuxbrew/bin/brew shellenv)"' >> $HOME/.bashrc
    ```

    ```
    eval "$(/home/linuxbrew/.linuxbrew/bin/brew shellenv)"
    ```

    檢視 Homebrew 版本：

    ```
    brew ––version
    ```

- 安裝 Visual Studio Code（WSL 請略過）

    - macOS：
    
        ```
        brew install --cask visual-studio-code
        ```
    - Ubuntu：

        ```
        sudo snap install --classic code
        ```

- 安裝 Node.js

    - 安裝 nvm：

        ```
        brew install nvm
        ```

        開啟 VSCode 修改設定檔：

        ```
        code ~/.bashrc
        ```

        要加入設定檔的內容：

        ```
        export NVM_DIR="$HOME/.nvm"
        [ -s "/home/linuxbrew/.linuxbrew/opt/nvm/nvm.sh" ] && \. "/home/linuxbrew/.linuxbrew/opt/nvm/nvm.sh"
        [ -s "/home/linuxbrew/.linuxbrew/opt/nvm/etc/bash_completion.d/nvm" ] && \. "/home/linuxbrew/.linuxbrew/opt/nvm/etc/bash_completion.d/nvm"
        ```

        修改設定檔後讓設定檔生效：

        ```
        source ~/.bashrc
        ```
    - 安裝 Node.js

        ```
        nvm install node
        ```

        檢視版本：

        ```
        node ––version
        ```

    - 安裝 Python 環境管理工具--uv

        ```
        brew install uv
        ```

#### 透過 Node.js 環境安裝 Claude Code

> [!TIPS]
> 除非安裝原生版本有問題，否則不需要在安裝 Node.js 版本的 Claude Code。

```
npm install -g @anthropic-ai/claude-code
```

