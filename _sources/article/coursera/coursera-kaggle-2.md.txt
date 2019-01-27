# 仕事をしながら Coursera の Kaggle コースを受けてみる ②
## はじめに
この記事は、[kaggle Advent Calendar 2018](https://qiita.com/advent-calendar/2018/kaggle) 2日目の記事です。

この記事を読んでもスコアは上がりません。  
空いていたので無理やりねじ込みました。

Coursera の [Kaggle コース](https://www.coursera.org/learn/competitive-data-science) Week 2 の感想記事になります。  
コース1週目の記事は[こちら](https://doarakko.hatenablog.com/entry/coursera_kaggke_week1)からどうぞ。
  
コースを受講しようか考えている方の参考になれば幸いです。  

## Week 2
２週目は以下の内容になります。

- EDA
- Validation
- Data Leak
  
Validation に結構期待していたのですが、だいたい知っているようなことでした。

実際のコンペでの EDA を説明してる動画が一番勉強になりました。 

### Quiz 
Data Leak の Quiz が鬼門（奇問？）です。  
計算問題がありますがビデオを見返せば問題ありません。

変な問題が1つ混じっているので、気をつくてください。

### Programming Assignment
<b>テストデータのみを使ってスコアを 90% 以上取る</b>ことが合格基準です。

やり方自体は書いてあるので、Scipy を使ってその通りに実装します。  
[Sparse matrices](https://docs.scipy.org/doc/scipy/reference/sparse.html) の使い方になれている人であれば、そこまで難しくないのかもれしません。

個人的にはコース全て含めてこの課題が一番きつかったです。  
Data Leak さっぱりわからん。

### Peer-graded Assignment
見つけたリークについて説明する文章（もちろん英語）を 3 ~ 5 文で書いて提出して、他の受講者にレビューしてもらいます。  

合計 3 人、それぞれ 0 ~ 4 pt で採点されます。  
クリア基準は、<b>3人合計で 3 pt</b>なので簡単です。

レビューしてくれる（する）人はシステム上で自動で割り振られます。

この課題はレビューする人がいなくなるとクリアできないので、期限内にやっておいた方がいいです。

レビューする数には制限がない（＝何個でもレビューできる）ので、最悪フォーラムで助けを求めればなんとかなるかもしれません。

## 感想
1週目に比べて英語がきつくなってきたので、会社の昼休みに予習して、家に帰って再度聞くというやり方で進めました。

 
リークは自分で見つけられる気がしないので、コンペにでた時は Kernel と Duscussion を漁ることにします。


Kaggle meet up 行きたかった...

## 参考資料
- [コース1週目の記事](https://doarakko.hatenablog.com/entry/coursera_kaggke_week1)
- [How to Win a Data Science Competition: Learn from Top Kagglers](https://www.coursera.org/learn/competitive-data-science)
- [コース課題（公式）](https://github.com/hse-aml/competitive-data-science)
- [Sparse matrices (scipy.sparse)](https://docs.scipy.org/doc/scipy/reference/sparse.html)
