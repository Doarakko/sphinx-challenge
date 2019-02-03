# JuliaTokyo #8
## 2018/10/20

## DataFrames and Types with Julia
### @ki_chi
### Juliaになんのパッケージを使えば抜け人を殲滅できるか
- DataFrames  
- DataFramesMeta  
- JuliaDB
    - Database ではないので注意
    - 現在v1.0でいれられない

- Queryverse
    - 入れるの大変  
    - 依存関係でこけるので個別で入れることになる

- 現状 DataFrame 使うのが安牌

### types 
- いろいろな dataframe が乱立  
- tabletrauts.jl + iterabletable.jl に合わせる
    - interface のみを提供

- Dataframes の構成と処理を別々にすることが可能

### QA
- データ可視化  
    - vegaLite / DataVoyager  

- Julia の速度  
    - コンパイルしてからやるので体感遅い. 一度コードが組めれば計算速速い  

- Julia のメモリ管理による優位性  
    - Python も R も C++でやっているので、その点の優位性はないのでは

### 感想
- Juliaを使うのは愛がないと厳しい  

## Julia : A Fresh Programming Language for Freshmen
### @hsugawa
- 大学の演習でJuliaを使っている  
    - 対象: 大学1年次（PC / 数学素人）

- 演習課題の提出を GitHub に  
    - Julia の日本語資料がないのはマイナス  

### 感想
- グループ演習にGitHubを使えば就職後に役立つのでは  
- 大学での講義の話を聞けたのは新鮮  


## JuliaでDeep Learning(できるかな？) 
### @SatoshiTerasaki
- flux
    - julia で書かれた機械学習ライブラリ  

- 学習済みモデルでのfinetunigもいける


## JuliaのFFI 
### @mrkn
- ruby でデータ分析をできるようなものを開発  
### Reference
- [apache arrow](https://arrow.apache.org/)  
- [Apache Arrow東京ミートアップ2018](https://speee.connpass.com/event/103514/)  

- 仕事で役立たせるのは難しい（できなくはない）
    - これから伸びる言語を最初に触っているのは大きなアドバンテージ  
- 他言語とやりとりするための機能は用意されている  

- Python などの他言語をいきなり Julia に書き換えるのではなく少しずつやる
    - PyCall.jl / RCall.jl で Python / R のプログラムを呼びだし 
    - 徐々に書き換えていく  

- apache arrow  
    - Python / R / etc それぞれでやっている  
        - ひとつに統合するために開発  
    - apatch の正式プロジェクト  

### research
- PyCall
- FFI 
- apache arrow  


## 覇権を取るパッケージ作成
### @bicycle1885
- direnv  
    - プロジェクトごとに環境変数を設定可能  

### 覇権をとるには
- アピールする  
    - GitHubにあげただけではだれもつかわない

- discourse でアナウンス  
- GitHub 映え  
- 手厚いサポート  
- 既存パッケージにプルリクをおくりつける  

### Research
- direnv  
- discourse  
    - julia のコミュニティ  
- revise.jl  
    - julia を再起動せず、パッケージのコードを更新可能  
    - パッケージ開発に便利  

## ライトニングトークセッション
### JuliaのDocumentationについて
- Julia の Documentation  
    - markdown  
    - html  
    - tex  

### Juliaと画像処理
#### @Dsuke_KATO
- juliaimage

## Reference
・[JuliaTokyo #8](https://juliatokyo.connpass.com/event/100780/)  