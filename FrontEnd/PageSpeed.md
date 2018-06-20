# フロントエンドのページ速度について（2018/06/17）

参考図書
[超速! Webページ速度改善ガイド](https://www.amazon.co.jp/Web%E3%83%9A%E3%83%BC%E3%82%B8%E9%80%9F%E5%BA%A6%E6%94%B9%E5%96%84%E3%82%AC%E3%82%A4%E3%83%89-%E4%BD%BF%E3%81%84%E3%82%84%E3%81%99%E3%81%95%E3%81%AF%E3%80%8C%E9%80%9F%E3%81%95%E3%80%8D%E3%81%8B%E3%82%89%E5%A7%8B%E3%81%BE%E3%82%8B-WEB-PRESS-plus/dp/477419400X/ref=sr_1_2?ie=UTF8&qid=1529197286&sr=8-2&keywords=%E8%B6%85%E9%80%9F)

## フロントエンドのネットワーク処理の最適化
### ネットワーク処理の最適化 基本３原則
#### データの転送量をなるべく小さく
##### 改善方法
テキストファイルの圧縮
画像ファイルの圧縮
gzipなど

#### データの転送回数をなるべく少なく
##### 改善方法
WebpackなどでのJSファイルの結合
画像の遅延ローディング
CSSスプライト
SVGスプライト

### コンテンツに影響しないスクリプトの非同期実行（async, defer）
参考文献
[<script> タグに async / defer を付けた場合のタイミング - Qiita](https://qiita.com/phanect/items/82c85ea4b8f9c373d684)


####  データの転送距離をなるべく短く
リソースへの事前接続
キャッシュでのリクエスト結果の再利用
CDNからのリソース配信

### ネットワーク処理の流れ
- DNSルックアップ
    - 1. ホスト名の名前解決
    - 2. 対応するIPアドレスの返却
- TCPウェイハンドシェイク
    - 3. ウェブサーバからTCP接続の要求
    - 4. サーバから接続要求に対する返答
    - 5. サーバとTCP接続の開始
- HTTPレスポンス
    - 6. ホスト名の名前解決
    - 7. 対応するIPアドレスの返却

### クリティカルレンダリングパス
Webページの最初のレンダリングが行われるまでに必要な一連の処理。
ページロードジにレンダリング処理に至るまでの時間を指す。

#### 処理の内容
1. HTMLドキュメントのダウンロードと評価
2. サブリソースのダウンロードと評価
3. レンダリングツリーの構築とレンダリング


## スクリプト処理の最適化
### スクリプト処理の最適化の基本方針
* UIブロッキングにつながる長大な処理を避ける
* メモリーリークの回避、GC（Garbage Collection）を把握する


## ネットワーク処理の効率化に役立つテクニック

### Service Worker
参考文献
* [Service Worker の紹介 | Web | Google Developers](https://developers.google.com/web/fundamentals/primers/service-workers/?hl=ja)

### Resource Hints
参考文献
* [Resource Hints API でリソースの投機的取得 | blog.jxck.io](https://blog.jxck.io/entries/2016-02-11/resource-hints.html)  
* [Resource Hintsでリソースを事前取得しよう！ - Qiita](https://qiita.com/ryo_hisano/items/e525616e5026b015aafe)

```html
<link rel="dns-prefetch" href="http://example-domain.com/">
```