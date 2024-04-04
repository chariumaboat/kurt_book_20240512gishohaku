# 音楽の要求定義とシステム化
世の中単純な音楽がありふれている。本物の音楽はカートコバーンだけ。もちろん寒川のね笑

## 音楽の要求定義とシステム化（ナイトコア編）

### 音楽の要求定義（ナイトコア編）
**ナイトコア**というジャンルを知っているだろうか。早速だがwikipediaを引用する。

//quote{
ナイトコア（英: Nightcore）とは、波形編集ソフトウェアを用いて、原曲のテンポを高速化させ、場合によっては意図的にピッチも上げて作られた、リミックスを指す音楽ジャンルである。
//}

なるほど、要するに要素は以下だ。

- 原曲のテンポを高速化
- 場合によっては意図的にピッチも上げる

つまり、登場人物は**原曲**がまずあり、その**テンポ**と**ピッチ**を編集すると言うことだ。これをやっていく。


### 音楽のシステム化（ナイトコア編）
早速やっていく、言語は**Python**を使用する。見た方が早いので早速コードを載せる。

```

import librosa
import soundfile as sf
import pydub
from pydub import AudioSegment

path = "motoneta.mp3" #元ネタの音源を指定する。引数でファイルパス受け取るでもいい
path_pitchup = "pitchup.wav"
path_nightcore = "nightcore.mp3"

#ピッチあげる
y, sr   = librosa.load(path , mono=True)
y_slow  = librosa.effects.time_stretch(y, 0.5)
sf.write(path_pitchup, y_slow, 44100, format='wav', subtype='PCM_24')

#早くする
base_sound = AudioSegment.from_file(path_pitchup, format="wav")
base_sound = base_sound.speedup(playback_speed=2, crossfade=0)
base_sound.export(path_nightcore, format="mp3")

```

スピードアップにはpydubを使用し、ピッチを上げるのにはlibrosaを使用している。
この程度で再現できるものがカートコバーンと肩を並べて**音楽**を語る、なんと愚かなことか。
好きにpydubとlibrosaの設定値を変えるといい。その度カートコバーンとの差を感じるだけだ。


## 実際に曲にした
Friday Night Fantasyという曲を上記のプログラムに食わせて見た。結果は以下だ。
![ナイトコア](images/chap-makeman-title/night_core_qr.png)
ゴミだ。

## 音楽の要求定義とシステム化（ヴェイパーウェイヴ編）

### 音楽の要求定義（ヴェイパーウェイヴ編）
ナイトコアと同じく**ヴェイパーウェイヴ**の正体を暴く。同じくwikipediaを引用する。

//quote{
音楽的には、1980年代から1990年代にかけての大衆音楽、ラウンジ・ミュージック、スムースジャズ、コンテンポラリー・R&Bなどのサンプリングを基本とし、そこからループ、ピッチダウン、チョップド&スクリュードなどエフェクトを重ねていくことによって制作される
//}

つまり、登場人物ナイトコアと同じくサンプリングされる**原曲**がまずあり、それを**ループ**させ**ピッチ**を編集すると言うことのようだ。

チョップド&スクリュードについてはわからないからまたwikipediaを引用する。
//quote{
ターンテーブルを使って回転数を落とす「スクリュード」と、二枚使いで半拍ずらして反復する「チョップド」の二つの要素を軸にしたDJの技法だ
//}

なるほど。実装がめんどくさいので一旦置いておく。申し送り事項にする。

### 音楽のシステム化（ヴェイパーウェイヴ編）

#### ループ
まずはループさせる。こんなのは適当に一曲を繰り返せばいい。Pythonでやる。

```
path = "motoneta.mp3" #元ネタの音源を指定する。引数でファイルパス受け取るでもいい

import numpy as np
import librosa
import pydub
from pydub import AudioSegment

y, sr = librosa.load(path)
tempo, beat_frames = librosa.beat.beat_track(y=y, sr=sr)

#曲の長さ（ミリ秒
time = int(librosa.get_duration(y=y, sr=sr) * 1000)
#BPMから1ビートの長さをとる（ミリ秒
beat_time = int( 60 / tempo * 1000)

base_sound = AudioSegment.from_file(path, format="mp3")
oneminit_sound = base_sound[0:0]
start_time = 0

#1分にする
while(True):

    import random
    # 乱数で適当に切り出す箇所の終了位置決める(ここの乱数がいじりどころ
    end_time = start_time + (random.randint(1, 4) * beat_time)

    # 切り出してくっつける
    cut = base_sound[start_time : end_time]
    oneminit_sound = oneminit_sound + cut

    # 1分すぎたら終わり
    if 60000 < len(oneminit_sound):
        break

    # 乱数で適当に切り出す箇所の開始位置決める(ここの乱数がいじりどころ
    start_time = end_time + (random.randint(10, 16) * beat_time)

    # 曲一周したら頭に戻る
    if time < start_time:
        start_time = start_time - int(time)

oneminit_sound[:60000].export("oneminit.mp3", format="mp3")

```

上記で1分間のループになる。

#### ピッチダウン
これはコマンドでやった。ffmpegというアプリを使用している。
`
ffmpeg -i motoneta.mp3 -vf setpts=PTS/0.5 -af aresample=48000,asetrate=48000*0.8 -ar 48000 vaporwave.mp3
`

Pythonでffmpegを使うラッパーもあるらしいがうまく動かなかった。誰か試して見て欲しい。

## 実際に曲にした
同じくFriday Night Fantasyという曲を上記のプログラムに食わせて見た。結果は以下だ。

 ループ
![ループ](images/chap-makeman-title/oneminit_qr.png)

 ピッチダウン
![ピッチダウン](images/chap-makeman-title/vapor_wave_qr.png)

ゴミだ。こんなものがカートコバーン（もちろん寒川のだよ）と肩を並べて語られている事に違和感を感じないのであれば、全員ここに耳を置いて行った方がいい。無駄だ。


## 自動生成した音楽の配信工場
かけたらかく

## 真の音楽とは

![真の音楽](images/chap-makeman-title/true_music.png?scale=5)

## 戯言

こう言ったリミックスの求心力をシステムに落とすにあたり**フラクタルと1/fゆらぎ**や**フォルマント周波数**とかその辺のキーワードが引っかかる気がするけどちょっとそこまで調べる元気がない。
