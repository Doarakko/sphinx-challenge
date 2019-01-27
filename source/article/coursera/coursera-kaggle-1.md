# 仕事をしながら Coursera の Kaggle コースを受けてみる ①
## はじめに
最近 Kaggle が Leak ばかりできつかったので、少しコンペから離れることにしました。全く別のことをしようと思ったのですが、せっかくなので前から気になっていた Coursera の [Kaggle コース](https://www.coursera.org/learn/competitive-data-science)を受けてみます。

- 実務経験：なし  
- 英語：読むのならなんとか  
- 機械学習：[Pythonではじめる機械学習](https://www.oreilly.co.jp/books/9784873117980/)  を読んだ程度の知識  
- Kaggle：いくつか参加したがメダルなし

残業がないのが弊社の唯一のいいところで、家に帰ってからだいたい 3 時間ほど学習の時間が取れます。

こんな感じの状態でスタートします。  
受講しようか迷っている方の参考になれば幸いです。  

## コース概要  
[こちら](https://www.coursera.org/learn/competitive-data-science)にシラバスがあります。

各週ごとに課題（Quiz / Programming Assignment）に期限が設けられていますが、コース終了日までに全て完了すれば問題ないです。  

ただ、他受講者にレビューしてもらう（レビューする）課題があるので、そちらは期限内にやらないとレビューしてくれる人がいなくなる可能性が高くなるので、気をつけてください。  
Discussion Forums（Kaggle の Discussion のようなもの）が用意されているので、最悪そこで助けを求めればなんとかなるかもしれません。  

Coursera にはスマホアプリがあります。教材をダウンロードしておけば、オフラインでも気にせず Video が見れて超便利。  

以下は 1 週目の概要と感想です。

## Week 1
１週目は導入で、以下のコンテンツがありました。

### Video
- 言語：英語  
- 字幕：英語  
- 速度：[0.75, 1.00, 1.25, 1.50, 1.75, 2.00]  

Kaggle GrandMaster が実際に話してます。  
今回は [Alexander Guschin](https://www.kaggle.com/aguschin)  と [Mikhail Trofimov](https://www.kaggle.com/mikhailtrofimov) が教えてくれました。  
速くて聞き取れない場合は 0.75倍速にするといいです。僕は字幕を読みます。  

字幕は英語しかありませんが、ページの下にテキスト化されているので、Google 翻訳に投げるのは簡単です。   

Video の途中で Quiz（ちょっとした確認のようなもの）が出されることがあります。スキップできて間違えても問題ないです。

### Reading  
- 言語：英語  

内容は、直前に見た Video のまとめ的なもの / 参考資料 / Quiz の解説などがあります。ページ右下の Complete ボタンを押せば完了になるので、読まなくても特に問題はないですが、文章はそこまで多くありません。

### Notebook
Video の補助的なものです。直前の Video で話した内容を掘り下げてます。  

今回は、GBDTモデルで最初のツリーを取り除いた時にスコアが変化するか検証しています。
[こちら](https://github.com/hse-aml/competitive-data-science/blob/master/Reading%20materials/GBM_drop_tree.ipynb)（公式）に公開されています。

### Practice Quiz / Quiz  
- 合格基準：80 ~ 100%  
- 問題数：6 ~ 10  
- 形式：選択問題  
- 制限時間：なし  
- 期限：なし / あり  
- 回答制限：なし / <b>1日3回まで</b>

問題数 / 選択肢の数が小さいので全探索でいけます。  
Quiz によって合格基準と問題数が異なります。

### Programming Assignment
- 合格基準：100%  
- 形式：Jupyter notebook  
- 言語：英語  
- 制限時間：なし  
- 期限：あり  
- 回答制限：<b>なし</b>

名前の通りプログラムを提出します。  
ページ内のリンクを開くと Jupyter notebook が起動して、そこで自由にプログラムを実行できます。問題は穴埋めになっていて、解答を指定された変数にいれて、Submit 用の関数を実行すると採点されます。  

1週目で行なったのは <b>Pandas</b> の基本的な使い方の問題でした。<b>grouby</b> や <b>join</b> がわかっていればさほど難しくありません。問題は GitHub に公開（公式）されています、興味のある方は[こちら](https://github.com/hse-aml/competitive-data-science)からどうぞ。
  
僕は問題を正しく理解できなくて、こういう意味かなと思ったものを片っ端から Submit しました。一発合格した人は 17% ほどだそうです。Form で助けを求めている方もいました。

## 感想
スタート前は英語が一番不安でしたが、多少知っている分野の英語だと聞き取りやすいです。コースの難易度がわからないという方は、[こちら](https://github.com/hse-aml/competitive-data-science) にプログラミング課題が公開されているので参考にしてください。  

Week 1 でどれくらいの時間を使ったか忘れましたが、想定されている時間 * 1.5 くらいだと思います。これから難しくなってくると思うので、想定されている時間 * 2.0 くらいかかる予定で行きます。  

コース終了後も教材が見れるのか気になります。  
知っている方いたら教えてください。

あと、スマホアプリだと各課題の期限が Web の 1 週間後の日にちで表示されています。
おそらく Coursera の 1 週間無料期間で今回のコースをスタートしたことが影響しているのだと思います。

それでは Week 2 に行ってきます。

## 参考資料
- [How to Win a Data Science Competition: Learn from Top Kagglers](https://www.coursera.org/learn/competitive-data-science)
- [コース課題（公式）](https://github.com/hse-aml/competitive-data-science)
- [Pythonではじめる機械学習](https://www.oreilly.co.jp/books/9784873117980/) 