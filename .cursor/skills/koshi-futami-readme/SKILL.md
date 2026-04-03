---
name: koshi-futami-readme
description: KoshiFutami（GitHub プロフィール README）の編集方針。Kotlin data class ブロック・セクション構成・リンク・トーンを揃える。
---

# KoshiFutami README スキル

## いつ使うか

- `README.md` を更新するとき（経歴・リンク・興味・自己紹介の文言）
- プロフィール用リポジトリの体裁を崩さずに差分を足したいとき

## リポジトリの性質

- GitHub ユーザー名と同名のリポジトリ。ルートの `README.md` がプロフィールに表示される。
- コードベースやアプリではなく、**自己紹介用 Markdown** が主な成果物。

## 構成の目安（現状に合わせる）

- 冒頭の短い挨拶
- **`KoshiFutami` の Kotlin `data class` + `val me = ...`** で要約（名前・出身・役割・GitHub・focus・interests）
- **Previous work experience** — 会社名、期間、役割を英語で簡潔に
- **Education**
- **Philosophy** — バックエンド・インフラ・フルスタックのバランス
- **Beyond code** — 趣味・学習
- **How to reach me** — GitHub・Instagram など（URL は完全形）

新しいセクションを足す場合も、既存の見出しレベル（`###`）と英語中心のトーンに揃える。

## Kotlin ブロックを触るとき

- `data class` のフィールドと `me` の実引数が **対応している**ことを保つ（名前変更は両方）。
- リストは `listOf(...)` のまま、末尾カンマは Kotlin の慣習に合わせてよい。
- このブロックは「表示用の要約」なので、README 本文と矛盾しないようにする。

## Markdown・リンク

- 外部リンクは `[表示名](https://...)` でフル URL。
- 絵文字は冒頭程度に留め、本文は読みやすさ優先。

## 避けること

- 秘密情報・社内固有情報の過剰な記載
- プロフィール README と無関係な大規模ファイル追加（このリポジトリのスコープ外）
- `README.md` 以外を安易に増やさない（ユーザーが明示した場合を除く）

## 確認

- 保存後、GitHub 上のプロフィール表示で改行・コードブロックが意図どおりか目視する。
