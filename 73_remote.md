# remote コマンド

| コマンド | 機能 | コマンド実行例 | 
| ---- | ---- | ---- | 
| `git remote add` | ローカルリポジトリとリモートリポジトリとを関連づけます。 | `git remote add origin https://github.com/<username>/<repository_name.git>` |
| `git push -u origin <branch_name>` | ローカルのブランチと同じものをリモートで利用可能にします。 | `git push -u origin <branch_name>` |

| コマンド | 機能 | コマンド実行例 | 
| ---- | ---- | ---- | 
| `git remote remove <repository_name>` | リモートリポジトリとの関連づけを解除します。 | `git remote remove <repository_name>` |

上記で origin はリモートリポジトリにローカル側でつける名前です。  
任意の名前をつけられますが、慣例として、 origin が使われます。  

(滅多にやりませんが)複数のリモートブランチと関連づけることも可能ではあります。  
その場合は、 origin 以外の、別の名前をつけることになります。  

***

メモ:
Windows11の場合、git に関連づけられた認証情報は、「資格情報マネージャー」にあります。