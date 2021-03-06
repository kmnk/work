# unity1weeks 2018/06/04T00:00:00 - 2018/06/10T20:00:00
[Unity 1week Game Jam](https://unityroom.com/unity1weeks) に参加する

いきなりやるので良いものを作るのは難しいだろうが、これを経ずしてこれから何して生きていくつもりなのだ、という話なので、計画を建ててやる

今回は完成させて、投稿することが一番の目標。面白さは二の次とは言わないまでも、それを優先しすぎて投稿を諦めるということは許さないこととする

また、最近忙しいので、仕事や健康に支障が出るようなスケジューリングはしない。あくまで自由時間だけで完成させられる目標設定をする

- __done__ unityroom にユーザー登録する
- __done__ 使える時間の算段を立てる
    - 6/3(日) お題の確認と連想書き出しのみ
    - 6/4(月)〜/8(木) 終業19時頃〜24時頃まで
        - 6/8(金) 午後は私用で時間が多くはとれないかも
        - 1h 位は Splatoon2 基礎練習しておきたい
        - 更に 1h イラストの基礎練習をしたい
        - 更に 1h 筋トレもしたい
        - 通勤は 1.5h 位
        - 実質5h位？..だと無理なので削らないと
            - 筋トレはアイディア出しながらやる
            - Splatoon2 練習は .5h に減らす
            - イラストの練習は布団に入ってから寝るまで（24時〜1時）にやる
        - 3 * 5h = 15h 位
    - 6/9(土) は1日空くはず
        - Splatoon2 のフェスの日じゃ？
        - 8h 取れれば御の字
    - 6/10(日) も一日空くはず
        - 仕上げをしてもよいが、余りここに頼りたくない
        - もう投稿できる状態にして、クオリティ上げ程度にしていおきたい
        - 自己振り返りを2h位するので、 6h 位か
    - 大体取れて 30h 位の作業時間で仕上げる必要がある
        - 一日ごとに 3h 以上削れていくことを想定しながら作業する
- __done__ おおよその流れ、計画を想像して立てる
- __done__ 実装用のプロジェクトを作成、 github でバージョン管理できるように準備しておく
    - [作った](https://github.com/kmnk/unity1weeks_20180604)
    - Unity のバージョンは 2018.1.2f1 にする
- __done__ 6/3 の 24時 にお題を確認する。ざっと連想されるキーワードやアイディア、ギミックを書き出す
- __done__ 紙に簡単なモックを書き出し、ゲーム性を創出する
    - ゲームの実装を検討し、作れそうかどうかも判断
        - 技術的な挑戦を入れるとおそらく無理になる。投稿最優先
        - ただし、実務関連上 UniRx を使う前提で考える
    - 弾幕避けゲームが作りたい。やっぱり
        - ぎりぎりで避けるほど点数が高いのがゲーム性
            - [【これならできる】unityの2Dゲームで背景画像を多重スクロールさせる](http://noranuk0.hatenablog.com/entry/2016/10/24/225249)
            - [Re:ゼロから始める弾幕アルゴリズム　～　Unityで作る弾幕STG](http://noranuk0.hatenablog.com/entry/2016/10/29/235004)
- __here__ デザイン性は無視し、簡易なオブジェクトで実装する
    - 必要な素材
        - 自機: [Unityちゃんのドット絵](http://unity-chan.com/download/index.php) があったはず
        - 敵機: 同上
        - 弾: 適当にフリー素材を探す。真ん中が明るくて外側が暗い感じのドット絵
        - 背景: 適当に用意
    - 必要な技術、実装
        - 弾幕計算
        - 当たり判定、ぎりぎり判定
        - 前進してる感。背景の動き
        - 自機、敵機の動き／操作
        - スタート、インゲーム、ゲームオーバー、結果
    - __done__ Unityちゃんアセットを取り込んでデータ確認
    - __done__ キャラ配置と操作を実装する
        - 配置は x:3, y:1 くらいっぽい。
        - UnityChan の用意されているアニメーションを使うとすぐUnityが落ちるので一旦四角と丸で作る
    - __done__ 敵機を配置する
    - __done__ 弾幕を出力できるようにする
    - __done__ 敵がよしなに弾を撃つようにする
    - __done__ 移動制限をつける
        - 実は [ここ](https://unity3d.com/jp/learn/tutorials/projects/2d-shooting-game/limiting-player-movement-and-other-corrections) に書いてあることがそのままな気がする..
    - __done__ 敵がランダムに弾を撃つようにする
    - __done__ 当たり判定と負けを実装する
        - 当たり判定を追加したら重くなった
            - 数を減らして微妙に解決
- ゲーム性をより高める実装をする
- エフェクト、効果音を入れる
- バグとり、パフォーマンス向上
- デザインを良くする
- unityroom へ投稿する
