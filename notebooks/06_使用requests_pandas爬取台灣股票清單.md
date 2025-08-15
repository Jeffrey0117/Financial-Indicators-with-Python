## 使用 requests + pandas 爬取台灣股票清單

在資料分析與量化交易領域中，取得最新的股票清單是基礎工作之一。這裡我們以台灣上市股票為例，使用 Python 的 `requests` 與 `pandas` 兩個套件，從證交所公開 API 抓取並整理成結構化資料。

---

### 1. 需求背景
- **目標**：取得台灣上市股票（不含上櫃、興櫃）的代碼與名稱。
- **來源**：臺灣證券交易所（TWSE）提供的 CSV / JSON 下載服務。
- **工具**：
  - `requests`：負責發送 HTTP 請求。
  - `pandas`：讀取與處理 CSV 資料。

---

### 2. 安裝套件
如果尚未安裝套件，可執行：
```bash
pip install requests pandas
````

---

### 3. 取得股票清單

臺灣證券交易所的上市股票清單 API：

```
https://isin.twse.com.tw/isin/C_public.jsp?strMode=2
```

此 API 會回傳 HTML 格式的資料，我們可以用 `pandas.read_html` 直接解析。

---

### 4. 範例程式碼

```python
import requests
import pandas as pd

# 目標網址
url = "https://isin.twse.com.tw/isin/C_public.jsp?strMode=2"

# 發送請求
headers = {
    "User-Agent": (
        "Mozilla/5.0 (Windows NT 10.0; Win64; x64) "
        "AppleWebKit/537.36 (KHTML, like Gecko) "
        "Chrome/114.0.0.0 Safari/537.36"
    )
}
resp = requests.get(url, headers=headers)
resp.encoding = "big5"  # TWSE 使用 Big5 編碼

# 解析 HTML 內的表格
dfs = pd.read_html(resp.text)
df = dfs[0]  # 第一個表格

# 清理資料
df.columns = df.iloc[0]  # 第一列作為欄位名稱
df = df.iloc[1:]         # 去掉欄位列
df = df.dropna(how="any")  # 移除空值列

# 過濾出股票代號（代號為數字開頭）
stock_list = df[df["有價證券代號及名稱"].str.match(r"^\d{4}")]

# 分離代號與名稱
stock_list[["代號", "名稱"]] = stock_list["有價證券代號及名稱"].str.split("　", expand=True)

# 選擇需要的欄位
stock_list = stock_list[["代號", "名稱"]]

# 輸出結果
print(stock_list.head())

# 可選：存成 CSV
stock_list.to_csv("twse_stock_list.csv", index=False, encoding="utf-8-sig")
```

---

### 5. 重要注意事項

1. **編碼問題**
   TWSE 網頁使用 Big5 編碼，需設定 `resp.encoding = "big5"` 才能正確解析中文。
2. **HTML 表格解析**
   `pandas.read_html` 可直接解析 HTML 中的 `<table>`，但結果會是 `DataFrame` 列表，需要挑選正確的表格。
3. **資料清理**

   * 原始資料第一列是欄位名稱，需手動設定。
   * 資料中包含分類標題（如「水泥工業」），需要過濾掉。
4. **自動化更新**
   若要定期更新，可搭配排程（Windows Task Scheduler 或 Linux cron）。

---

### 6. 小結

透過 `requests` + `pandas`，我們可以快速從公開 API 取得台灣股票清單並整理成結構化資料。這個方法適合建立股票代號查詢表、批次下載財報或股價資料的前置步驟。

```

---


