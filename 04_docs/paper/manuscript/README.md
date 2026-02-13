# 最終報告書の作成ガイド

## 概要

最終報告書は LaTeX（情報処理学会の研究報告フォーマット）で作成します．
このフォルダにスタイルファイルとサンプルが用意されています．

## TeX 環境のセットアップ

TeX 環境の構築は，**生成AI（GitHub Copilot, Claude 等）に相談しながら進めてください．**
以下の情報を伝えれば，具体的な手順を案内してもらえます．

### 生成AIへの依頼例

```
LaTeX の環境を構築したいです．以下の条件で手順を教えてください．

- OS: （macOS / Windows / Linux）
- 目的: 日本語の論文（情報処理学会フォーマット）を書く
- 必要なもの: platex + dvipdfmx が使えること
- エディタ: VS Code を使いたい（LaTeX Workshop 拡張を使う想定）
```

### 最低限必要なもの

| 項目 | 説明 |
|---|---|
| TeX ディストリビューション | TeX Live（macOS/Linux）または MiKTeX（Windows） |
| LaTeX エンジン | `platex`（日本語対応） |
| PDF 変換 | `dvipdfmx` |
| エディタ（推奨） | VS Code + LaTeX Workshop 拡張 |

## ファイル構成

| ファイル | 説明 | 編集 |
|---|---|---|
| `sample-report.tex` | **サンプル報告書（これをコピーして使う）** | コピーして編集 |
| `kaishi-report.sty` | ゼミ用カスタムスタイル | 変更不要 |
| `ipsj.cls` | 情報処理学会クラスファイル | 変更不要 |
| `ipsjtech.sty` | 研究報告用スタイル | 変更不要 |
| `ipsjpref.sty` | 序文用スタイル | 変更不要 |
| `ipsjsort.bst` / `ipsjunsrt.bst` | 参考文献スタイル | 変更不要 |
| `../references.bib` | 参考文献データ（BibTeX 使用時） | 必要に応じて編集 |

## 報告書の書き方

### 1. サンプルをコピーする

```bash
cp sample-report.tex my-report.tex
```

### 2. 編集する箇所

`my-report.tex` を開き，以下を書き換えてください．

```latex
%% 年度を指定
\nendo{2026}

%% タイトル
\title{あなたの報告書のタイトル}

%% 著者名
\author{あなたの名前}{Your Name}{}

%% 概要
\begin{abstract}
ここに概要を書く．
\end{abstract}
```

本文は各 `\section{}` の中身を書き換えます．

### 3. ビルドする

```bash
platex my-report.tex
platex my-report.tex
dvipdfmx my-report.dvi
```

2回 `platex` を実行するのは，相互参照（図表番号・章番号など）を正しく解決するためです．

BibTeX を使う場合は以下の順序になります．

```bash
platex my-report.tex
pbibtex my-report
platex my-report.tex
platex my-report.tex
dvipdfmx my-report.dvi
```

### 4. VS Code + LaTeX Workshop を使う場合

LaTeX Workshop をインストールすれば，保存時に自動ビルドされます．
設定方法が分からない場合は，生成AIに以下のように聞いてください．

```
VS Code の LaTeX Workshop で platex + dvipdfmx を使う設定を教えてください．
recipe と tool の設定例を JSON で示してください．
```

## 報告書のフォーマット

- **原則5枚以上**（文字数で原則7500字以上）
- 句点は「．」，読点は「，」を使用（「。」「、」は使わない）
- 図表を効果的に使うこと

### 構成例

1. **はじめに** — 背景・課題・方法の概略，報告書の構成
2. **背景と課題** — 実習内容の背景と課題
3. **課題の解決方法** — 解決のための方法（「提案手法」等でも可）
4. **結果と考察** — 結果の提示と考察
5. **まとめと今後の課題** — 総括と今後の課題（「おわりに」でも可）

テーマによってしっくりこない場合は，章立てを適宜調整してください．

## 困ったときは

LaTeX のエラーや書き方で困ったら，**エラーメッセージをそのまま生成AIに貼り付けて**相談してください．
ほとんどの問題は解決できます．
