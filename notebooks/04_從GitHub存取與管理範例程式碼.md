## 從 GitHub 存取與管理範例程式碼

在學習 Python 或進行專案開發時，GitHub 是取得範例程式碼與開源專案的最佳來源之一。本章將介紹如何從 GitHub 存取程式碼，並用 Git 工具管理它，讓你可以隨時更新、修改與貢獻。

---

### 1. 什麼是 Git 與 GitHub？
- **Git**：一種版本控制系統（VCS），用來追蹤檔案的變化，方便協作開發。
- **GitHub**：基於 Git 的線上平台，提供程式碼託管、協作與社群功能。

---

### 2. 安裝 Git
1. 前往官方網站下載安裝：
   - [https://git-scm.com/](https://git-scm.com/)
2. 安裝後開啟終端機（cmd、PowerShell 或 VS Code 終端機）輸入：
   ```bash
   git --version
````

若顯示版本號，即代表安裝成功。

---

### 3. 從 GitHub 下載專案（Clone）

1. 找到想要下載的 GitHub 專案，點擊 **Code** 按鈕，複製 HTTPS 或 SSH 連結。
2. 在終端機執行：

   ```bash
   git clone https://github.com/username/repo-name.git
   ```
3. 完成後會在當前資料夾生成一個與專案名稱相同的資料夾，內含完整程式碼與版本紀錄。

---

### 4. 更新範例程式碼（Pull）

若該專案持續更新，可以用以下指令同步：

```bash
cd repo-name
git pull
```

這會將遠端的新版本合併到本地端。

---

### 5. 建立自己的版本（Fork）

若想在不影響原始專案的情況下修改程式碼，可以：

1. 在 GitHub 專案頁面點擊 **Fork**，建立屬於自己的複本。
2. Clone 你的複本到本地端：

   ```bash
   git clone https://github.com/your-username/repo-name.git
   ```

---

### 6. 修改與提交變更（Commit & Push）

在本地端修改程式碼後：

```bash
git add .
git commit -m "修改範例程式碼"
git push
```

這會將變更上傳到你自己的 GitHub 儲存庫。

---

### 7. 與專案貢獻者同步（Upstream）

若你 Fork 的專案有原作者更新，需與原專案同步：

```bash
git remote add upstream https://github.com/original-username/repo-name.git
git fetch upstream
git merge upstream/main
```

或使用：

```bash
git pull upstream main
```

確保你的版本保持最新。

---

### 8. 常見情境

* **只想下載一次範例** → 直接 `git clone` 或下載 ZIP。
* **想長期追蹤更新** → `git clone` 後定期 `git pull`。
* **想改成自己的版本** → Fork 後修改並 Push。
* **想貢獻程式碼** → Fork → 修改 → Pull Request。

---

### 小結

透過 GitHub，不僅能取得範例程式碼，還能參與專案開發。養成用 Git 管理程式碼的習慣，能讓你的專案更有條理，並隨時與最新版本保持同步。

```

---


