# HALF — design-art-gallery-emerging Spec

**Status:** Approved
**Author:** torifo
**Created:** 2026-05-22
**Updated:** 2026-05-22

---

## 1. Overview

### Problem Statement
新進ギャラリー（Off Paradise / Bridget Donahue / 56 Henry / Maxwell Graham 級）は、ブルーチップ的「museum white」を採用するとブランド規模に見合わず、商業EC的UIを採用するとアート界での信用を失う。同時に、Instagram 駆動の若いコレクター・アート愛好家は「整い切ったサイト」よりも「現場の質感」を信用する。情報の整然さよりも、編集者の個性が滲むレイアウト言語が求められる。

### Goal
"HALF"（不完全・未完成・半身）という架空の新進ギャラリーのランディングページを実装し、**DIY zine 美学 × 意図的な不揃い × アンチラグジュアリー** が、低予算ながら強いブランド人格を立ち上げられることを検証する。

### Non-Goals
- EC機能
- 美術館的な余白美学（HALF は意図的にギャラリー化されたホワイトキューブ感を拒否する）
- スムーズなアニメーション（むしろカクカク・jolt を許容）
- 多言語対応

### Background
- HALF は本デザイン研究のために作成した架空ブランドであり、実在のギャラリーではない
- `design-art-gallery-emerging` リポジトリ予定
- art-gallery シリーズ第2作（市場ロー軸 / 編集者個性軸）

---

## 2. Persona

| 属性 | 詳細 |
|------|------|
| 年齢 | 25–40代 |
| 職業 | クリエイティブ業（写真家・編集者・グラフィックデザイナー・小規模ブランドオーナー） |
| 資産 | 年収 $60K–$150K、年間アート購入 $500–$8K（プリント・ZINE・小品中心） |
| 行動 | Instagram でアーティストをフォロー、NADA / Felix Art Fair 来場、Printed Matter Book Fair 常連 |
| 共鳴する価値 | アーティスト本人の声、DIY、未完成性、独立性、印刷物の質感、コミュニティ |
| 嫌うもの | 過剰なポリッシュ、museum white の冷たさ、コーポレートUI、価格非公開の格付け感 |
| 情報源 | Instagram, Are.na, Substack newsletter, Printed Matter, e-flux |

---

## 3. User Stories

| ID | Persona | Want to | So that |
|----|---------|---------|---------|
| US-01 | アート愛好家 | 開いた瞬間に「人がやってる」感を受け取りたい | 自分の感性と合うか即座に判断できる |
| US-02 | 同上 | 現在のショーの作品を、雑誌の見開きを眺めるように見たい | 編集者の意図 = ギャラリストの目利きを感じ取れる |
| US-03 | 同上 | 価格・在庫・サイズが明示されていてほしい | 購入可否を即判断できる（コレクター層と違いここは明示） |
| US-04 | アーティスト志望者 | submit / open call の動線を見つけたい | 自分の作品を持ち込める入口がある |
| US-05 | コミュニティメンバー | リスニングパーティ・対談・zine リリースイベント情報を知りたい | ギャラリーの「現場」に行ける |

---

## 4. Functional Requirements

| ID | Requirement | Priority |
|----|-------------|----------|
| FR-01 | ロード時：ブランド名がガタガタ揃わずに着地（intentional misalignment） | P0 |
| FR-02 | 紙ノイズ・パンチホール・テープ風オーバーレイ（fixed, opacity 0.06） | P0 |
| FR-03 | ヒーロー：見出しが2行で意図的に左右非対称、右にスナップ写真 | P0 |
| FR-04 | 作品グリッド：irregular masonry、画像が傾く（rotate ±2deg）、価格バッジ付き | P0 |
| FR-05 | マーキー：手書き風または mono フォント、スロー、文章を途中で切る | P1 |
| FR-06 | アーティスト紹介：左に Polaroid 写真、右にハンドタイプ風キャプション | P0 |
| FR-07 | About セクション：手紙風レイアウト、署名入り | P1 |
| FR-08 | Events セクション：チケット風カード、日付スタンプ | P1 |
| FR-09 | Open Call CTA：付箋風、ページ右下固定 | P2 |
| FR-10 | カスタムカーソル：default のまま（DIY 感を残す） | - |
| FR-11 | ナビ：ノートの破れた紙風背景、リンク間がランダム距離 | P0 |
| FR-12 | モバイル対応（375px基準、傾きは弱める） | P0 |

