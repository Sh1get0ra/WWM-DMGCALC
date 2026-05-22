# 風燕伝 ダメージ計算ツール — Design System

武侠HUD テーマ。朱色 (vermilion) を主軸とした中華武侠美術 × 戦術データ HUD。

## 1. デザイン哲学

| 原則 | 説明 |
|------|------|
| 武侠HUD | 中華武侠世界観 × 軍用 HUD 戦術表示 の融合 |
| 高密度 | 計算ツール = 情報密度優先、装飾は機能に従属 |
| 朱色基調 | vermilion `#c83c2b` をアクセント、過剰使用なし |
| 鋭利 | 角丸 1〜2px 限定、シャープなエッジ |
| 双テーマ | dark (墨色基調) / light (古紙基調) 完全対応 |

## 2. カラーパレット

### Dark theme (デフォルト)

| トークン | 値 | 用途 |
|----------|----|----|
| `--vermilion` | `#c83c2b` | 主朱色 |
| `--vermilion-bright` | `#e8513a` | アクセント |
| `--vermilion-deep` | `#8a1f17` | 影朱 |
| `--gold` | `#c9a45a` | 金 |
| `--gold-bright` | `#f0d28a` | 期待値ヒーロー数字 |
| `--gold-deep` | `#8a6f30` | 影金 |
| `--jade` | `#7fa88a` | 翡翠 (STATUS SCORE 緑) |
| `--jade-bright` | `#a8d4b4` | 翡翠アクセント |
| `--bone` | `#c9b88a` | 骨色 |
| `--paper` | `#ede4d0` | 紙白 (主テキスト) |
| `--paper-dim` | `#8b8170` | 紙暗 (補助テキスト) |
| `--paper-mute` | `#6a6053` | 紙静 (背景文字) |
| `--bg-0` | `#07060a` | 最深背景 |
| `--bg-raised` | `#1a1410` | 浮上背景 |

### Light theme (`html[data-theme="light"]`)

dark トークン上書き。古紙テーマ:
- `--bg-0: #ede2c8`、`--paper: #2a1c12`、`--gold-bright: #5e4310`
- 朱色は両テーマ共通

### Chart カラー (確率分布円グラフ準拠)

| トークン | 値 | 意味 |
|----------|----|----|
| `--chart-crit` | `#f0d28a` | クリティカル (黄金) |
| `--chart-sympathy` | `#e8513a` | 共鳴 (朱橙) |
| `--chart-graze` | `#6a6053` | かすり (灰) |
| `--chart-normal` | `#ede4d0` | 通常 (淡灰) |

## 3. タイポグラフィ

### フォントファミリー

| トークン | スタック |
|----------|----------|
| `--f-display` | Noto Serif JP / Yu Mincho — 見出し |
| `--f-body` | Noto Sans JP / Hiragino Sans — 本文 |
| `--f-latin` | Cinzel / Cormorant Garamond — 数字ヒーロー |
| `--f-mono` | Rajdhani / JetBrains Mono — 数値 HUD |

### サイズスケール (8段)

| トークン | サイズ | 用途 |
|----------|--------|------|
| `--text-2xs` | 8px | アイコンラベル |
| `--text-xs` | 10px | 補助ラベル・HUDメタ |
| `--text-sm` | 11px | 本文・入力ラベル |
| `--text-md` | 13px | 本文 base |
| `--text-lg` | 16px | 強調 |
| `--text-xl` | 22px | パネル見出し |
| `--text-2xl` | 28px | breakdown数値 |
| `--text-hero` | 92px | EXPECTED ヒーロー |

特殊: `48px` (STATUS SCORE)、`320px` (背景印章)。

## 4. スペーシング

```
--space-1: 4px    --space-5: 20px
--space-2: 8px    --space-6: 24px
--space-3: 12px   --space-7: 32px
--space-4: 16px   --space-8: 40px
```

## 5. コンポーネント命名規約

- `.field-input` — 数値入力
- `.field-select-wide` — セレクト
- `.icon-btn` — アイコンボタン
- `.icon-btn-x` — X (Twitter) 専用
- `.preset-btn`, `.preset-name-input` — プリセット
- `.lang-btn` — 言語切替
- `.hero` / `.hero--collapsed` — メインヒーロー
- `.compact-bar` — コンパクト表示帯
- `.tier-badge` (SS/S/A/B/C) — スコア階級

## 6. アニメーション原則

- 27箇所のみ = 機能的アニメに限定
- 過剰スクロールアニメ なし
- Tier S = pulse glow、Tier SS = shimmer + glow
- transition 標準: 0.15s ease

## 7. アクセシビリティ

- `aria-live` 動的更新通知
- `aria-expanded` 折りたたみ状態
- `focus-visible` 全インタラクティブ要素
- カラーコントラスト: WCAG AA 準拠 (paper #ede4d0 on bg-0 #07060a = 13.5:1)

## 8. 角丸

- 1〜2px のみ
- 武侠HUD = シャープなエッジ強調
- 大きな radius (`8px+`) 禁止 — テーマ崩壊

## 9. レスポンシブ

- `@media (max-width: 600px)` モバイル
- コンパクトモード = JS トグルでヒーロー圧縮
- 横スクロール厳禁

## 10. 多言語対応

- ja (日本語、デフォルト)
- en (English)
- zh (中文簡体)
- ko (한국어)

`data-i18n="key"` 属性で i18n.js が文字列差替。

---

**バージョン**: 1.0.0
**最終更新**: 2026/05/22
**保守**: SHIGETORA
