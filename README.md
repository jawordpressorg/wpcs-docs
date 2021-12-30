<!-- 
# WordPress Coding Standards Docs
 -->
# WordPress コーディング規約ハンドブック翻訳作業用リポジトリ

<!-- 
This repo contains the source for the [WordPress Coding Standards](https://developer.wordpress.org/coding-standards/) on https://developer.wordpress.org

When creating new files, these must be added to the [manifest.json](https://github.com/WordPress/wpcs-docs/blob/master/manifest.json) file. 

Removing files also requires updating the [manifest.json](https://github.com/WordPress/wpcs-docs/blob/master/manifest.json) file. After deletion and sync with DevHub, the page also needs to be manually deleted from DevHub.
 -->
これは [WordPress コーディング規約ハンドブック](https://ja.wordpress.org/team/handbook/coding-standards/)の翻訳ファイル用リポジトリです。

## 日本語訳への質問やコメント
[Issues](https://github.com/jawordpressorg/wpcs-docs/issues) から新しい issue を作成してください。[こちら](https://github.com/jawordpressorg/wpcs-docs/issues/new) のリンクをクリックしても作成できます。画面は英語ですが、日本語を入力できます。

または [WordPress の 日本語 Slack](https://ja.wordpress.org/support/article/slack/) 内の #docs チャンネルからも連絡いただけます。

## 日本語翻訳のワークフロー

Takayuki Miyauchi さんの発案された翻訳方式を採用して、ブロックエディターハンドブックのドキュメントを翻訳しています。
https://qiita.com/miya0001/items/4745cf900a66c0bbf8e5

最初の1回だけ
```
% git clone git@github.com:jawordpressorg/wpcs-docs.git
% cd wpcs-docs
% git remote add upstream https://github.com/WordPress/wpcs-docs.git
```
あとは定期的に
```
% git fetch upstream
% git merge upstream/master
```

ここですべてのファイルがマージされる場合でも、どこが変更されたかチェックし、手動で反映する必要があります (例: コードが変更された場合)。画面の出力から「.md」ファイルを抽出して変更一覧を取得します。

すべてのファイルがマージされなかった場合は、以下のコマンドで変更されたファイルの一覧を取得します。
```
% git status | grep \.md | grep -v CHANGELOG
```

変更ファイルの一覧を取得したら、GitHub で最近の変更を確認しながら、日本語版に反映します。
```
% git add -A
% git commit -m "Synched with the latest"
% git push
```

