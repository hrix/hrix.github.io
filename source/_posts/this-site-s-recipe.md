title: "this site's recipe"
date: 2015-04-13 12:48:32
tags:
---
## このサイトの作り方
手軽にブログサイトのようなものを作りたく、githubの機能と静的ページ出力のhexoというフリーソフトで作りました。
1. linux環境を作る（私はwindows7+vagrant+virtualboxで作りました)
1. node.js(nvm)をインストールする
    * 参考 http://liginc.co.jp/web/programming/server/104594
1. hexoをインストールしてブログを作る
    * デザインをいじるためtheme(casper)を追加でインストールしました
1. github pages機能を使うためhrix.github.ioというリポジトリを作る
1. 上記リポジトリをlinux環境にclone
1. hexoでできたファイルを全部cloneしたディレクトリに移し、リポジトリに追加
1. _config.ymlを編集して調整しhexoを立ち上げる。(hexo server)
1. ローカル環境でmdファイルをプレビューしながら編集（utf8で保存すること）
1. 静的ページ(html)発行（hexo generate）
    * theme以下のcssを直した場合、一度全部消して（hexo clean）からgenerateしないとcssの変更は反映されないようです
1. ソースのmdも含めてgithubにpush
    * https://github.com/hrix/hrix.github.io　がリポジトリになります。
    * hexoで静的ページだけをデプロイする仕組みもあるようですが、全部一つのリポジトリに入れることにしました。
そのため、http://hrix.github.io/public/　がトップページになりますが、今回は気にしません。

### 感想
* hexo便利
    * シンプルで動作が軽快なので楽しい
    * 設定ファイル（_config.yml）分かりやすい
* github, mdファイルを使えることは必要
* でも全部で無料できる。

### その後
* hexo3に対応
    * いったん全部記事作り直し
    * hexo-serverが別モジュールになった

