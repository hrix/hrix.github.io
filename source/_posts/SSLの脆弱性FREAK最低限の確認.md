title: SSLの脆弱性FREAK最低限の確認
date: 2015-03-05 10:18:29
tags:
---
SSLの深刻な脆弱性「FREAK」というのが話題になっています。
対策できていない場合、SSL通信が乗っ取られる危険があるので関係するWebサーバはチェックしておくとよいです。

これのチェック方法・対応ですが
CentOS6/Apacheの組み合わせであれば、以下のような対策が考えられます。

### ①適当なサーバから問題の暗号形式になっていないかチェック

```
$ openssl s_client -connect [対象のドメイン]:443 -cipher EXPORT
```
※結果
> handshake failureとでて15行ぐらいで終わったら問題なし、
そうではなく、たくさん暗号が出て
> Server Temp Key: RSA, 512 bits
など出たら、問題ありです。
※Apacheの場合ssl.conf（CentOS6）ではデフォルト
> SSLCipherSuite ALL:!ADH:!EXPORT:!SSLv2:RC4+RSA:+HIGH:+MEDIUM:+LOW
となってあってこれが効いていれば問題なしですが、
設定の仕方によって無効になってしまっている場合もあるので
SSLCipherSuiteを有効になるよう調整するなど確認が必要です。


### ②（CentOS6/7）2015/1/21にopensslのモジュールアップデートが出ているのでアップデートする

```
# yum update openssl
```

* ①が問題なければ②はそれほど急がなくてもよいかと。
* 以下がまとまっていて分かりやすいかと思いました。
http://d.hatena.ne.jp/Kango/20150304/1425448983
