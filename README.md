# Prog2kakushin
作成した課題プログラムを公開する場所。
## プログラム1について(12/19 Pandasを用いたプログラム)
今回作成したのは疑似的な辞書作成プログラムです。  
文章を読む時、特に教科書やネット上の参考情報などを読んでいるときに、  
単語の意味だけまとめたことはありませんか？  
このプログラムではテキストデータから自分でやると意外と面倒なこの作業をある程度簡単に、  
かつ重要度を把握しながら行えます。  
このプログラムでは  
1.テキストファイルを読み込み\nなどを削除  
2.任意の品詞に対してその単語とそれぞれの出現回数をカウント  
3.単語と出現回数をデータフレーム化  
4.回数を基に降順でソート  
5.指定した件数だけ上位のデータを抽出
6.意味や読みなど必要なものをデータに追加  
7.データをcsvファイル化、表示  
を行います。　　

テキストデータを用いてプログラムを動作させるため、ファイルを用意してください。  
使用できるファイルは.txtファイルのみです。
事前準備についての説明です。  
```sh
!pip install janome
!pip install Tokenizer
```
  
形態素解析を用いて品詞解析を行うため上記2つをインストールします。  

```sh
%%bash
cat <<EOF > input3.txt
#テキストを入力
EOF
```
このコードでGoogle Colab上ならテキストファイルを作成できます。  
ドライブから個人的に用意しても構いません。  
※上記2つの準備はColab上にも記載しています。  

プログラムを実行した際の出力例です。  
今回はこのREADMEの文章の一部を用いて実行しています。  

| |単語|回数|読み|
|:----|:----|:----|:----|
|0|作成|2|さくせい|
|1|プログラム|2|ぷろぐらむ|
|2|今回|1|こんかい|
|3|の|1|の|
|4|疑似|1|ぎじ|
  
名詞の上位5件を読みデータを追加して表示しています。  

工夫した点は  
・文字化け対策として2種類の文字コードでcsvファイルを出力する  
・例外処理を用意して使用しやすいようにする  
・品詞を指定できるようにする(通常は名詞を想定)  
・単語にフォーカスして辞書のようにする  

といった点です。  
文章要約はあるけれど単語をまとめることはあまりされてないのではと思い作成しました。  
今後さらに改造するとすれば、  
・意味検索などができるAPIの導入  
・形態素解析のより有効的な活用  
・ファイルの導入の簡単化  
などすれば面白いかもしれません。


## プログラム2について(01/09 Numpyを用いたプログラム)
### 微積分プログラム
微積分と結果に基づいてアニメーショングラフを作成します.  
扱えるデータなどの注意点は「使用方法」をご覧ください.
### DEMO
$x^3+5x^2$ の微分についてのデモ  
  
入力および出力  
```bash
式:x**3+5*x**2
微分/積分(b/s):b
微分結果:3*x**2 + 10*x
保存形式:gif/mp4/None(g/m/n)g
```
  
![x^3+5×x^2_微分](https://github.com/e-s-23/Prog2kakushin/assets/153585231/4e6b2dbe-18b9-446f-94b2-6385f6f66ae7)

### ポイント
微積分を手軽に行えます.  
また結果を動的なグラフで表示することによって,  
理解しにくい増減や極値などの要素を視覚的に理解できます.(計算は自力でしてください...)  
またgif,mp4のどちらかでアニメーションの保存ができます.

### 必要ライブラリ
* numpy  
* pandas  
* matplotlib(pyplot,animation,FuncAnimation,PillowWriter)
* IPython.display(HTML)  
* sympy  
* japanize_matplotlib
japanize_matplotlibのみpipでのインストールが必要です.  

Colab環境で以下を実行してください.  
```bash
!pip install japanize_matplotlib
```

その他のライブラリについてはpipは必要ありません.

### 使用方法
work2.ipynbをクローンすればcolab環境上で実行できると思います.  
Colab上で動作するコードとVSCodeで実行できるコードを用意しています.  
動作がColab上では大変遅いこともあるため,その場合はVSCodeの利用も検討して頂けると幸いです.  
以下DEMOでも示したプログラムの入力例です.  

```bash
式:x**3+5*x**2
微分/積分(b/s):b
微分結果:3*x**2 + 10*x
保存形式:gif/mp4/None(g/m/n)g
```
入力値は  
* 数式  
* 微分/積分の選択
* 保存形式の選択
  
の3要素となっています.  
微分を行うならば b,積分を行うならば sを入力してください.  
また保存形式はgifならば g,mp4ならば m,保存をしない場合は nを入力してください.
  
ここから重要な式の入力について説明します.  
前提として, $x$ の定義域は $-10 \leqq x \leqq 10$となっています.  
そして,入力する式が満たさなければならない条件は,  
***文字xのみを含む2次以上の方程式であること***  
のみです.(三角関数などは例外)  
※(y,a,bなどのほかの文字が含まれていてはいけません)  
例) 
| 実行結果 | 入力内容                   | 
| -------- | -------------------------- | 
| 〇       | $x ^ 2$ , $sin(x)$         | 
| ×        | $y ^ 2$ , $sin(y)$ , $x + y$ |  
  
