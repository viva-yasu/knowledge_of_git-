#Gitのおさらい

- [パッチモード](#パッチモード)
- [空のディレクトリを管理](#空のディレクトリを管理)
- [差分を確認する](#差分を確認する)


## パッチモード
パッチモードとは、ワーキングツリーの変更のあったファイルの差分を表示してくれて、その変更を追加するかどうかを選べるモード。  
あるファイルを変更したけれども、その変更を一つのコミットにしたくないときに使えます。  
パッチモードを立ち上げるコマンドは以下です。  

```
$ git add -p
```
このコマンドを叩くと差分を表示してくれて下の方に
```
Stage this hunk [y,n,q,a,d,/,s,e,?]?
```
といったものが出てきます。  
ここで、ハンクに追加するかどうかを選べます。
入力に対する挙動は、以下の表を参考に。

| type | action |
|:----:|:-------|
|y|その変更をハンクに追加|
|n|その変更をスキップ|
|q|パッチモード終了|
|a|以降の変更をハンクに追加|
|d|以降の変更を拒否|
|/|検索|
|s|表示されている差分を分割する|
|e|エディタを起動し手動で編集|
|?|ヘルプを表示|


## 空のディレクトリを管理
Gitではディレクトリを管理しないけれども、空のディレクトリを残したいときは、そのディレクトリに ***.gitkeep*** という名前の空のファイルを作成すると空のディレクトリをGitに残しておくことができる


## 差分を確認する
差分を確認するには、大きくわけて3種類。
- ステージングエリアとワーキングツリーの間
- ステージングエリアとリポジトリの間
- ステージングエリア&ワーキングツリーとリポジトリの間

一つ目のステージングエリアとワーキングツリーとの間の差分を確認するには下記のコマンド
```
$ git diff
```
オプションもパラメータのなにも付けないで実行すると、ステージングエリアとワーキングツリーとの差分を得れます。

二つ目のステージングエリアとリポジトリとの間の差分を確認するには下記のコマンド
```
$ git diff --cached
```
cachedオプションを付けて実行すると、ステージングエリアとリポジトリとの間の差分を得れます。

三つ目のステージングエリア&ワーキングツリーとリポジトリの間の差分を確認するには下記のコマンド
```
$ git diff HEAD
```
HEADをパタメータに渡して実行すると、ステージングエリア&ワーキングツリーとリポジトリの間の差分を得れる。  
ちなみに、 ***HEAD*** というのは、現在のブランチの最新のコミットを表すキーワードのこと。


表にまとめると

| Case | コマンド |
|:-----|:--------|
|addする前には|$ git diff|
|addしたものがある場合|$ git diff --cached|
|commitしていないものとリポジトリの間を確認したいとき|$ git diff HEAD|
