# 歌とプログラム

## Lyrics
>Midnight takes your heart and your soul
>While your heart is as high as your soul
>Put your heart without your soul into your heart
>
>Give back your heart
>
>
>Desire is a lovestruck ladykiller
>My world is nothing 
>Fire is ice
>Hate is water
>Until my world is Desire,
>Build my world up
>If Midnight taking my world, Fire is nothing and Midnight taking my world, Hate is nothing
>Shout "FizzBuzz!"
>Take it to the top
>
>If Midnight taking my world, Fire is nothing
>Shout "Fizz!"
>Take it to the top
>
>If Midnight taking my world, Hate is nothing
>Say "Buzz!"
>Take it to the top
>
>Whisper my world

引用 : https://codewithrockstar.com/

## ロックスターの言語
勘の良い人間にはわかるだろうが上記は歌のように見えるれっきとしたFizzBuzzのプログラムである。

突然だが最強の言語と聞いて浮かぶ物は何か？RustやPython？いや歌こそが力、それがこのRockstar言語だ。
我々は歌を聴き、無意識に脳でコンパイルして動かされているに過ぎない。誰もロックスターには敵わないのだ。

実際にNevermind part 0は全てこの言語で書かれていた為、聴く者を虜にしてしまったのは有名な話であり、その後事態を重く見た当時の政府が発禁としてしまった。
赤ん坊(=未熟な政治)が水中(=それは苦しい)でドル札(=金)に踊らさせられてるとNevermind(part 1)のジャケットでこの出来事を暗に皮肉っているのは周知の事実かと思う。

## Rockstar言語について
言語仕様はここを見てくれ。
引用 : https://github.com/dylanbeattie/rockstar/blob/master/spec.md


## コーディング
そんなものはしない、何故なら本物のロックスターだから。
それに俺が本気でコーディングしたらまた消されてしまうだろう…Nevermind minus oneのようにな。

```md
~~仕様がめんどくさ過ぎる。~~
```

## なんとかならんか
それでも紡ぎたい、歌詞を。本物の歌を。

なんとpythonのトランスパイラーを見つけた。お前の負けだアメリカのカートコバーン。


https://github.com/yyyyyyyan/rockstar-py


## pythonをトランスパイルしてお茶を濁したい
ここに3の倍数を受け取ったときにKart Cobainと出力する簡単なプログラム、samukawa.pyを用意した。これをRockstar言語へトランスパイルすることで何とかしたい。

以下でインストールをする。

```
pip install rockstar-py
```

そして用意したpythonを引数に渡して動かすと、、、

```
rockstar-py --stdin -o samukawa.py
``` 


![真のコバーン](images/chap-cobain-rockstar/kart.jpg?scale=0.5)

動かない。（コマンド実行でフリーズ）

ファイル数からもわかる通り何度か試したが動かない。
ばーかばーか

最後の更新から4年も経ってるし無理もないのかもしれない。そもそもRockestar言語自体3年前で更新が止まっている。(なんとアメリカのカートコバーンの没年と重なる！！！)

1週間前に体調壊さなければ動くところまでやりたかったがワクの後遺症で頭が痛い。pythonはあまりデバッグの知見も無いのでここまでとする。

誰か動かせたら教えてほしい、修正してcommitしてもいいよ。

## 最後に
歌がプログラムってアルトネリコ思い出すよね、ミシャの胸成長させたのまだ赦してないからな。

