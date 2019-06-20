# write-atcoder-selection-by-rust

Rust を用いて [AtCoder に登録したら次にやること ～ これだけ解けば十分闘える！過去問精選 10 問 ～](https://qiita.com/drken/items/fd4e5e3630d0f5859067) を解く

環境構築は [AtCoder に登録したら解くべき精選過去問 10 問を Rust で解いてみた](https://qiita.com/tubo28/items/e6076e9040da57368845) を参考にして、 [github](https://github.com/kmnk/docker-rust-sandbox) に作成済み

既に Rust に慣れている人なので、解答がスタイリッシュだけれど、解答例も [AtCoder に登録したら解くべき精選過去問 10 問を Rust で解いてみた](https://qiita.com/tubo28/items/e6076e9040da57368845) に載っている

ファイル構成等まだよくわかっていないので、 main.rs で解凍＆実行して、解けたら別ファイルにコピペして残す、というようなフローでやっていく

- __done__ [第6問](https://qiita.com/drken/items/fd4e5e3630d0f5859067#%E7%AC%AC-6-%E5%95%8F--abc-088-b---card-game-for-two-200-%E7%82%B9)
    - 問題: https://beta.atcoder.jp/contests/abc088/tasks/abc088_b
    - 自分の解答: https://beta.atcoder.jp/contests/abc088/submissions/2860164
        - https://github.com/kmnk/docker-rust-sandbox/blob/master/projects/atcoder/src/abc_088_b.rs
    - 模範解答: https://qiita.com/tubo28/items/e6076e9040da57368845#%E7%AC%AC-6-%E5%95%8F-abc-088-b---card-game-for-two-200-%E7%82%B9
        - 配列の読み取りがスマート `let mut a: Vec<u32> = (0..n).map(|_| read()).collect();`
        - ソートに reverse を使わず comparer を渡している `a.sort_by(|x, y| y.cmp(x));`
        - for 文の条件がちょっと違う `for (i, &x) in a.iter().enumerate() {`
            - a の iterator を作ってそれを enumerator にすることで、 index と値(x) を同時に受け取って、 for 文の中に入っている？
- __done__ [第7問](https://qiita.com/drken/items/fd4e5e3630d0f5859067#%E7%AC%AC-7-%E5%95%8F--abc-085-b---kagami-mochi-200-%E7%82%B9)
    - 問題: https://beta.atcoder.jp/contests/abc085/tasks/abc085_b
    - 自分の解答: https://beta.atcoder.jp/contests/abc085/submissions/2862688
    - 模範解答: https://qiita.com/tubo28/items/e6076e9040da57368845#%E7%AC%AC-7-%E5%95%8F-abc-085-b---kagami-mochi-200-%E7%82%B9
        - HashSet ではなく BTreeSet というのを使っている。こちらは Ord （比較可能）であることが条件なので、より実現可能性が高い
            - HashSet は Hash 値計算可能であることが条件
- __done__ [第8問](https://qiita.com/drken/items/fd4e5e3630d0f5859067#%E7%AC%AC-8-%E5%95%8F--abc-085-c---otoshidama-300-%E7%82%B9)
    - 問題: https://beta.atcoder.jp/contests/abc085/tasks/abc085_c
    - 自分の解答: https://beta.atcoder.jp/contests/abc085/submissions/2872087
        - https://github.com/kmnk/docker-rust-sandbox/blob/master/projects/atcoder/src/abc_085_c.rs
    - 模範解答: https://qiita.com/tubo28/items/e6076e9040da57368845#%E7%AC%AC-8-%E5%95%8F-abc-085-c---otoshidama-300-%E7%82%B9
        - ラベルを使ってちゃんと全体を抜けている（自分のでは最後の答えになっていたので、問題は満たしているがバグっている）
        - `Some` と `unwrap_or` というのを使い、スマートに書いている（自分のでは a, b, c という変数をそれぞれで使っている）
            - 参考: https://qiita.com/tatsuya6502/items/cd41599291e2e5f38a4a
- __done__ [第9問](https://qiita.com/drken/items/fd4e5e3630d0f5859067#%E7%AC%AC-9-%E5%95%8F--abc-049-c---daydream-300-%E7%82%B9)
    - 問題: https://beta.atcoder.jp/contests/abc049/tasks/arc065_a
    - 自分の解答: 解けなかった
    - 模範解答: https://qiita.com/tubo28/items/e6076e9040da57368845#%E7%AC%AC-9-%E5%95%8F-abc-049-c---daydream-300-%E7%82%B9
- __done__ [第10問](https://qiita.com/drken/items/fd4e5e3630d0f5859067#%E7%AC%AC-10-%E5%95%8F--abc-086-c---traveling-300-%E7%82%B9)
    - 問題: https://beta.atcoder.jp/contests/abc086/tasks/arc089_a
    - 自分の解答: https://beta.atcoder.jp/contests/abc086/submissions/2923030
    - 模範解答: https://qiita.com/tubo28/items/e6076e9040da57368845#%E7%AC%AC-10-%E5%95%8F-abc-086-c---traveling-300-%E7%82%B9
        - やってることは同じ。むしろコード的には自分の方がシンプル
        - 但し、 tuple の Vector を使ったり map を使ったり、 windows を使って同時に2つずつの配列をとるイテレーターを作って使ったりと、 Rust 的な書き方をしている
- __pend__ [ABC103](https://abc103.contest.atcoder.jp/assignments) で解けなかった C, D を解説を見つつ実装する
    - むずかしいのでまた今度
- __here__ [追加過去問](https://qiita.com/drken/items/fd4e5e3630d0f5859067#%E3%81%93%E3%81%93%E3%81%BE%E3%81%A7%E8%A7%A3%E3%81%84%E3%81%9F%E3%82%89)
    - 問題: https://beta.atcoder.jp/contests/abc075/tasks/abc075_b
        - 解答: https://beta.atcoder.jp/contests/abc075/submissions/2975860
        - 解説: https://img.atcoder.jp/abc075/editorial.pdf
        - 考察:
            - index の対応を持った配列を定数と定義しておき、それをループすることで if 文を書く代わりにしている
            - それ以外はそれほど変わらない
        - 考察を踏まえた解答: https://github.com/kmnk/docker-rust-sandbox/blob/master/projects/atcoder/src/abc_075_b.rs
    - 問題: https://beta.atcoder.jp/contests/abc096/tasks/abc096_c
        - 解答: https://beta.atcoder.jp/contests/abc096/submissions/3020906
        - 解説: https://img.atcoder.jp/abc096/editorial.pdf
        - 考察:
            - 前の解答を流用すれば簡単に解けた。問題なし
    - 問題: https://beta.atcoder.jp/contests/abc070/tasks/abc070_b
        - 解答: https://beta.atcoder.jp/contests/abc070/submissions/3049083
        - 解説: https://img.atcoder.jp/abc070/editorial.pdf
        - 考察:
            - max, min を使ったほうが効率よくシンプルに書ける
            - 0秒の条件は最初に除外せずとも、負にならないように考えれば良い
                - 但し、その場合負を考えないといけないので unsigned な型を使えなくなる
        - 考察を踏まえた解答: https://beta.atcoder.jp/contests/abc070/submissions/3049099
    - 問題: https://beta.atcoder.jp/contests/abc055/tasks/abc055_b
        - 解答: https://beta.atcoder.jp/contests/abc055/submissions/3057423
        - 解説: https://atcoder.jp/img/arc069/editorial.pdf
        - 考察:
            - ビット数を考慮しないと u32 で計算してオーバーフローさせてエラーになってしまう
            - 10.pow(9) + 7 で割った余りが必要なとき、オーバーフローしたあとはいくら掛けても余り以上の部分は切り捨てることになるので、常に余りを出し続けて良い
                - ..というのを理解していると簡単に解けるはず
    - 問題: https://beta.atcoder.jp/contests/abc046/tasks/abc046_b
        - 解答: https://beta.atcoder.jp/contests/abc046/submissions/3089032
        - 解説: http://arc062.contest.atcoder.jp/data/arc/062/editorial.pdf
        - 考察:
            - u16 でやったところ、オーバーフローしたので両方の変数を u32 にした
    - 問題: https://beta.atcoder.jp/contests/abc048/tasks/abc048_b
        - 解答: https://beta.atcoder.jp/contests/abc048/submissions/3103523
        - 解説: https://atcoder.jp/img/arc064/editorial.pdf
        - 考察:
            - f(b) - f(a-1) として解く
            - f は関数を書く
        - 考察を踏まえた解答: https://beta.atcoder.jp/contests/abc048/submissions/3103553
    - 問題: https://beta.atcoder.jp/contests/abc060/tasks/abc060_b
        - 解答: わからなかった
        - 解説: https://atcoder.jp/img/arc073/editorial.pdf
        - 考察:
            - 途中までは考えたが、数列になるな、もっとうまい方法があるのかな、というところで思考を止めてしまった。方向性はそれで良い
            - A%B, 2A%B, 3A%B, ..., (k+B)A%B, ... と考えた時に (k+B)A%B = (kA + BA)%B = kA%B であるので最初のB個を割り切れるか調べる
        - 考察を踏まえた解答: https://beta.atcoder.jp/contests/abc060/submissions/3107503
    - 問題: https://beta.atcoder.jp/contests/abc065/tasks/abc065_b
        - 解答: https://beta.atcoder.jp/contests/abc065/submissions/3130561
            - 解けていたが、自信が持てずに解説を見てしまった。ただ、それでも不正解
        - 解説: https://atcoder.jp/img/arc076/editorial.pdf
        - 考察:
            - 1..n で for していたため、 n 回目が計算されていなかった
            - 仕様をちゃんと読んでおらず、回数の計算を間違えていた
            - と思ったら合っていた。解説の実装が間違っている
        - 考察を踏まえた解答:
            - https://beta.atcoder.jp/contests/abc065/submissions/3130685
    - 問題: https://beta.atcoder.jp/contests/abc087/tasks/arc090_a
        - 解答: https://beta.atcoder.jp/contests/abc087/submissions/3177237
        - 解説: https://img.atcoder.jp/arc090/editorial.pdf
        - 考察: 特になし
    - 問題: https://beta.atcoder.jp/contests/abc098/tasks/arc098_a
        - 解答: https://beta.atcoder.jp/contests/abc098/submissions/3190080
            - 実行時間超過で不正解
        - 解説: https://img.atcoder.jp/arc098/editorial.pdf
        - 考察:
            - 計算時間（量）を考えると全走査してはだめ
            - 初期状態を計算してから位置に対して現在の値を計算し直すようにすると計算量が O(N) になる
        - 考察を踏まえた解答
            - https://beta.atcoder.jp/contests/abc098/submissions/3190224
    - 問題: https://beta.atcoder.jp/contests/abc079/tasks/abc079_c
        - 解答: https://beta.atcoder.jp/contests/abc079/submissions/3274221
        - 解説: https://img.atcoder.jp/abc079/editorial.pdf
        - 考察:
            - 高々8通りなので全部試せとあった。はい
        - 考察を踏まえた解答: 特になし