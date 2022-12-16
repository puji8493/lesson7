# detached HEAD

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
