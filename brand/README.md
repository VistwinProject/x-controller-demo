# 品牌資產插槽

頂列的排法是 **[寶鋪 logo] │ [ANLB 商標] │ 全區總控** —— 三個東西是三件事:
寶鋪是業主、ANLB 是展的東西、全區總控是這支 app。

把寶鋪的 logo 放進這個資料夾,頂列會自動補上那一格。**不需要改任何程式。**

## ANLB 商標(已經有了,不在這個資料夾)

來源:`20260723 ANLB LOGO_註冊商標.ai`(2 個 artboard,同一組路徑的
黑 `#231815` 與白 `#ffffff` 兩個色版)。

它**不是**放在這裡的圖檔,而是 [`src/components/AnlbMark.jsx`](../../src/components/AnlbMark.jsx)
裡的 inline SVG。理由只有一個:要吃 `currentColor`。
`<img>` 載進來的 SVG 繼承不到文字色,就得維護黑白兩個檔、還會有哪一版
忘記更新的問題;inline 之後 light / dark 自動翻,只有一個來源。

轉檔時**路徑一個點都沒有動** —— 這是註冊商標,形狀不可改。唯一的改動
是填色換成 `currentColor`,而那剛好等價於原檔的兩個色版。

出現在:每一個分頁的頂列(24px 高)+ 入口頁的折射玻璃板(56px 高)。

## 要放的檔案

| 檔名 | 用途 | 規格 |
|---|---|---|
| `baopu-logo.svg` | 頂列品牌標 | **SVG 優先**。高度會被縮到 28px,所以請給向量;若只有點陣圖,至少 3× 尺寸(高 84px 以上)的 PNG,並把檔名改成 `baopu-logo.png` 同時改 `src/components/BrandMark.jsx` 裡的 `LOGO_SRC` |

檔案不存在時整格連同分隔線一起收掉(不會留一個洞),頂列就只有 ANLB 商標 —— **缺檔不會壞版**,所以先放先看、不急也沒關係。

## 深色模式

頂列是霧面玻璃,light / dark 兩軌的底色差很多。logo 如果是單色,最省事的做法是給
**深色版一份**,命名 `baopu-logo-dark.svg`,然後在 `BrandMark.jsx` 依 `data-theme` 切換。

如果 logo 本身是 SVG 且用 `currentColor` 描邊/填色,那什麼都不用做 —— 會自動跟著文字色翻。
拿到檔案後我可以幫你改成這種寫法。

## 還沒決定的事

`X-Controller` 是**銷售人員拿在客人面前**的東西,所以品牌層有一個未決:

- 只掛寶鋪?
- 寶鋪 + VISION BASE 雙標?
- 還是掛 VisTwin?

目前版面預留的是「logo + 細分隔線 + 全區總控」,單標雙標都塞得下。
vault 有一份 `01 專案/寶鋪 showcase/寶舖品牌概念對照表.md`(8.5 KB)還沒讀,
裡面應該有寶鋪自己的品牌語言,可能會影響這個決定。

## 其他圖示

app 圖示(PWA / 加入主畫面 / 瀏覽器頁籤)是另一組,在 `public/` 根目錄:

- `icon.svg` · `icon-192.png` · `icon-512.png` · `apple-touch-icon.png`

目前是暫代圖(X + 中央匯流節點),視覺定稿後直接覆蓋這四個檔即可。
