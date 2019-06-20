# implement bookmark denite source
Unite にはある bookmark source を Denite 用に実装。但し、自分的にはカレントディレクトリが変えられれば良いので、それに特化した形で実装する。 [既に cd action はあるとのこと](https://twitter.com/ShougoMatsu/status/998866143963107328) なので、確認しつつ用いる

- __done__ Unite の bookmark source の実装を眺めて、どういう流れで動かしているかを理解する
    - ~/.cache/unite/bookmark 下に、グループごとのファイルを生成している
    - ブックマークファイルの補完が利いてる
- __done__ Denite の source として何をどこまで実装するかを考えて決める
    - やりたいのは、ディレクトリを保存してそこに cd する機能
    - すでに directory kind の action として cd はある
    - 任意のディレクトリのパスを保存して、それを表示し、 directory kind に流し込めれば完成
    - python でファイルにキャッシュする機構はどこかにそれっぽいのあるだろうか
        - 自分で作る？そんな大変じゃないと思うが
    - python で directory か否かを調べるのは `os.path.isdir(path)` でできるっっぽい
    - デフォルトアクションは `-default-action=cd` で指定できる
    - まずは、任意のファイルに名前とパスを書き出して、それを参照して candidates を構成できるようにする
    - 次に、ファイルを分けられるようにする
    - その次に、ディレクトリだけでなく、ファイルも指定できるようにする、かもしれない
- __done__ リポジトリ名決める
    - とりあえず `denite-bookmark`
    - ただ、ディレクトリを保存したいだけなら別の名前にしたほうが良い気がする
- __done__ 決めた実装作業を書き出してリスト化する
- __done__　source ファイルの作成と、仮動作確認
    - kind を directory にして、 `-default-action=cd` をすれば想定する動作を得られた
- __done__ ファイルの書き出しフォーマットを決める
    - json
        - version
        - groups
            - name
            - bookmarks
                - name
                - path
- __done__ キャッシュファイルの位置決めと、デフォルト取得方法の調査
    - `~/.cache/denite-bookmark/bookmark`
- __done__ ファイルの生成方法を実装
- __done__ ファイルからデータを読み込めるようにする
- __done__ 読み込んだデータを source の candidates に変換できるようにする
- __done__ ブックマーク名の入力処理をどう書くか調査
- __done__ ブックマーク名を入力して、そのデータをファイルに書き出せるようにする
    - ほぼできた。あとはリファクタ
    - あと命名
- __done__ `denite#custom#action` の実装を読む
    - https://twitter.com/ShougoMatsu/status/1010736773373104130
    - 基本的には Vim Script としての書き方を想定。Pythonに閉じられない
        - 最終的には共通部分とかは VimScript で書くことになりそうだが、一旦個別の source & kind 実装で乗り切ることにする。 bookmark を追加するときはそのために file 開くし
- __done__ 初めてファイルを作成するときのフローを実装する
    - データ構造のテンプレートを定義する
    - データがない状態で read をした場合に初期構造を返すようにする
- __done__ delete action を実装する
    - file, directory それぞれのデフォルト挙動に delete を追加しないといけないので、個別のファイルがいるか
    - そろそろ共通ライブラリ書いて、そっちの処理で片付けるみたいなことをしたほうが良さそう
        - read, write, add, delete, rename 等、ライブラリ側で書いて kind ではそれを使うのみにすべき
        - じゃないとそろそろ source & kind がカオスになりつつある
    - 名前空間が取れない。 gitn でとってたはずなので参考にする。ちょっとうまくいってない
        - いけた。ちゃんとパスが取れていなかったときと sys モジュールが import できていなかったときとで混ざっていた
    - openable.py にカレントバッファーが empty かどうかを確かめるメソッドがある
- __done__ 良い名前に改名する
    - `directory-mark` とする。良さそう
    - リポジトリを作り直して、ファイルやREADMEを移動＆リネームする
        - だいたいできた
    - `denite-dirmark` にした
- __here__ しばらくドッグフーディングして、問題なければブログの記事に説明を書く
    - そのまえにハイライトを入れる
- リファクタリングして必要のないメソッドや共通処理、設定などをまとめる
    - 将来的にはオブジェクト構造を dictionary のままじゃなく、クラス化したほうが良いかもしれない