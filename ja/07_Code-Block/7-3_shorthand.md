

## 省略表記

コード ブロックにはデータ管理を*大幅に*容易にする基本的な省略表記方法がいくつかあります。 ここでは基本の概要を示し、この省略表記をデータの作成とクエリーの両方に使用する方法を説明します。

|データ タイプ|標準 Dynamo|コード ブロックの同等表記|
| -- | -- | -- |
|数値|![](images/7-3/table/number.png)|![](images/7-3/table/numberCB.png)|
|文字列|![](images/7-3/table/string.png)|![](images/7-3/table/stringCB.png)|
|シーケンス|![](images/7-3/table/sequence.png)|![](images/7-3/table/sequenceCB.png)|
|範囲|![](images/7-3/table/range.png)|![](images/7-3/table/rangeCB.png)|
|インデックスでの項目の取得|![](images/7-3/table/getItem.png)|![](images/7-3/table/getItemCB.png)|
|リストの作成|![](images/7-3/table/list.png)|![](images/7-3/table/listCB.png)|
|文字列の連結|![](images/7-3/table/concat.png)|![](images/7-3/table/concatCB.png)|
|条件ステートメント|![](images/7-3/table/if.png)|![](images/7-3/table/ifCB.png)|

### その他の構文

|ノード|コード ブロックの同等表記|注意|
| -- | -- | -- |
|すべての演算子(+、&&、>=、Not など)|+、&&、>=、! など|「Not」は「!」になりますが、「Factorial」(階乗)と区別するためノードは「Not」と呼ばれます|
|ブールの True|true;|小文字を使用します|
|ブールの False|false;|小文字を使用します|

### 範囲

基本的な省略表記を組み合わせることで、範囲とシーケンスを設定することができます。下記の画像を「..」構文のガイドとして参照し、コード ブロックを使用して数値データのリストを設定してみましょう。この表記に慣れると、数値データを効率的に作成できるようになります。![廃止された範囲](images/7-3/obsolete02.png)

> 1. この例では、数値範囲を ```beginning..end..step-size;``` の基本的なコード ブロック構文で置き換えて設定します。 数値で表すと、```0.. 10.. 1;``` になります。
2. 構文 ```0..10..1;``` は ```0..10;``` と同じ意味になります。 step-size の 1 は省略表記の既定値です。つまり、```0..10;``` は間隔の大きさが 1 であるシーケンス 0 から 10 を表しています。
3. *数値のシーケンス*の例も同様です。ただし、「*#*」を使用して、15 までの値を含むリストではなく、15 個の値を含むリストを指定しています。 この場合、```beginning..#ofSteps..step-size:``` を設定しています。 シーケンスの実際の構文は ```0..#15..2``` になります。
4. 今度は前の手順の「*#*」を構文の *step-size* 部分に配置してみましょう。 これで、*数値範囲*は *beginning* から *end* に設定され、これらの 2 つの間の値が *step-size* 表記に指定された値で均等に分割されます: ```beginning..end..#ofSteps```。

### 高度な範囲

高度な範囲を作成すると、リストのリストを簡単な方法で使用できます。次の例では、メイン範囲の表記から変数を分離して、このリストに別の範囲を作成します。![範囲](images/7-3/03.png)

> 1. ネストされた範囲を作成して、「*#*」が指定されている表記と指定されていない表記とを比較してみましょう。 ロジックは基本的な範囲と同じですが、多少複雑になります。
2. サブ範囲はメイン範囲内の任意の場所に設定できます。また、2 つのサブ範囲を設定することもできます。
3. 範囲内の「*end*」値をコントロールすることにより、長さが異なる範囲を追加で作成できます。

![範囲](images/7-3/02.png)

> ロジックの演習として上記の 2 つの省略表記を比較し、*サブ範囲*と「*#*」表記が出力をどのようにコントロールしているかを読み解いてください。

### リストを作成してリストから項目を取得する

リストは省略表記を使用して作成できる他、すばやく作成することも可能です。これらのリストには幅広い要素タイプを含めることができ、クエリーを実行することも可能です(リストはリスト自体がオブジェクトです)。簡単に言うと、コード ブロックでブレース(中括弧)を使用してリストを作成し、ブラケット(角括弧)を使用してリスト内の項目のクエリーを実行します。

![リストのクエリーを実行する](images/7-3/cbn07.png)

> 1. 文字列を使用してリストをすばやく作成し、項目のインデックスを使用してクエリーを実行します。
2. 変数を使用してリストを作成し、範囲の省略表記を使用してクエリーを実行します。

ネストされたリストを管理するプロセスは同様です。リストの順番に配慮し、複数の角括弧のセットを使用します。

![リストのクエリーを実行する](images/7-3/cbn08.png)

> 1. リストのリストを設定します。
2. 1 つの角括弧の表記を使用してクエリーを実行します。
3. 2 つの角括弧の表記を使用して項目のクエリーを実行します。

### 演習

> この演習に付属しているサンプル ファイルをダウンロードしてください(右クリックして[名前を付けてリンク先を保存]を選択)。すべてのサンプル ファイルの一覧については、付録を参照してください。[Obsolete-Nodes_Sine-Surface.dyn](datasets/7-3/Obsolete-Nodes_Sine-Surface.dyn)

