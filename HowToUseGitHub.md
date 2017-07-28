# GitHubの使い方

※Android Studio及びSourceTreeが既にインストール済み、GitHubへ登録済みが前提の手順です。

手順は以下の通り
1. 秘密鍵・公開鍵の作成
2. 公開鍵をGithubに預ける
3. githubに接続しクローンを作成
4. Android Strdioの起動画面から作成したクローンを参照する
5. エミュレータ上でAndroid版Oisix Appの起動確認
6. Done!


# 1. 秘密鍵・公開鍵の作成
## (1).既に生成されているか確認
terminalを起動し、以下のコマンドを入力。
```
$ ls ~/.ssh
```
**ここで以下のような2つのファイルが存在した場合は、既に秘密鍵・公開鍵は作成されているため以降の(2)の手順は飛ばす。**
```
id_rsa      id_rsa.pub
```

## (2).秘密鍵・公開鍵のペアを生成する
ターミナルで以下のコマンドを実行する
```
$ ssh-keygen -t rsa -C "hogehoge@oisixdotdaichi.co.jp"
```
メールアドレスは自分のメアドに変更する（例： ssh-keygen -t rsa -C “hogehoge@oisixdotdaichi.co.jp" ）

実行すると以下の3つの入力を求められるが、すべて Enter(return) で実用上で良い。
* 鍵ファイルを保存するフォルダ
* パスフレーズ
* パスフレーズ（確認用）

※もしパスフレーズを設定した場合は以下のコマンドを実行し、パスフレーズの入力を省略する設定をしておくと便利です。
```
$ ssh-add ~/.ssh/id_rsa
```

# ２. 公開鍵をGithubに登録する

公開鍵の内容をクリップボードにコピーするため、ターミナルで以下のコマンドを入力
```
// Macの場合
$ pbcopy < ~/.ssh/id_rsa.pub

// Windowsの場合
$ clip < ~/.ssh/id_rsa.pub
```
### SSH Keysの設定ページ
Githubへアクセスし、SSH Keysの設定ページを開く。
![2017-07-28 16 31 53](https://user-images.githubusercontent.com/29743842/28707252-a9131d62-73b2-11e7-89e0-dc8db66e6dc2.png)
1. 右上の自分のアイコンより Settings のページを開く
![2017-07-28 16 31 34](https://user-images.githubusercontent.com/29743842/28707327-e903879a-73b2-11e7-83a9-3e46ccecf5fe.png)
2. 左側のメニューより SSH Keys のページを開く
3. 赤い下線の位置にある [Add SSH Key] のボタンをクリック

### 公開鍵を登録
Add SSH Keyの画面にて以下のように登録する。
<img alt="20140317213538" src="https://user-images.githubusercontent.com/29743842/28047619-44302d84-6626-11e7-9b06-f7fbf1fdb77c.png">
1. Titleは任意の名称を入力（どのPCの鍵かを区別するための名称などなど）
2. Keyの入力欄でクリップボードの内容を Paste する（⌘+v / Ctrl+v等）
3. Add Key ボタンをクリック

### 試しに接続してみる
terminalにて、以下のコマンドを入力。
```
$ ssh -T git@github.com
```
つぎのように表示されたら、yes と入力。
```
The authenticity of host 'github.com (207.97.227.239)' can't be established.
RSA key fingerprint is 16:27:ac:a5:76:28:2d:36:63:1b:56:4d:eb:df:a6:48.
Are you sure you want to continue connecting (yes/no)?
```
接続に成功すると、つぎのようなメッセージが表示される。
```
Hi username! You've successfully authenticated, but GitHub does not
provide shell access.
```
# ３-a．任意のプロジェクトを新規リポジトリとして登録(既存リポジトリを利用する場合は3-bへ)
Android Studioを起動し、新規リポジトリとして登録したいプロジェクトを開いておく。

画面上部のVCSメニューから
「VCS」 -> 「Import into Version Control」 -> 「Share project on GitHub」
と選択。
<img alt="2017-07-28 16 41 40" src="https://user-images.githubusercontent.com/29743842/28707645-249841c8-73b4-11e7-8bb5-57a2a30e7c73.png">

何やらGitHubのアカウントでログインしろ、って言われるのでいう通りにしてください。

新しいリポジトリーの名前と説明（Description）を入力してください。
<img width="426" alt="2017-07-28 16 54 37" src="https://user-images.githubusercontent.com/29743842/28708010-7c7b9038-73b5-11e7-8109-43887a3ee635.png">

これで新規リポジトリーは作成されました。
「5.SourceTreeとの連携」へ！

# ３-b．githubに接続しクローンを作成(既存のリポジトリをAndroidStudioと連携する場合)
## クローンの作成
GitHubへアクセスし、複製したリポジトリを表示する。
画面右側にあるClone or downloadを押下すると表示されるダイアログを確認。

![28047678-aa780bde-6626-11e7-847d-de26dbd71604](https://user-images.githubusercontent.com/29743842/28707814-c2659c5c-73b4-11e7-9b09-072515ab5cc1.png)

右上のUse SSHを押下して「Clone with SSH」の表示を確認後、URLをコピーする
![28047683-bcfde580-6626-11e7-8222-d089589582bb](https://user-images.githubusercontent.com/29743842/28707827-d0cb2258-73b4-11e7-8172-1f33caa39f8a.png)

ターミナルを開いて、以下のコマンドを入力
```
$ cd AndroidStudioProjects/
```
コマンド「git clone」に引数として先ほどクリップボードにコピーしたURLをペーストする
```
$ git clone git@github.com:hoge/hogehoge.git
```
これでクローン作成が完了！

## Android Studioから生成したクローンを参照する

Android Studioの最初の画面で
Open an existing Android Studio project
<img alt="2017-07-10 19 42 03" src="https://user-images.githubusercontent.com/29743842/28047744-3df5876a-6627-11e7-8b48-29d17c7f79b2.png">

さっきクローンしたフォルダを選択

(/User/[ユーザ名]/AndroidStudioProjects/hogehoge)

# 5.SourceTreeとの連携
## SourceTreeへローカルリポジトリを設定(初回のみ)
Source Treeを起動し、[New]ボタンから**既存のローカルリポジトリを作成**をタップする。
![００](https://user-images.githubusercontent.com/29743842/28059629-bdae7600-665f-11e7-8f35-317fecd999da.png)

ローカルリポジトリを選択してOK
（macだったら「/Users/[ユーザ名]/AndroidStudioProjects/hogehoge/」）

# Done!