連続性などは考慮する必要はありません.  
ただし,連続性がないものに関しては0除算によるエラー対策をしているため,
グラフが一部おかしくなります.  
(以下 $log(x)$ の微分についての例)  
![log(x)_微分](https://github.com/e-s-23/Prog2kakushin/assets/153585231/09615a65-ad6b-4e98-890a-40577da8255b)  
VSCodeなどであればfigureの拡大・縮小が容易にできるため,   $log(x)$ は $x > 0$ , $\frac{1}{x}$ は $x \neq 0$で描画されていることが確認できます.  
  
式を入力する際の記号などの記法を示します.  
| 実行内容 | 入力内容          | 
| -------- | ----------------- | 
| 和差積商 | +,-,*,/           | 
| 累乗     | **                | 
| π       | pi                | 
| 自然対数 | log()             | 
| 三角関数 | sin(),cos(),tan() | 
| 平方根   | sqrt()            | 

※その他,虚数 $i$ や自然数 $e$ なども入力できますが,  
　今回のプログラムでは0除算対策関連でエラーが発生してしまうため入力しないようにお願いします.  

### 備考など  
#### 作成経緯
微積分が苦手なので計算と増分を視覚的に理解することで,  
学習の手助けになるようなものを作成しようと思いコードを書きました.  
偏微積分や二階以上の微積分, $x$ 以外を含む方程式も解けるようにしようと思いましたが,  
グラフも同時に作るとなるとライブラリの学習もあるため,  
不可能と思い $x$ を含む二次以上の多項式を解けるように作りました.  
classとして使うような加工をすれば他の機能も製作できるかもしれません.  

#### お断り
デバッグが追い付いていないので未知のエラーが大量にある気がします.  
あまりいいコードとは言えない箇所も存在すると思いますがご容赦ください.  


## プログラム3について(01/16 画像処理を用いたプログラム)
### 陣取りゲームプログラム
3×3のボードと手札で陣取りゲームができます.  

### ゲームのルール  
手持ちの手札9枚を駆使して自分の色の陣地を増やします.  
ゲームは全9ターンで構成され,手札を交互に出して進めます.  
同じ手札を何回使用しても構いません.  
すでに色が塗られているマスにも色を重ねることができます.  
1度出すごとに盤面の色が薄まっていきます.  
手札はランダムで作成します.  
色によって有利不利が生まれにくくするために  
・手札は回転可能  
・色付きのマスは9マス中3マス  
の手札が生成されます.  
最終的にすべてのマスのRGB画素平均値をとり,値が大きい方が勝利となります.  
詳しい進め方は使用方法を参照してください.  

### 必要ライブラリ
* numpy    
* sys  
* Opencv2  
pipでのインストールは必要ありません.  

ただしColab環境で画像を表示するために以下を記述しています.  
```bash
from google.colab.patches import cv2_imshow
```

### 使用方法
work3.ipynbをクローンすればcolab環境上で実行できると思います.  
プログラムはColab環境に記述されている順番で実行してください.  
同時に実行させても動作は保証しかねます.  
実行順序は以下の通りです.  
1. 元画像の作成
2. 手札の作成
3. 手札一覧の作成
4. 一人用もしくは二人用のゲームを実行
5. リザルトの表示
手札はランダムで9枚作成されます.

#### 元画像作成  
![Blue](https://github.com/e-s-23/Prog2kakushin/assets/153585231/f3c12f85-d3ac-4ded-ba83-a9355d801962)
![Red](https://github.com/e-s-23/Prog2kakushin/assets/153585231/2c306128-cea1-425e-97b1-5f567df9bb2b)  
手札のもととなる上の画像を作成します.  

#### 手札の作成  
![Blue1](https://github.com/e-s-23/Prog2kakushin/assets/153585231/f7545d67-29b6-4897-8e6a-e9ff03c52870)
![Red1](https://github.com/e-s-23/Prog2kakushin/assets/153585231/5654684e-d7e1-49ca-bbb3-3f941d90d16b)  
手札を作成します.  
色がつくマス目はランダムです.  
被りが発生する恐れがありますが,頑張ってください.  

#### 手札一覧の作成  
<img src="![Blue_grid](https://github.com/e-s-23/Prog2kakushin/assets/153585231/bd7b3a69-a624-46e8-97e9-87dc1c1230c2)" width="150px">
<img src="![red_grid](https://github.com/e-s-23/Prog2kakushin/assets/153585231/a31f685e-1719-460f-b755-35a048211036)" width="150px">  

手札の一覧画像を作成します.  
ファイルから開くなどして見ながらゲームすると楽です.  

#### ゲームの流れ 
```bash
Red:どの番号の札を出しますか:
何回転させますか:
```
以上のような入力を繰り返してゲームを行います.  
番号札は1-9で振られています.  
一覧画像では左上から1,2,3となり,右下が9番目の手札となっています.  
それを参考に1-9の値を入力して手札を出してください.  
回転は時計回りに90度ずつ回転させられます.  
角度の対応は以下の通りです.  
| 入力値 | 回転度数 | 
| ------ | ------ | 
| 0 | 0 | 
| 1 | 90 | 
| 2 | 180 | 
| 3 | 270 | 
  
※手札選択では1-9以外の値を使用すると再移入力を求められます.  
　回転では4以上の値も利用できます.ループするだけなのでほぼ意味はないと思います.  

盤面は徐々に色が落ちていきます.  
出す手札と回転量を考えましょう.  
終了すると盤面の画像が表示,保存されます.  
![result](https://github.com/e-s-23/Prog2kakushin/assets/153585231/87aa71ce-9ae2-45b2-a079-1fce2e50ca07)  

#### リザルトについて
盤面の画像を基にRGB画像の平均を算出します.  
値が大きい方がより盤面を支配していることになり,勝利になります.  
```bash
Redの勝利！ Red score = 180  Blue score = 159
```
  
### 備考など  
#### 作成経緯や感想
某インク系ゲームのミニゲームを基に作ってみました.  
盤面を制限することと徐々に変化させること,重複を許すなどやりたい処理ができました.  
グラフィックをメインに扱うのはColabだとなかなか難しかったです.  
画像合成や加工の理論,データの扱いなどの知識が浅いのでもっと本格的に学ぶ必要があると思いました.  

#### お断り
ゲームのルール自体が微妙なのは許してください...
