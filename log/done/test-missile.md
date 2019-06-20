# test missile
[誘導ミサイル完全マスター](https://www.slideshare.net/UnityTechnologiesJapan/unite-2018-tokyo/UnityTechnologiesJapan/unite-2018-tokyo) の講演、面白かったし、自分が Unity 試した時一番最初に作ったのが誘導ミサイル（ただし線形補間）だったのもあり、感慨深かった

ので、物理演算的にミサイルを動かすことを学習することと、それをコンピュートシェーダーで実装することに関してを、自分で試しつつ、サンプルを確認しつつ、学んでみる。まずは触りをやり、より深く突っ込んでみたくなったら続きを考える。3Dは今の所考えなくてもよい（やりたいのは物理計算とコンピュートシェーダーの学習であるため）

今回は敵機の消滅やトレイルのねじれなどもとりあえず考慮しない。ミサイルの軌道を作りたいことに特化する

サンプルは [github に上がっている](https://www.slideshare.net/UnityTechnologiesJapan/unite-2018-tokyo/UnityTechnologiesJapan/unite-2018-tokyo)

- __done__ もう一度講演資料を読み返して、聴いたときの記憶を蘇らせる
    - [誘導ミサイル完全マスター](https://www.slideshare.net/UnityTechnologiesJapan/unite-2018-tokyo/UnityTechnologiesJapan/unite-2018-tokyo) を見る
    - __done__ 作業予定項目を見直す
- __done__ [バネトルクの講演資料](https://www.slideshare.net/UnityTechnologiesJapan/unite-2017-tokyo3d-76689196) を見る
- __done__ テスト用 Unity プロジェクトを作成する
- __done__ 2D 上でテストをするシーンを作成する
- __done__ ミサイルとなるオブジェクトを作成する
- __done__ ミサイルの軌道を実装する
    - とりあえずターゲットを向いて進むようにはなった
    - 常に力をかけ続けているので、バネの作用でどんどん振幅が大きくなってしまっていた
    - 本来は敵機に当たれば爆発したり、時間が経ったら爆発したりで止まるから良いのかな？考える
    - 一応 velocity に制限をかけることで安定はした。が、時限で死ぬ方が正しいと思う
- __done__ ボタンを押したらミサイルを発射して、時間が経ったら消すようにする
- __done__ パフォーマンスがわかるように fps を出す
    - あんまりFPS落ちない。殆どテクスチャ使っていないからか
    - さすがにオートで連射するようにしたらみるみるおちた。ただどのくらい発射されているかわからない
- __done__ ミサイルを管理するクラス、オブジェクトを作る
- __done__ とりあえず、プロジェクトサンプルのコードを眺める
    - `Scripts/MisssileManager.cs` と `Shaders/*.compute` 辺りがキモ。だと思う。が、結構読み解くの大変そう。基礎知識が足りない
    - あとは、 `Shaders/*.cginc` 系でデータ領域の定義をしている
- __pend__ コンピュートシェーダーへの移動を考える
- __pend__ コンピュートシェーダーへ実装する
- __pend__ 動作確認する
