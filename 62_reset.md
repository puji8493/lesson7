# reset

`git reset` コマンドを使って、HEAD を特定のコミットがされたときの状態に戻すことができます。  
ほぼ間違いなく、 `--hard` オプションを同時に指定します。

| コマンド | 機能 | コマンド実行例 | 
| ---- | ---- | ---- | 
| `git reset` | 直前のコミットのときの状態に戻します。 | `git reset --hard` |
| `git reset [revision_no]` | 特定のコミットのときの状態に戻します。 | `git reset 74dd8f09c4419000ab3cf96d1fc809389f8f43cc --hard` |