この演習では、新しい省略表記のスキルを使用して範囲と式を設定し、一風変わった卵型のサーフェスを作成します。この演習では、コード ブロックと既存の Dynamo ノードを並行して使用する方法を学習します。Dynamo ノードを視覚的に配置して設定を確認しながら、コード ブロックを使用して大きなデータを処理します。

![演習](images/7-3/Exercise/13.png)

> まず上記のノードを接続してサーフェスを作成します。数値ノードを使用して幅と長さを設定する代わりに、キャンバスをダブルクリックして、コード ブロックに ```100;``` と入力します。

![演習](images/7-3/Exercise/12.png)

> 1. Code Block に ```0..1..#50``` と入力して、0 から 1 の範囲を 50 個に分割するように設定します。
2. 範囲を *Surface.PointAtParameter* ノードに接続します。これは 0 から 1 の範囲内にある *u* と *v* の値を取得してサーフェス全体に設定します。 *Surface.PointAtParameter* ノードを右クリックし、*レーシング*を*外積*に変更します。

![演習](images/7-3/Exercise/11.png)

> この手順では、最初の関数を適用して、グリッドを Z の正の向きに移動します。このグリッドは基盤となる関数に基づいて生成されるサーフェスをコントロールします。

> 1. 上記の画像に示すように、ビジュアル ノードをキャンバスに追加します。
2. 式ノードを使用する代わりに、Code Block を使用して ```(0..Math.Sin(x*360)..#50)*5;``` を指定します。 この式を簡単に分割して説明するために、式内に範囲を設定します。この式は正弦関数です。正弦関数は Dynamo で角度(度)入力を受け取ります。このため、完全な正弦波を取得するには、*x* 値(0 から 1 までの入力範囲)を *360* で乗算します。 次に、各行のコントロールグリッドの点と同じ数だけ分割するため、*#50* を指定して 50 個のサブディビジョンを設定します。 最後に、Dynamo プレビューで効果を確認できるようにするため、累乗の指数に 5 を指定して変換の振幅を大きくします。

![演習](images/7-3/Exercise/06.png)

> 1. 以前のコード ブロックは正常に動作しましたが、完全にパラメトリックではありませんでした。パラメータを動的にコントロールするため、前の手順で使用した行を ```(0..Math.Sin(x*360*cycles)..#List.Count(x))*amp;``` で置き換えます。 こうすることで、これらの値を入力に基づいて設定できるようになります。

![演習](images/7-3/Exercise/10.png)

> 1. スライダ(範囲 0 から 10)を変更して、どのような結果が生じるか確認します。

![演習](images/7-3/Exercise/09.png)

> 1. 数値範囲を転置することにより、カーテン ウェーブの方向を反転します: ```transposeList = List.Transpose(sineList);```。

![演習](images/7-3/Exercise/07.png)

> 1. sineList と tranposeList を追加すると、歪曲した卵型のサーフェスが生成されます: ```eggShellList = sineList+transposeList;```。

![演習](images/7-3/Exercise/05.png)

> 1. もう一度スライダを変更して、このアルゴリズムの生成結果をなだらかになるように調整しましょう。

![演習](images/7-3/Exercise/04.png)

> 1. 最後に、コード ブロックを使用して、データの一部のクエリーを実行しましょう。特定の範囲の点を指定してサーフェスを再生成するには、*Geometry.Translate* ノードと *NurbsSurface.ByPoints* ノードの間に上記の Code Block ノードを追加します。 ```sineStrips.. 15 [0.. 1] ;``` が指定されています。 これにより、50 行の最初の 16 行の点が選択されます。サーフェスを再作成すると、点のグリッドの一部が分離されて生成されていることがわかります。

![演習](images/7-3/Exercise/03.png)

> 1. 最後の手順では、このコード ブロックをよりパラメトリックなものにするため、範囲 0 から 1 のスライダを使用してクエリーをコントロールします。これを行うには、コード行 ```sineStrips[0..((List.Count(sineStrips)-1)*u)];``` を使用します。 わかりにくいかもしれませんが、このコード行により、リストの長さを乗数 0 から 1 の値を使用してすばやくスケールできます。

![演習](images/7-3/Exercise/02.png)

> 1. スライダに *.53* の値を設定すると、グリッドの中央をわずかに超えるサーフェスが作成されます。

![演習](images/7-3/Exercise/01.png)

> 1. おわかりのように、スライダを *1* に設定すると、すべての点のグリッドを使用してサーフェスが作成されます。

![演習](images/7-3/Exercise/00.png)

> 生成されたビジュアル グラフを参照する際、コード ブロックをハイライト表示して Code Block ノードの各関数を確認できます。

> 1. 最初の Code Block ノードは *Number* ノードを置き換えます。
2. 2 番目の Code Block ノードは *Number Range* ノードを置き換えます。
3. 3 番目の Code Block ノードは *Formula* ノード(および *List.Transpose*、*List.Count*、*Number Range* の各ノード)を置き換えます。
4. 4 番目の Code Block ノードはリストのリストのクエリーを実行し、*List.GetItemAtIndex* ノードを置き換えます。
