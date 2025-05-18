## GitCheatSheet

### ブランチ操作

| 目的  | コマンド |
| --- | --- |
| ブランチ一覧 | `git branch --all` |
| 作業中ブランチを表示 | `git branch --show-current` |
| 新規ブランチ作成 & 移動 | `git switch -c <new-branch>` |
| 既存ブランチへ移動 | `git switch <branch>` |
| ブランチをリネーム | `git branch -m <new-name>` |
| **ローカルブランチを削除** | `git branch -d <branch>`（未マージなら `-D`） |
| マージされたブランチを一括削除 | <br>`git branch --merged |
| 先祖コミット基準でブランチを切り替え | `git switch -c <new> <base-hash>` |
| ブランチを別リモートへ対応付け | `git branch -u upstream/<branch>` |
| ブランチ差分を確認 | `git diff <branchA>..<branchB>` |
| ブランチの先頭を変更せずに最新に追従 | `git merge --ff-only origin/<branch>` |
| ローカルの追跡設定を解除 | `git branch --unset-upstream` |

### リモート操作

| 目的  | コマンド |
| --- | --- |
| リモート一覧表示 | `git remote -v` |
| リモート追加 | `git remote add origin <URL>` |
| リモート URL 変更 | `git remote set-url origin <新URL>` |
| リモート名変更 | `git remote rename origin upstream` |
| 取得（フェッチ）のみ | `git fetch` |
| 取得 + 自動マージ | `git pull` |
| リベース付き取得 | `git pull --rebase` |
| 特定ブランチだけ取得 | `git fetch origin <branch>` |
| 変更を送信 | `git push` |
| 初回 push & 上流設定 | `git push -u origin <branch>` |
| --force-with-lease で安全強制 push | `git push --force-with-lease` |
| リモートブランチ削除 | `git push origin --delete <branch>` |
| リモートタグ削除 | `git push origin :refs/tags/<tag>` |
| プルリク用に push（fork -> upstream） | `git push fork <branch>` |
| リモートの HEAD を変更 | `git remote set-head origin -a` |

### ステージング & コミット

| 目的  | コマンド |
| --- | --- |
| 変更をステージ | `git add <ファイル>` / `git add .` |
| ステージを確認 | `git status` |
| コミットを作成 | `git commit -m "メッセージ"` |
| 直前のコミットを修正 | `git commit --amend` |

### 履歴を調べる

| 目的  | コマンド |
| --- | --- |
| ログを一覧 | `git log --oneline --graph --decorate --all` |
| ファイルの変更履歴 | `git log -p <ファイル>` |
| 2 つのコミット差分 | `git diff <hash1> <hash2>` |

### マージ & リベース

| 目的  | コマンド |
| --- | --- |
| 現在のブランチに `<branch>` をマージ | `git merge <branch>` |
| インタラクティブリベース | `git rebase -i <base>` |
| マージコンフリクト解消後に続行 | `git rebase --continue` / `git merge --continue` |

### 取り消し & 復元

| 目的  | コマンド |
| --- | --- |
| ステージ取り消し | `git restore --staged <ファイル>` |
| 変更取り消し（作業ツリー） | `git restore <ファイル>` |
| コミットを取り消して作業ツリーへ | `git reset --soft <hash>` |
| 強制巻き戻し（破壊的） | `git reset --hard <hash>` |

### タグ

| 目的  | コマンド |
| --- | --- |
| タグ作成 | `git tag <tag>` |
| 署名付きタグ | `git tag -s <tag> -m "msg"` |
| タグ送信 | `git push origin <tag>` |

---

### 便利オプション一行メモ

- `--all` : すべてのブランチ・リモートを対象
- `--force/-f` : 強制実行（誤用注意）
- `-u` : 上流（tracking）設定と push を同時に
