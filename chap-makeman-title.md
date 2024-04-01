# 音楽の要求定義とシステム化
世の中単純な音楽がありふれている。本物はカートコバーンだけ。もちろん寒川のね笑

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

//source{

import librosa
import soundfile as sf
import pydub
from pydub import AudioSegment

path = "motoneta.mp3"
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

//}

スピードアップにはpydubを使用し、ピッチを上げるのにはlibrosaを使用している。



## 音楽の要求定義とシステム化（ヴェイパーウェイヴ編）
f/1揺らぎ　カオス/フラクタル　フォルマント周波数
### 音楽の要求定義（ヴェイパーウェイヴ編）

### 音楽のシステム化（ヴェイパーウェイヴ編）


## 自動生成した音楽の配信工場
かけたらかく

## 真の音楽とは

![真の音楽](images/chap-makeman-title/true_music.png?scale=5)