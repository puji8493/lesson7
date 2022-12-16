# git でのバージョン管理 init 編

| 用語 | ざっくりとした意味 |
| ---- | ---- |
| リポジトリ | 更新情報の「貯蔵庫」のこと。 |
| ワーキングツリー | 作業中のディレクトリのこと。 |
| ブランチ | 枝分かれした枝のうちのひとつ。<br><span style="color:red">ただし、文脈によっては、その枝の「最先端」を指すこともある。</span> |
| コミット | 個々の「変更記録」のこと。 |
| インデックス | 次のコミットに含めるファイルの置き場のこと。<br>「ステージングエリア」とも言う。 |

***

## git でのバージョン管理を開始する

| コマンド | 機能 | コマンド実行例 | 
| ---- | ---- | ---- | 
| `git init` | 空のリポジトリを作ります。 | `git init` |
| `git status` | 現在の working tree の状態を確認します。 | `git status` |

プロジェクトの git でのバージョン管理を開始します。

バージョン管理したいプロジェクトのディレクトリに移動してください。  
そして、以下のコマンドを実行してください。

```bash
git init
```

これで、プロジェクトのディレクトリに `.git` ディレクトリが作成されます。  
この `.git` ディレクトリには、git で管理する情報が格納されます。  
この情報格納先のことを、リポジトリと言います。  
(リポジトリの中身を直接見たり編集したりすることはありません)

## プロジェクトの状態を確認する

git で管理されているプロジェクトの状態を確認するには、以下のコマンドを実行します。

```shell
git status
```

以下は、 `git init` 直後に `git status` を実行した場合の例です。

```shell
PS D:\git_lesson> git status
On branch master

No commits yet

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        11_introduction.md
        21_install_and_seettings.md
        31_init_add_commit.md
        img/
```

`On branch master` と表示されています。  
「master という名前のブランチにいるよ」という意味です。  
mater というのは、デフォルトで作られるブランチの名称です。 main という名称になることもあります。  
「ブランチ」とは、「枝分かれした枝のうちのひとつ」の、「最先端」のことです。  
とはいえ、「最先端」どころか、「枝分かれ」どころか、まだ、「コミット」すら一度もしていません。  
なので、これ以上説明しようがありません。いったんスルーします。  

次に `No commits yet` と表示されています。  
コミットとは、個々の「変更記録」のことです。  
「まだ、コミットが一度もされていないよ」という意味です。

そのあと、 `Untracked files:` ということで、ファイルがリストされています。

`(use "git add <file>..." to include in what will be committed)` とは、「git add ... というコマンドによって、(以降に行われる)コミットに含まれるべきファイルを含めよ」という意味です。  

ということで、これから、 `git add` して、 `git commit` してみましょう。

***

## add して commit する

| コマンド | 機能 | コマンド実行例 | 
| ---- | ---- | ---- | 
| `git add` | ファイルをインデックスに追加します。 | `git add -A` |
| `git commit` | リポジトリに変更を記録します。 | `git commit -m "○○の機能を追加した"` |

まずは、 `git add` コマンドを実行してみましょう。  
たいていの場合、 -A オプションをつけます。  
新規に追加されたファイル/更新されたファイルをすべて含められるので便利です。  
`git add -A` で、実質、ひとつのイディオムのようなものです。

```shell
git add -A
```

そして、もう一度 `git status` を実行してみます。  
以下のような表記に変わりました。

```shell
PS D:\git_lesson> git status
On branch master

No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
        new file:   11_introduction.md
        new file:   21_install_and_seettings.md
        new file:   31_init_add_commit.md
        new file:   img/without_git.png
```

`Changes to be committed:` という表示があって、そのあと、 `new file: xxx` という記述が複数続いています。  
これは、インデックスに新規にファイルが追加されたよという意味です。

それでは、このまま、コミットしてみます。

```shell
PS D:\git_lesson> git commit -m "最初のコミット"
[master (root-commit) 39eb905] 最初のコミット
 4 files changed, 253 insertions(+)
 create mode 100644 11_introduction.md
 create mode 100644 21_install_and_seettings.md
 create mode 100644 31_init_add_commit.md
 create mode 100644 img/without_git.png
```

`-m` オプションのあとのコミットメッセージは必須です。  
コミットメッセージは、あとから振り返ったときに、どういう趣旨の変更か分かるように記述します。

