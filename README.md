[English](#english) | [日本語](#japanese)

---

<a id="english"></a>

# HALF — design-art-gallery-emerging

> **"Half-formed is the most honest state."**

A design study exploring a fictional emerging art gallery — Off Paradise / Bridget Donahue / 56 Henry tier — targeting **creative professionals aged 25–40** who follow artists on Instagram, attend NADA and Felix Art Fair, and value transparency over polish.

HALF is a fictional gallery created for this design study. It is not a real gallery, dealer, artist, or work.

## Overview

| | |
|---|---|
| **Brand** | HALF |
| **Persona** | emerging |
| **Live Site (planned)** | `design.art-gallery-emerging.riumu.net` |

## Design Concept

- **Color**: Yellowed paper `#F4F0E6` × printing ink `#161410` × fluo lime `#D7FF3A` + hot pink `#FF5C8A`
- **Typography**: IBM Plex Mono (display) × Times New Roman (body editorial) × Inter (UI)
- **Aesthetic**: DIY zine × asymmetric scrapbook × intentional imperfection
- **UX**: Price badges always visible. Tilted images (±2°). Sticky Open Call CTA. No cart — "DM to buy".
- **Texture**: SVG paper noise + punchholes + tape decorations.

## Tech Stack

- Pure HTML + CSS Custom Properties + Vanilla JS
- Google Fonts CDN (IBM Plex Mono + Inter) + system Times
- No framework, no build step — GitHub Pages ready

## Spec

See [spec.md](./spec.md) for the full design specification.

## Install as a skill / スキルとして導入

This repo ships a cross-agent **`SKILL.md`** (open standard) usable by both Claude Code and Codex CLI as a design-reference skill. Link the repo into the agent's skills directory:

このリポジトリは Claude Code / Codex CLI 共通の **`SKILL.md`**（オープン標準）を同梱し、デザイン参照スキルとして使えます。

```bash
# Claude Code
ln -s "$(pwd)" ~/.claude/skills/design-art-gallery-emerging
# Codex CLI
ln -s "$(pwd)" ~/.codex/skills/design-art-gallery-emerging
```

Restart the agent; it is matched automatically by the skill's `description` (skill name: `design-art-gallery-emerging`). / エージェント再起動後、`description` に基づき自動マッチします。

## Part of

This repository is one of four design studies under the **art-gallery persona series**:

| Persona | Brand | Aesthetic |
|---------|-------|-----------|
| bluechip | NORE | Museum-grade white cube |
| **emerging** | HALF | DIY zine, anti-luxury |
| digital | HEX | Terminal, Web3 native |
| institutional | MASS | Scholarly, multilingual |

Navigator: [art-gallery](../README.md)

---

<a id="japanese"></a>

# HALF — design-art-gallery-emerging（日本語）

> **「半分のままが、いちばん正直だ」**

新進アートギャラリー（Off Paradise / Bridget Donahue / 56 Henry 級）のデザイン研究。**25–40代、Instagram でアーティストを追うクリエイティブ業のアート愛好家** — NADA / Felix Art Fair 来場、ポリッシュより透明性を重んじる層 — に特化した架空ギャラリーのサイトです。

HALF は本デザイン研究のために作成した架空ギャラリーです。実在のギャラリー・ディーラー・作家・作品ではありません。

## 概要

| | |
|---|---|
| **ブランド** | HALF |
| **ペルソナ** | emerging |
| **公開URL（予定）** | `design.art-gallery-emerging.riumu.net` |

## デザインコンセプト

- **カラー**: 黄ばんだ紙 × 印刷インク × フルオライム + ピンクハイライター
- **フォント**: IBM Plex Mono（見出し）× Times New Roman（本文）× Inter（UI）
- **世界観**: DIY zine × 非対称スクラップブック × 意図的な不完全さ
- **UX**: 価格バッジ常時表示、画像が ±2° 傾く、付箋風 Open Call CTA。カート無し、"DM to buy"
- **テクスチャ**: SVG 紙ノイズ + パンチホール + テープ装飾

## 技術

- 純粋な HTML + CSS Custom Properties + Vanilla JS
- Google Fonts CDN（IBM Plex Mono + Inter）+ OS の Times
- ビルド不要で GitHub Pages 対応

## 仕様書

詳細は [spec.md](./spec.md) を参照。

## シリーズ

このリポジトリはアートギャラリー・ペルソナシリーズ4作のうちの1つ。
ナビゲーターページ: [art-gallery](../README.md)
