# 前提
* Android Studioとgithubとの連携が行えていること（[参考](https://github.com/taikai-m/documents/blob/master/HowToUseGitHub.md)）
* Source Treeがインストール済みであること([公式サイト](https://ja.atlassian.com/software/sourcetree))

# 目次

1. 取り組むissueを決める
2. deveropブランチからissue用のブランチをきる
3. ソース修正を行う
4. issue用ブランチへプッシュする
5. github上でPull request詳細を書く
6. その他修正点があればプッシュする
7. レビューのためPull requestのラベル等を変更する
8. レビューの結果を待つ

# 1. 取り組むissueを決める
## githubへアクセス

issueタブから取り組む項目を決める。
![28059412-2b706834-665f-11e7-9a05-40085a733cfb](https://user-images.githubusercontent.com/29743842/28710884-adfc1e7e-73c0-11e7-9be5-d5c11077284f.png)

取り組むissue詳細を開き、issue番号を覚えておく。
![28059524-79b61ba6-665f-11e7-8a54-59d640a1298f](https://user-images.githubusercontent.com/29743842/28710889-b1925c9c-73c0-11e7-99e2-f6be45ab782c.png)

# 2. deveropブランチからissue用のブランチをきる
## (1).SourceTreeへローカルリポジトリを設定(初回のみ)
Source Treeを起動し、[New]ボタンから**既存のローカルリポジトリを作成**をタップする。
<img width="481" alt="28059629-bdae7600-665f-11e7-8f35-317fecd999da" src="https://user-images.githubusercontent.com/29743842/28710893-b1d0ca04-73c0-11e7-8d98-1f2040929a3b.png">
ローカルリポジトリを選択してOK
（/Users/[ユーザ名]/AndroidStudioProjects/oisixAndroid/）

## (2).developブランチを最新状態に更新
左側メニューのdevelopブランチが選択されていることを確認し、
画面中央のヒストリーリストの最上部のリストを選択した状態で、[プル]ボタンをタップ。
<img width="1332" alt="28059840-72f93c5c-6660-11e7-934f-06c7d38d22f8" src="https://user-images.githubusercontent.com/29743842/28710890-b1c95652-73c0-11e7-9e5f-8babc6f901ae.png">
## (3).ブランチをきる
[ブランチ]ボタンをタップ。
<img width="1332" alt="28060006-e3929ad0-6660-11e7-9270-371420cc063d" src="https://user-images.githubusercontent.com/29743842/28710892-b1cac74e-73c0-11e7-9009-36ddc5c54b60.png">
以下の設定としてブランチを作成する。※issue番号は#なし
```
現在のブランチ：develop
新規ブランチ：feature/[issue番号]
（他はデフォルトのまま）
```
<img width="767" alt="28060029-f75db338-6660-11e7-9d90-0ae9cca3316d" src="https://user-images.githubusercontent.com/29743842/28710891-b1ca24d8-73c0-11e7-81cc-b8b5177fce20.png">

# 3. ソース修正を行う
 
AndroidStudioでは新規作成したブランチに切り替わっているので 
ソース修正を行う。
**実機における動作テストまで行うこと**
**（工数がかかる場合に進捗示す必要性がある場合はこの限りではない）**

<img width="444" alt="28060327-cacd5afc-6661-11e7-8820-b015d91beefd" src="https://user-images.githubusercontent.com/29743842/28710894-b1ea8fa2-73c0-11e7-80a7-9cadd8cd2868.png">
# 4. issue用ブランチへプッシュする

AndroidStudiodにて変更を行うと、
SourceTreeにて変更点が参照できる

<img width="1102" alt="28061287-13cc9b8e-6665-11e7-97ae-f5419029e106" src="https://user-images.githubusercontent.com/29743842/28710895-b1ed1ccc-73c0-11e7-858d-c4bec7ac5cdb.png">
差分を確認した上で、問題がなければコメントを付与し、コミットする。
<img width="978" alt="28061288-02817daa-6664-11e7-9f02-67f5c0b85b51" src="https://user-images.githubusercontent.com/29743842/28710896-b1ee3e54-73c0-11e7-8bea-edba7f01d1cd.png">　
　
差分がないことを確認し、左側メニューのブランチをタップ
<img width="976" alt="28061389-3f445ff0-6664-11e7-971c-b6b0beb95e3b" src="https://user-images.githubusercontent.com/29743842/28710897-b20b9594-73c0-11e7-985c-4c37dc169185.png">　
　
　
ヒストリー最上段を選択し、それが最後のコミットであることを確認し[プッシュ]ボタンをタップ
<img width="979" alt="28061390-a06faa3c-6664-11e7-9ffa-cb9be86df8ed" src="https://user-images.githubusercontent.com/29743842/28710898-b22ac4d2-73c0-11e7-9953-5678edca8c40.png">　
　
　
プッシュするブランチが新規作成したブランチのみであることを確認し、[OK]ボタンをタップ
**※developのチェックが外れていること**
<img width="977" alt="28061391-a632e4de-6664-11e7-8725-59c827265c07" src="https://user-images.githubusercontent.com/29743842/28710899-b22b9574-73c0-11e7-8642-30a30571945a.png">　
　
# 5. github上でPull request詳細を書く
## (1).githubへアクセス
プッシュされた後にはCompare & pull requestのボタンが表示されるのでタップ
![11](https://user-images.githubusercontent.com/29743842/28062255-4a6ac58c-6668-11e7-81f0-79c5fd4ea945.png)
　

pull requestに関する詳細を記入する。
* タイトルはレビュー前までは「WIP:[タイトル]」と、「WIP:」をつける
* OverViewの**resolve**へは、「#」付きでissue番号を記載する。
* Screenshotsへは、画面説明が必要な場合は添付する。
* Linksへは、参考URLなど
**基本的にpull requestするのは「なぜか」がわかるよう記入する**

右側メニュー設定については
* Reviewers　：　レビュワーを選択
* Assigness　：　アサインは基本的に自分を選択
* Labels　：　作業中である場合は「in progress」（後のレビュー時に変更する）

![28062523-30fafcba-6669-11e7-80ed-75df53e574bc](https://user-images.githubusercontent.com/29743842/28711066-3976af0a-73c1-11e7-8d2d-ca332c03ab79.png)　
　
# 6. その他修正点があればプッシュする

### レビュー段階に達するまで「3.〜〜」と「4.〜〜」を繰り返す

# 7. レビューのためPull requestのラベル等を変更する
Pull requestのタイトルから「WIP:」をとる
![28062663-9d7658ee-6669-11e7-88d0-0b80be2aa494](https://user-images.githubusercontent.com/29743842/28711116-70ecbb32-73c1-11e7-8bbb-91027969c1b5.png)
Labelsを変更する。「in progress」のチェックを外し、「ready for review」のチェックをつける。
![28062667-9f5e82c6-6669-11e7-9c82-1399041976c0](https://user-images.githubusercontent.com/29743842/28711117-712e7ba8-73c1-11e7-98e8-1187b2c80d76.png)
# 8. レビューの結果を待つ

### GLHF！

**※もちろんレビュー時にご指摘いただいた場合は、適宜対応してください。**