---

## 5. Design System

### Color Palette
```css
--bg:        #F4F0E6;   /* 黄ばんだ紙、newsprint ground */
--bg-sub:    #ECE7D8;   /* やや深い紙 */
--bg-stamp:  #1A1A1A;   /* インクスタンプ黒 */
--fg:        #161410;   /* 印刷インクほぼ黒 */
--fg-muted:  #6B6555;   /* 鉛筆書き */
--fg-light:  #A8A092;   /* セピアミュート */
--border:    #1A1A1A;   /* 太罫線（細罫線を使わない） */
--accent:    #D7FF3A;   /* フルオライム（highlighter pen） */
--accent-2:  #FF5C8A;   /* ピンクハイライター */
```

### Typography
```css
--font-mono:   'IBM Plex Mono', 'Courier New', monospace;       /* Display, brand */
--font-serif:  'Times New Roman', 'Tiempos Text', Times, serif; /* Body editorial */
--font-sans:   'Söhne', 'Inter', sans-serif;                    /* Captions, UI */
```
- Google Fonts CDN: IBM Plex Mono (wght 400, 600), Inter (wght 400, 500)
- Times は OS フォントで十分（Tiempos は商用、回避）
- Display サイズ: clamp(3rem, 8vw, 9rem)、wght 600、letter-spacing 0
- Body サイズ: 17px / line-height 1.5 / Times serif
- 価格バッジ: 13px / mono / 黒バック白文字

### Spacing
```css
--space-xl:    clamp(4rem, 8vw, 7rem);
--space-md:    1.6rem;
--space-sm:    0.6rem;
/* 余白は museum 系より詰める、紙の節約感 */
```

### Motion
```css
--ease:   cubic-bezier(0.4, 0, 0.2, 1);
--ease-snap: cubic-bezier(0.7, 0, 0.3, 1);
/* loader: brand 0.6s, ガタッと着地 (translate jolt) */
/* hero: image rotate ±1.5deg → 0 in 0.8s */
/* scroll reveal: opacity 0.5s + translate 20px、ease-snap */
/* マーキー: 60s linear infinite (遅め) */
```

### Texture
- SVG paper noise（feTurbulence baseFrequency=0.9, opacity 0.06）
- パンチホール: 円形 SVG、ヘッダー上に2つランダム配置
- テープ: 半透明黄色矩形、画像のコーナーに rotate ±10deg

### Imagery
- スナップ写真（iPhone的）、グレイン強め
- インスタレーション写真は床・什器が映り込む（museum 写真の真逆）
- アーティストポートレートはカラーの Polaroid 風（白い枠付き）
- 完全な構図を選ばず、フレームアウトを許容

---

## 6. Architecture

```
index.html
├── .paper-bg            # SVG noise + texture
├── .punchholes          # 2つの円、ヘッダー上に配置
├── nav                  # 紙の破れ風、ロゴ "HALF" + 5リンク
├── .hero                # 2カラム左右非対称
│   ├── .hero-text       # "WORKS BY / PEOPLE WE / KNOW" 3行スタック
│   └── .hero-snap       # Polaroid 風スナップ、rotate -3deg
├── .marquee             # 現在ショー名 + アーティスト名スクロール
├── .section#works       # 作品 masonry グリッド
│   └── .work-card       # 画像（rotate ±2deg）+ タイトル + 価格バッジ
├── .section#artists     # アーティスト紹介、Polaroid + 手紙
├── .section#about       # 手紙風 About、署名入り
├── .section#events      # チケット風カード、3枚
├── .opencall-sticky     # 付箋風 CTA、右下固定
└── footer               # newsletter form + 住所 + SNS
```

---

## 7. Key Design Decisions

