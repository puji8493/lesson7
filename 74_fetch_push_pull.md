# fetch コマンド、pull コマンド、push コマンド

| コマンド | 機能 | コマンド実行例 | 
| ---- | ---- | ---- | 
| `git branch --list -r` | リモートブランチのリストを出力します。 | `git branch --list -r` |
| `git push` | リモートリポジトリを更新します。 | `git push` |
| `git fetch` | リモートリポジトリからブランチ等の状態を取得し、リモート追跡ブランチを更新します。 | `git fetch` |
| `git pull` | `git fetch` と `git merge` を連続的に実行し、ローカルブランチを更新します。 | `git pull` |
| `git chekout origin <branch_name>` | ワーキングツリーを、リモートリポジトリのブランチの最新の状態にします。 | `git pull` |

***

メモ:
- `git fetch` と `git merge` を分けて行うことは基本的にありません。  
      `git pull` コマンドを使う場合がほとんどです。
- `git push` コマンドは、ローカル端末のリポジトリがリモートリポジトリと同期された状態でないと実行できません。  
    `git push` が拒絶された場合は、いったん `git pull` を行い、それから再度 `git push` コマンドを実行します。