無事に `git commit` に成功したら、改めて `git status` コマンドを実行してみましょう。

```shell
PS D:\git_lesson> git status
On branch master
nothing to commit, working tree clean
```

`git add` すべき対象がない場合は、上に示したようなシンプルな表示になります。  

ここで、さらに、ファイル「31_init_add_commit.md」を編集してみます。

それから、 `git status` を実行してみましょう。

```shell
PS D:\git_lesson> git status
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   31_init_add_commit.md
```

今度は `new file: xxx` ではなく、 `modified: xxx` になっていますね。

では、再び、 `git add -A` して、 `git commit` してみます。  
`git status` もしてみましょう。

```shell
PS D:\git_lesson> git add -A
PS D:\git_lesson> git commit -m "解説文を追加"
[master 32ccfdf] 解説文を追加
 1 file changed, 36 insertions(+), 1 deletion(-)
```

さらに、 .md ファイルに修正を加えます。  
そして、 `git add -A` して、 `git commit` してみます。  
`git status` もしてみましょう。

```shell
PS D:\git_lesson> git add -A
PS D:\git_lesson> git commit -m "解説文をさらに追加"
[master 50b8275] 解説文をさらに追加
 1 file changed, 39 insertions(+), 3 deletions(-)
PS D:\git_lesson> git status
On branch master
nothing to commit, working tree clean
```

***

## git log

| コマンド | 機能 | コマンド実行例 | 
| ---- | ---- | ---- | 
| `git log` | コミットのログを表示します。 | `git log` |

これまでに、3回のコミットをしました。  

`git log` コマンドは、コミットのログを表示します。  
実行してみましょう。  

```shell
PS D:\git_lesson> git log
commit 50b82759c32348d9fc24d40e3617b23547909c70 (HEAD -> master)
Author: k-ogawa <k.brahma.nirvana@gmail.com>
Date:   Sun Dec 11 21:19:15 2022 +0900

    解説文をさらに追加

commit 32ccfdf2d5b8153e18fad64a42a48f17a08ba817
Author: k-ogawa <k.brahma.nirvana@gmail.com>
Date:   Sun Dec 11 21:08:37 2022 +0900

    解説文を追加

commit 74dd8f09c4419000ab3cf96d1fc809389f8f43cc
Author: k-ogawa <k.brahma.nirvana@gmail.com>
Date:   Sun Dec 11 20:47:57 2022 +0900

    最初のコミット
```

`commit xxxxx ` という表記は、そのコミットを参照するとき用のハッシュ値です。  

log の中には、 `(HEAD -> master)` という文字列が後ろに続いているものもあります。  
HEAD とは、今作業中のディレクトリがこのコミットと同じだということを意味しています。

***

### git checkout

| コマンド | 機能 | コマンド実行例 | 
| ---- | ---- | ---- | 
| `git checkout` | コミットのログを表示します。 | `git checkout master`<br>`git checkout 74dd8f09c4419000ab3cf96d1fc809389f8f43cc` |

`git checkout` というコマンドで、ワーキングツリーを、特定のコミットがされたときの状態に戻すことができます。

引数には、ブランチ名またはハッシュ値を使います。  

ブランチ名を使った場合は、そのブランチの最新のコミットのときの状態になります。  

```shell
git checkout master
```

- <span style="color:red">ブランチ名を使う場合がほとんどです</span>
- <span style="color:red">今は1つしかブランチがないですが、「枝分かれ」して複数のブランチが出てくるようになると、この方法での切り替えはとても便利です</span>

ハッシュ値を使った場合は以下のようになります。

```shell
git checkout 74dd8f09c4419000ab3cf96d1fc809389f8f43cc
```
ただし、ハッシュ値を使ってワーキングツリーの状態を変更したときは、 <span style="color:red">detached HEAD </span>という状態になります。  
<span style="color:red">detached HEAD 状態でのファイルの編集は、反映されません。  
編集内容をコミットできませんし、他のコミットに移動した瞬間、行ったすべての編集は破棄されます。</span>

対策としては、<span style="color:red">detached HEAD になったら、そのコミットから新たにブランチを作り、そして `git add` して `git commit` することになります。</span>
この件は、初心者のうちのハマりポイントのひとつです。  
改めて後ほど解説したいと思います。