| Decision | Chosen | Rationale |
|----------|--------|-----------|
| テーマ | Light / yellowed paper #F4F0E6 | 黄ばんだ紙 = zine 美学、museum white の逆 |
| ヒーロー | 左右非対称テキスト + Polaroid 写真 | 雑誌見開きの編集体験、整然グリッドの拒否 |
| Display font | IBM Plex Mono | typewriter / fanzine 美学、Bodoni の真逆 |
| Body font | Times New Roman | OSデフォルト、印刷物的、無料、特権感の拒否 |
| アクセント | Fluo lime + ピンクハイライター | highlighter pen / sticker、商業色を持つ |
| 罫線 | 太黒罫線 1.5–2px | 細罫線（高級UI）の意図的拒否、印刷物の太線 |
| 画像 | rotate ±2deg、テープ付き | スクラップブック、museum 整列の拒否 |
| 価格表示 | バッジ常時表示 | 透明性 = ロー層への誠実さ、隠す = ハイ層特権 |
| カート | なし、価格バッジに "DM to buy" | DIY運営感、Instagram駆動 |
| マーキー | 文章を途中で切る | 雑誌の余白感、完璧性の拒否 |
| Open Call | 付箋風固定 | コミュニティ志向、入口の常時可視化 |
| カーソル | OSデフォルト | カスタムカーソル = 過剰演出、DIY 美学に反する |
| Texture | paper noise + テープ + パンチホール | リアル印刷物の質感再現、3層重ね |

---

## 8. Layout Reference

### Hero (Desktop)
```
○                              ○        ← punchholes
┌───────────────────────────────────────────────┐
│ HALF              works  artists  about ...   │  ← nav, torn paper bg
├───────────────────────────────────────────────┤
│                                               │
│  WORKS BY                  ╱──────────╲       │
│    PEOPLE                  │ [POLAROID] │  ←  │  ← rotate -3deg
│      WE KNOW.              │ snap       │     │
│                            ╲──────────╱       │
│                                               │
│  CURRENT SHOW —— May 12 ▸ June 30             │  ← mono caption
│                                               │
├───────────────────────────────────────────────┤
│ ⟵⟵⟵ marquee: artist names, slow ⟵⟵⟵      │
└───────────────────────────────────────────────┘
```

### Works Grid (Desktop)
```
┌────────────────────────────────────────────┐
│  ┌────┐    ┌──────┐         ┌────┐         │
│  │ ART│    │ ART  │         │ART │         │  ← rotate ±2deg, masonry
│  │ ▢  │    │  ▢   │         │ ▢  │         │
│  │$420│    │$1.2K │         │$680│         │  ← price badge (black)
│  └────┘    └──────┘         └────┘         │
│       ┌─────┐       ┌────────┐             │
│       │ ART │       │ ART    │             │
│       │  ▢  │       │   ▢    │             │
│       │$890 │       │ NFS    │             │
│       └─────┘       └────────┘             │
└────────────────────────────────────────────┘
```

---

## 9. Accessibility

| 項目 | 実装 |
|------|------|
| コントラスト比 | fg #161410 on bg #F4F0E6 = 14.2:1 (AAA) |
| 画像 rotation | prefers-reduced-motion で 0 に戻す |
| キーボード操作 | tab可、focus-visible で fluo lime 太枠 |
| 価格バッジ | aria-label 明示（"price: 420 USD"） |
| テープ・パンチホール | aria-hidden, デコレーション |
| 手書き風フォントは使わない | 視覚的に手書き感は色とテクスチャで作る |
| 言語 | `<html lang="en">` |

---

## 10. Tech & Deploy

- 単一 `index.html`、CSS Custom Properties、Vanilla JS
- フォント: Google Fonts CDN（IBM Plex Mono + Inter）+ Times はシステム
- 画像: Unsplash CDN（スナップ写真風を選定）
- SVG noise / punchholes はインライン SVG
- デプロイ: GitHub Pages, `design-art-gallery-emerging` リポジトリ
- カスタムドメイン: `design.art-gallery-emerging.riumu.net` 予定

---

## 11. Inspiration & References

- offparadise.com — DIY editorial、変則レイアウト
- bridgetdonahue.nyc — 価格透明、フレンドリーなコピー
- 56henry.nyc — 極小ギャラリー、ロゴと写真だけのページ
- printedmatter.org — zine 文化の総本山、紙質感
- aresnave / are.na — リサーチ的ブラウズUX

HALF は上記から「**紙質感 + 太罫線 + 価格透明 + DIY 編集言語**」を抽出した架空のブランド。NORE の対極として設計。
