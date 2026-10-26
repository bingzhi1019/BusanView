# BusanView

旅行行程入口網站，部署在 GitHub Pages。目前有兩個已完成的旅程：釜山與大阪。

## 網站結構

```text
index.html       旅程入口頁
README.md        專案說明
shared/          共用資源
  apple-touch-icon.png
busan/           釜山旅程
  index.html
  busan.mp3
osaka/           大阪旅程
  index.html
```

使用者先進入 `index.html`，再從旅程卡片選擇想查看的目的地。兩個旅程頁可以各自維持適合該行程的版面與互動，不需要強迫使用相同的內容格式。

## GitHub Pages

在 repository 的 **Settings → Pages** 設定：

- Source：Deploy from a branch
- Branch：`main`
- Folder：`/ (root)`

網站網址：

```text
https://bingzhi1019.github.io/BusanView/
```

請以 GitHub repository 的 Pages 設定為準。

## 本機預覽

建議從 repository 根目錄啟動靜態伺服器：

```bash
python3 -m http.server 8000
```

然後開啟：

```text
http://localhost:8000/
```

## 新增未來旅程

新增城市時，採用「一個入口頁＋一個獨立旅程頁」：

1. 建立城市資料夾，例如 `kyoto/`。
2. 在資料夾內新增 `kyoto/index.html`。
3. 在根目錄 `index.html` 的 `.trip-grid` 新增一張旅程卡片。
4. 將卡片的 `href` 指向 `kyoto/index.html`。
4. 更新卡片上的國家、日期、旅程名稱與簡介。
6. 若有該城市專屬音樂、圖片或其他資產，放在該城市資料夾內並使用相對路徑。
7. 共用資產放在 `shared/`，並從城市頁使用 `../shared/資產檔名`。
8. 在 GitHub Pages 實際網址測試入口與旅程頁連結。

範例：

```html
<a class="trip-card" href="kyoto/">
  <div class="trip-flag">🇯🇵</div>
  <div class="trip-name">京都三天兩夜</div>
  <div class="trip-meta">日本・2027 / 03 / 01 ～ 2027 / 03 / 03</div>
  <p class="trip-description">京都寺院、街道與美食行程。</p>
  <span class="trip-action">查看京都行程 →</span>
</a>
```

不要複製 `index.html` 當成新入口；`index.html` 永遠只負責選擇旅程，新的完整行程應放在自己的 HTML 檔案中。
