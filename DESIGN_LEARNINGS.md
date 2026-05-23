# HALF Design Learnings

## 目的

emergingペルソナは、25–40代のクリエイティブ業のアート愛好家。Instagram でアーティスト個人をフォローし、NADAやFelix Art Fairを巡回する層。Gagosian的「ホワイトキューブの権威」にはむしろ警戒し、「DM で買えます」程度の透明性とDIY感に価値を感じる。HALFでは zine の手触りそのものをサイトに転写した。

このギャラリーは架空ブランドであり、実在のギャラリー・作家・作品ではない。

## 設計したこと

- 写真や作品画像を ±2° 単位で意図的に傾け、グリッドに乗らない貼り付け感を出した。
- 価格は常時表示・大きく可読。コレクター層と違って「いくらか分からないと検討すらしない」層の前提に立つ。
- カート/チェックアウト不採用。CTAは "DM to buy" 一本化。Instagramへ直接遷移する。
- 「Open Call」をスクリーン下に sticky で常時掲出し、ギャラリーが新人を募集している姿勢を見せる。
- パンチホール・テープ・スタンプ装飾を SVG で配し、zine やインディペンデント雑誌の質感を作る。

## CSS

主要なCSS判断:

```css
:root {
  --paper: #f4f0e6;        /* yellowed paper */
  --ink: #161410;          /* printing ink */
  --lime: #d7ff3a;          /* fluo highlight */
  --pink: #ff5c8a;          /* hot pink marker */
  --font-mono: 'IBM Plex Mono', monospace;
  --font-serif: 'Times New Roman', 'Noto Serif JP', serif;
  --font-ui: 'Inter', sans-serif;
}

/* tilt utility — never use 0deg */
.tilt-1 { transform: rotate(-1.5deg); }
.tilt-2 { transform: rotate(1.8deg); }
.tilt-3 { transform: rotate(-.6deg); }

/* paper noise */
body::after {
  content: "";
  position: fixed; inset: 0;
  background: url("data:image/svg+xml;utf8,<svg..."); /* fractalNoise */
  mix-blend-mode: multiply;
  opacity: .35;
  pointer-events: none;
}

/* highlighter swipe */
.fluo {
  background: linear-gradient(transparent 55%, var(--lime) 55%, var(--lime) 90%, transparent 90%);
}
```

色は黄ばんだ紙 × 印刷インクという「正しいセピア」をベースに、フルオライム+ピンクの蛍光ペン色を2点だけ刺す構造にした。

## アニメーション

- ローダーなし、reveal なし — 「未完成な状態こそ正直」というキーステートメントに反するため。
- 画像 hover で1°だけさらに傾く、というおまけ程度の遊び。
- スティッキー Open Call CTA は背景がほんのり脈動するだけの subtle な動き。

## フォント

- Display: `IBM Plex Mono`（zineのタイプライター見出しを参照）
- Body: `Times New Roman`（OS標準セリフ — リソース読み込みを敢えてケチる「貧しさ」の美徳）
- UI: `Inter`

Times New Roman を本文に採用したのは、貧弱さの誇示でもある。emerging ギャラリーは予算がないという前提を、フォント選定で隠さない。

## ボタン

ボタンはステッカー風。

- 蛍光ライムのバッジ、太い黒い縁取り、軽く回転。
- Hover で2°回転が逆向きになり、「貼ってある感」を強める。
- 価格バッジ・Open Call バッジに同じパターンを使い、サイト全体で「貼り付けた紙」のメタファーを統一。

## UI/UX

- アーティストのプロフィールには Instagram ハンドルと、(ない場合は無印で) email のみ。経歴は最小限に。
- Press section は引用付き。新人作家の場合「未掲載」と正直に書く。
- 価格は USD のみ。Ed. (Edition) と Year を併記。

## レイアウト

非対称スクラップブック。3カラム・4カラムを行ごとに崩し、グリッドラインを意図的に守らない。

各セクションは封筒の中身を貼ったような体裁。タイトル横にパンチホール SVG、写真の角にマスキングテープを SVG で描き、「実物の zine をスキャンしたかのような」第一印象を作っている。
