## VS Code 整合開發環境設定

Visual Studio Code（簡稱 VS Code）是目前最受歡迎的跨平台程式編輯器之一，對 Python 開發者來說，它提供了輕量、擴充性強、功能完善的開發體驗。本章將介紹如何將 VS Code 設定成完整的 Python 開發環境。

---

### 1. 安裝 VS Code
1. 前往官方網站下載並安裝：
   - [https://code.visualstudio.com/](https://code.visualstudio.com/)
2. 安裝過程中建議勾選：
   - 將 VS Code 加入系統路徑（PATH）
   - 在右鍵選單加入「Open with Code」選項

---

### 2. 安裝 Python 擴充套件
1. 開啟 VS Code，按下 `Ctrl + Shift + X` 開啟擴充套件視窗。
2. 搜尋並安裝：
   - **Python**（Microsoft 官方提供，支援語法高亮、Lint、偵錯）
   - **Pylance**（提升 IntelliSense 自動補全與型別提示速度）
   - **Jupyter**（如需在 VS Code 內直接跑 `.ipynb` 筆記本）
3. 安裝完成後，重新啟動 VS Code 讓擴充套件生效。

---

### 3. 設定 Python 解譯器（Interpreter）
1. 按下 `Ctrl + Shift + P` 開啟命令面板。
2. 搜尋並選擇 **Python: Select Interpreter**。
3. 選擇對應專案的虛擬環境，例如：
```

.venv\Scripts\python.exe

````
4. 這樣 VS Code 就會使用該環境來執行與偵錯。

---

### 4. 建立並使用虛擬環境
在專案資料夾下建立虛擬環境：
```bash
python -m venv .venv
````

啟用虛擬環境後，安裝所需套件並透過 `requirements.txt` 管理（詳見前一章）。

---

### 5. 偵錯設定（launch.json）

VS Code 偵錯功能透過 `.vscode/launch.json` 控制，可以自訂啟動參數與環境變數。

建立方式：

1. 按下 `F5` 或點擊左側「執行與偵錯」圖示。
2. 選擇 **Python File**。
3. VS Code 會自動在專案建立 `.vscode/launch.json`，可自行修改：

```json
{
    "version": "0.2.0",
    "configurations": [
        {
            "name": "Python: Current File",
            "type": "python",
            "request": "launch",
            "program": "${file}",
            "console": "integratedTerminal"
        }
    ]
}
```

---

### 6. 自動格式化與程式檢查

建議安裝以下工具，確保程式碼整潔：

```bash
pip install black flake8
```

在 VS Code 設定檔（`settings.json`）加入：

```json
{
    "python.formatting.provider": "black",
    "editor.formatOnSave": true,
    "python.linting.flake8Enabled": true
}
```

---

### 7. 推薦延伸工具

* **GitLens**：加強 Git 版本控制
* **Code Runner**：快速執行程式碼片段
* **Prettier**（前端專案同時使用時）

---

### 小結

透過以上步驟，VS Code 將成為一個輕量但功能完整的 Python 整合開發環境。從語法高亮、虛擬環境管理、偵錯，到自動化程式碼格式化，都能在同一個編輯器內完成，大幅提升開發效率。

```

---


