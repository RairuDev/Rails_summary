# Railsの実務で学んだことやテクニックについて書いていく

## まず実務に取り掛かるにあたっての心構え

### 1人で悩みすぎない
- 実務は基本的に期日があるので、悩みすぎてスケジュールが遅れるのが1番迷惑となります。
- 報告は細かくしていこう、また遅れているときは遅れている原因も一緒に報告できたら良さそう

### 人に質問するときはわかりやすく簡潔に
- 先輩たちの時間を奪わないように分かりやすく！！  

- ポイントとしては結論から話す事や太字・句読点・改行を使って文字が詰め詰めにならないように！！

- エラーの場合はエラーログを調べて調査してから質問をする

### 先方へのPRを作成するときは慎重に、レビューをもらう前にこれだけは確認しよう!!

- コミットメッセージは綺麗か

- そもそも仕様をもれなく満たしているか

- 変数名は適切か？・N＋1(バックエンドなら)等は起きていないか？

- ブランチ名に問題はないか

- PRを作成する先を間違ってはいないか

### まずチケットに取り掛かる前に、下記の記事を読んでおくと良さそう

[【新人プログラマ応援】開発タスクをアサインされたらどういう手順で進めるべきか](https://qiita.com/jnchito/items/017487cd882091494298)


## 便利なメソッド等のまとめ

### モデル・DB（リレーション）周りはここら辺押さえておくと良さそう
- [scope](https://qiita.com/ngron/items/14a39ce62c9d30bf3ac3)
- [Railsで別名の外部キーを設定する方法](https://qiita.com/j-sunaga/items/ee1fb558807c04243f0f)
- [polymorphic](https://qiita.com/sibakenY/items/7d984267995e8ce408c2)
- [inverse_of](https://www.sejuku.net/blog/66868)

### その他の便利なメソッド
- pluck
- all?
- [Railsで変数の中身が空か確認する空チェックメソッド4種](https://materializer.co/lab/blog/27)
- to_sql→ActiveRecordのオブジェクトに対して使うことでSQLを見ることができる(主にデバックで確認するように使う)
- inspect→ActiveRecordのオブジェクトに対して使うことでオブジェクトの中身を確認できる(主にデバックで確認するように使う・めっちゃおすすめ)
- [配列の要素と何番目にあるかを一緒に取り出す_each_with_indexメソッド](https://satoru103.hatenablog.com/entry/2020/02/09/225503)
- [ぼっち演算子でNIlエラーを回避する](https://qiita.com/yoshi_4/items/e987b698c1978d248cfc)(割と使う)




### SQLを扱うならここら辺押さえておくと良さそう

- N+1対策はここら辺を使えば問題ない（includes・preload・eager_load）
- [ActiveRecordのjoinsとpreloadとincludesとeager_loadの違い](https://qiita.com/k0kubun/items/80c5a5494f53bb88dc58)
- [joins](https://qiita.com/yuyasat/items/c2ad37b5a24a58ee3d30)
- この記事も良さそう[joinsメソッドの使い方 ~ テーブル結合からネストまで学ぶ](https://pikawaka.com/rails/joins)
- 生のSQLをRailsで使う
= <<-"EOS"
- [eachは空の配列でも[]でも対応可能だから、条件分岐等で場合分けは不要](https://teratail.com/questions/168508)

  (個人的にView側で使う機会が多い気がしている)
- map(個人的にはあまりSQLで使う印象はないカナー)
- [論理削除したデータを扱う](https://www.task-notes.com/entry/20170813/1502618254)
- [関連テーブルの条件をON句に書きたい！](https://blog.logicoffee.tech/posts/programming/scoped-association.html)
- [present?とexists?のSQLでデータ取得する際のパフォーマンスの違い](https://mikamisan.hatenablog.com/entry/2017/09/26/223137)
- [SQLをRailsで扱う時の色々な便利なもの](https://qiita.com/yut_h1979/items/4cb3d9a3b3fc87ca0435)
- [find_by_sqlでRailsから生SQLクエリを直接実行する](https://qiita.com/natsuokawai/items/7bc330e9a6f6f4ef0359)

  (基本的にRailsで既存であるメソッドでSQLを組むことを推奨)
  (どうしても厳しい場合や複雑なSQLを組むときはプレースホルダー等を用いて動的に変更できるようなSQLを書いていく)

### ソースコードの書き方




## ソースコードの読み方

## プログラミングの考え方編
[中／大規模開発のためのRails設計パターン](https://qiita.com/ktsujichan/items/2899d337ecbd90474c46)

### エラーが出たときはログを確認
バックエンドORフロントエンドどちらでエラーが出ているか？


### その他実務で見たもの
- [バッチの実行方法などで使う(rails-runner)](https://qiita.com/port-development/items/61c0f74c123955f45f8e)
- [rails-runnerに引数を持たせる方法](http://nomnel.net/blog/rails-runner-keyword-arg/)
- [CanCanCanで特定のユーザーがアクセスできるリソースを制限する](http://319ring.net/blog/archives/2179/)
- [decoratorの使い方](https://qiita.com/ykemoemo/items/b2c5c68f853a5cc91446)

  （例）Viewに関係するメソッドでかつModelに関係するメソッドの記述
  ユーザーの名前とかのフォーマットetc
- [Serializers](https://zenn.dev/emono/articles/8211ad5ec036e9)※重要JSONとしてデータを返す時によく使う
- [attr_accessor](https://qiita.com/Hassan/items/0e034a1d42b2335936e6)

  (Railsでのマイグレーションファイルを作成する際にも自動で使われているはず)
  User.name→この値を取得できるのもgetterメソッドのおかげ

- [I18nで日本語化まとめ](https://qiita.com/Kta-M/items/bd4ba36a58ad602a9d8b)
[i18nで引数を渡して動的にする](https://takuyan.hatenablog.com/entry/20111120/1321741426)

- [ラッパークラスの概念](https://wa3.i-3-i.info/word191.html)

