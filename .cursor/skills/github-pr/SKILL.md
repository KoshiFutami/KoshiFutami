---
name: github-pr
description: GitHub で PR を作成・更新する手順（gh CLI）。タイトル・本文の書き方。push 後に使う。このリポジトリに Makefile / PR テンプレは無い前提。
---

# GitHub PR 作成スキル（KoshiFutami）

## 前提

- [GitHub CLI](https://cli.github.com/)（`gh`）をインストールし、`gh auth login` 済みであること
- 変更を push 済みであること（`git push -u origin <branch>`）

## タイトル・本文

このリポジトリに `.github/pull_request_template.md` は無い。次を目安に書く。

### タイトル

- **Conventional Commits 風の接頭辞**（`feat:` / `fix:` / `chore:` / `docs:` など）＋ **一行で変更要約**（目安 50〜72 文字以内）。

### 本文（推奨セクション）

| 見出し | 書くこと |
|--------|----------|
| 概要 | なぜこの PR が必要か。1〜3 文。 |
| 変更内容 | 何をどう変えたか。箇条書き。 |
| 確認 | プレビューや表示確認など、実施したことを書く。 |

### 改行・余白

- 見出し（`##`）の直後に本文を書くときは、**空行を 1 行**入れる。
- `gh pr create --body` では `\n\n` で段落を分ける。

## 作成の流れ

1. 差分を踏まえてタイトル・本文の下書きを用意する。
2. 新規 PR:

   ```bash
   gh pr create --base main --title "docs: …" --body "…"
   ```

   長文なら一時ファイルに本文を書き、`gh pr create --base main --title "…" --body-file path/to/body.md`。

3. ブラウザでプレビューして体裁を確認。

## 既存 PR がある場合

`gh pr create` は新規専用。同じブランチに PR があるときは追記・更新する。

1. `gh pr view --json number,title,body,baseRefName,url`
2. `git fetch origin` のうえ `git log "origin/main"..HEAD --oneline` などで、ベース…HEAD のコミットを把握。
3. 本文の「変更内容」に未反映コミットを足す。概要・確認セクションも変わっていれば更新。
4. `gh pr edit --title "…" --body "…"` または `--body-file`。

エージェントは push のあと **先に** `gh pr view` で既存 PR の有無を確認し、あれば `gh pr edit`、なければ `gh pr create`。

## よく使うコマンド

| 目的 | コマンド |
|------|----------|
| 既存 PR の確認 | `gh pr view` / `gh pr view --json number,title,body,baseRefName,url` |
| 差分 | `gh pr diff` |
| 編集 | `gh pr edit` |
| 下書き PR | `gh pr create --draft ...` |

## トラブルシュート

- `gh: command not found` → `brew install gh`（macOS）
- 認証エラー → `gh auth login`
- リモートにブランチが無い → 先に `git push -u origin HEAD`
