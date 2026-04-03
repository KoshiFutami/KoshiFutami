---
description: 現在ブランチをリモートへ push し、必要なら PR 作成へ進む
---

# push

## 目的

ローカルのコミットを **リモートに追跡付きで push** し、続けて PR を作れる状態にする。

## 手順

1. コミット済みであることを確認: `git status`（未コミットがあれば先に `commit` コマンドを参照）。
2. 初回または upstream 未設定時:

```bash
git push -u origin HEAD
```

3. 以降は `git push` でよい場合が多い。
4. push 後、PR がまだなら: `gh pr create --base main`（詳細は `.cursor/skills/github-pr/SKILL.md`）。

## 注意

- `git push --force` は共有ブランチでは原則使わない。リベース後などは自分のルールに従う。
- リモート名が `origin` でない場合はコマンドを読み替える。
