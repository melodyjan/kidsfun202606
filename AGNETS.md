# 小樹苗幼兒多元探索網站維護規格

## 專案概述

本專案為幼兒多元探索課程單頁式網站，使用 Bootstrap 作為版面框架，並以自訂 CSS 維護品牌視覺。頁面由上到下包含選單、五張輪播圖、關於我們、課程介紹四張卡片、頁尾公司資訊與社群連結。

## 目前檔案結構

```text
Website/
├── index.html
├── AGNETS.md
├── css/
│   ├── bootstrap.min.css
│   └── style.css
└── js/
    └── bootstrap.bundle.min.js
```

Bootstrap 相關原始檔與 map 檔可能也存在於 `css/`、`js/` 資料夾中，但頁面目前只引用壓縮版檔案。

## 主要引用

`index.html` 目前使用本地端 Bootstrap，不使用 CDN：

```html
<link href="css/bootstrap.min.css" rel="stylesheet">
<link href="css/style.css" rel="stylesheet">
<script src="js/bootstrap.bundle.min.js"></script>
```

自訂樣式統一維護於 `css/style.css`。若新增其他頁面，請在 Bootstrap 後方引用 `css/style.css`，讓自訂樣式能覆蓋 Bootstrap 預設值。

## 頁面區塊

1. 選單：固定於頁面上方，連結至首頁、關於我們、課程介紹、登入學員。
2. 輪播圖：使用 Bootstrap Carousel，共五張圖片。
3. 關於我們：左圖右文，介紹課程理念與特色標籤。
4. 課程介紹：四張 Bootstrap Card，分別為建構與邏輯、美感創作、音樂律動、感官探索。
5. 頁尾資訊：包含品牌介紹、社群連結、Email、電話、地址、快速連結與版權宣告。

## CSS 維護規範

主要品牌變數位於 `css/style.css` 開頭：

```css
:root {
  --brand: #4f8f7b;
  --brand-dark: #316655;
  --accent: #f6bd60;
  --soft: #fff8ed;
  --sky: #e8f6f8;
  --ink: #2f3a35;
}
```

調整品牌色、背景色、主文字色時，優先修改這些 CSS 變數。避免直接在多處寫死顏色，方便後續整體換色。

## 圖片維護

目前圖片使用 Unsplash 遠端圖片網址。若需改為完全本地化，建議新增 `images/` 資料夾，並依用途命名：

```text
images/
├── hero-01.jpg
├── hero-02.jpg
├── hero-03.jpg
├── hero-04.jpg
├── hero-05.jpg
├── about.jpg
├── course-building.jpg
├── course-art.jpg
├── course-music.jpg
└── course-sensory.jpg
```

圖片替換時請保留有意義的 `alt` 文字，確保無障礙與 SEO 基本品質。

## Bootstrap 使用規範

優先使用 Bootstrap Grid 與元件 class，例如：

- `container`
- `row`
- `col-*`
- `navbar`
- `carousel`
- `card`
- `btn`

自訂 CSS 應用於品牌視覺、間距微調、圖片裁切與互動效果。不要直接修改 `bootstrap.min.css`，避免框架升級時難以維護。

## 新增頁面規範

若未來新增其他頁面，建議沿用以下基本 HTML head：

```html
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<link href="css/bootstrap.min.css" rel="stylesheet">
<link href="css/style.css" rel="stylesheet">
```

頁面底部引用：

```html
<script src="js/bootstrap.bundle.min.js"></script>
```

若新頁面位於子資料夾，請依相對路徑調整 CSS 與 JS 引用。

## 注意事項

- 目前不使用 Bootstrap Icons CDN，圖標以文字標記呈現，避免外部套件依賴。
- 目前 Bootstrap CSS/JS 已改為本地引用。
- 若要完全離線使用，仍需將遠端圖片下載至本地並更新圖片路徑。
- `index.html` 不應再新增大型 `<style>` 區塊；請將自訂樣式放入 `css/style.css`。
- 頁面文字目前為繁體中文，後續新增內容請維持同一語系與語氣。

## 後續建議

- 建立 `images/` 資料夾並改用本地圖片。
- 將公司資訊、電話、地址與社群連結替換為正式資料。
- 若需要登入學員功能，建議新增獨立頁面或後端流程，不要只保留錨點。
- 上線前請測試桌機、平板、手機版的輪播圖裁切與文字可讀性。
