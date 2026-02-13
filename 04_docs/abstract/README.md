# 最終発表会 要旨の作成ガイド

## 概要

最終発表会で聴衆に配布する **A4 1枚の要旨**を作成します．
LaTeX（jsarticle ベース・2段組）で作成します．

## TeX 環境のセットアップ

報告書と同じ環境で作成できます．
まだ環境を構築していない場合は `04_docs/paper/manuscript/README.md` を参照してください．

## ファイル構成

| ファイル | 説明 | 編集 |
|---|---|---|
| `sample-abstract.tex` | **サンプル要旨（これをコピーして使う）** | コピーして編集 |
| `latexmkrc` | latexmk 用設定（platex + dvipdfmx） | 変更不要 |
| `image/` | 図表の画像ファイル置き場 | 必要に応じて追加 |

## 要旨の書き方

### 1. サンプルをコピーする

```bash
cp sample-abstract.tex my-abstract.tex
```

### 2. 編集する箇所

`my-abstract.tex` を開き，以下を書き換えてください．

```latex
%% 年度を指定
\renewcommand{\nendo}{2026}

%% タイトル
\title{あなたの要旨のタイトル}

%% 著者名
\author{あなたの名前}

%% 学籍番号
\bangou{201XX01}
```

本文は各 `\section{}` の中身を書き換えます．

### 3. ビルドする

```bash
platex my-abstract.tex
platex my-abstract.tex
dvipdfmx my-abstract.dvi
```

または latexmk を使う場合：

```bash
latexmk my-abstract.tex
```

## 要旨のフォーマット

- **A4 1枚**（2段組）
- 句点は「．」，読点は「，」を使用
- 構成例：背景と目的 → 研究方法 → 結果と考察
- 図表を効果的に使うこと

## 困ったときは

LaTeX のエラーや書き方で困ったら，**エラーメッセージをそのまま生成AIに貼り付けて**相談してください．
