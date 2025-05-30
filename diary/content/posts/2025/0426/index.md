---
title: "土曜日のハイキング"
date: "2025-04-26T19:55:42+09:00"
dates: [2025/04]
cover: ""
tags: [hiking, exercise, hugo]
showFullContent: true
---

昨晩の睡眠時間は6時間41分 (23:56〜7:25, 深い睡眠0:48) だった。登山へ出掛けるからいつもより1時間早くベッドに入って努めた分、いつもより睡眠時間が増えた。先週ぐらいから睡眠時間が6時間を超える日が多くなってきた。生活を改善している効果が睡眠時間に表れつつある。

## 世継山と摩耶山のハイキング

先週の土曜日 (19日) は世継山と再度公園へ、今日は摩耶山・掬星台へと、2週続けてハイキングへ行ってきた。毎日歩いていて体力がついてきたこともあり、少し険しい山道だったものの、体力不足の疲労感をあまり感じなかった。一方で昔からよくない右股関節の違和感は心肺能力とは別に疲労が蓄積して残り続けるのであまり右足を踏ん張らないようにしながら上り下りしてきた。歩いていて辛いほどの違和感ではないから、ハイキングに支障はない。

* [新神戸駅から布引ハーブ園、再度公園、大師堂コース](https://yamap.com/activities/39237231)
* [新神戸駅から稲妻坂・天狗道を経て摩耶山・掬星台](https://yamap.com/activities/39405242)

夕方に戻ってきて少し寝て [登山と身体の科学 運動生理学から見た合理的な登山術](https://www.kodansha.co.jp/book/products/0000392957) を読みながらふりかえりをした。yamap の「標準」コースタイムと比べて歩くペースが150%前後と速過ぎたことを理解した。どのぐらいのペースで歩くのがよいのか、まったくわかっていなかった。疲労度を軽減して安全に上るには「ゆっくり上る」のが大事で「標準」コースタイムの100%を基準にすればよいらしい。もちろんメンバーの体力と相談しながらでよいように思えるが、100-120%におさまるように歩くとよさそうにみえる。次からペース配分しながら歩いてみる。

これまで yamap の活動日記を「友だち」限定公開にしていた。山登り仲間を増やしていく上で yamap の情報をみせた方がわかりやすい。軽く調べてみて限定公開にする意図はプライバシーの配慮だけにみえる。基本的には行程を記録して風景の写真しか取っていない。yamap メンバーであれば、一緒に行ったメンバーはわかってしまう。ながいさんと一緒に行ったハイキングや三宮.devの登山部はとくにそういったプライバシーを考慮しなくても大丈夫そうに思えるので一般公開することにした (ながいさん、懸念があったら限定公開にするので教えてください) 。今後もプライベートでハイキングに行く機会はあると思えるが、一緒に歩く人に活動日記の公開の許可を得て、懸念表明があればメンバーを外すか、友だち限定にしておく。

yamap アプリの使い方を調べていて登山の軌跡を動画で見返すことができる。この動画を共有しようと思ったら yamap アプリがスマホ上で再生しているのを、スマホのスクリーンリーダーで記録するといったやり方で動画保存できる。道中で写真を取っておくと、この軌跡を見返すときに登山コースの雰囲気を伺えておもしろい。よく出来ていると思うし、歩きながら山道を写真に残していこうというインセンティブにもなる。

* video タグで指定した width/height サイズ: 360x640
* 左: オリジナル (サイズ 25MiB)
* 右: 品質を落として圧縮 (サイズ 6.2MiB)

{{< video file="yamap-sr-20250426-orig.mp4" width=360 height=640 >}}

{{< video file="yamap-sr-20250426-compact1.mp4" width=360 height=640 >}}

スクリーンリーダーの動画をそのまま保存するとサイズは 25MiB になる。ちょっとサイズが大き過ぎる。chatgpt にオリジナルの動画のメタデータを渡してよしなに圧縮してもらう。

```
Stream #0:0(und): Video: h264 (High) (avc1 / 0x31637661), yuv420p(tv, smpte170m/smpte170m/bt709), 720x1280, 3433 kb/s, 30 fps, 30 tbr, 600 tbn, 1200 tbc (default)
```

次のようなパラメーターで圧縮すればよいとのこと。私は動画について明るくないからパラメーターが適切かどうかは判断できない。しかし、こういう用途なら品質を目視で確認できるし、再生できれば目的を果たせるから細かいパラメーターの調整が適切でなくてもあまり困らない。

> 以下のように、解像度を横480pxに縮小しつつCRFエンコードで画質をコントロールする例を示します。元が720×1280の縦長動画なので、-vf scale=480:-2 でアスペクト比を保ったまま高さを自動調整します。
> 
> * -vf scale=480:-2  幅を480pxに固定、高さを偶数で自動計算
> * -c:v libx264  H.264で再エンコード
> * -preset medium  エンコード速度と圧縮率のバランス（slow～veryfastなど変更可）
> * -crf 28  品質係数。数値が大きいほど高圧縮(小ファイル)/低画質。18～28あたりが一般的
> * -c:a aac -b:a 128k  音声をAAC・128kbpsで再エンコード

```
$ ffmpeg -i yamap-sr-20250426-orig.mp4 -vf scale=480:-2 -c:v libx264 -preset medium -crf 28 -c:a aac -b:a 128k yamap-sr-20250426-compact1.mp4
```

サイズは1/4程度まで小さくなった。オリジナルと比べると明らかに劣化していることはわかるが、日記に掲載するのであれば十分な品質にみえる。

```bash
$ du -hs yamap-sr-20250426-*
6.2M  yamap-sr-20250426-compact1.mp4
25M	  yamap-sr-20250426-orig.mp4
```

圧縮後のメタデータは次のようになった。

```
Stream #0:0(und): Video: h264 (High) (avc1 / 0x31637661), yuv420p(tv, smpte170m/smpte170m/bt709), 480x854, 867 kb/s, 30 fps, 30 tbr, 15360 tbn, 60 tbc (default)
```

## video タグを扱う hugo の shortcode

デフォルトで hugo は video タグを扱う shortcode がないらしい。登山の軌跡の動画をアップロードするために作ってみた。この日記におけるコンテンツ管理の歴史的経緯で静的ファイルの管理方法が異なるため、static から参照する `src` 属性とコンテンツと同じ場所から参照する `file` 属性を使い分けている。

```xml
{{ $src := (default (printf "%s%s" .Page.RelPermalink (.Get "file")) (.Get "src")) | absURL }}
{{ $width := or (.Get "width") "640" }}
{{ $height := or (.Get "height") "360" }}
<video width="{{ $width }}" height="{{ $height }}" controls>
  <source src="{{ $src | relURL }}" type="video/mp4">
  お使いのブラウザは video タグに対応していません。
</video>
```

コンテンツからは次のように video タグを扱う shortcode を呼び出す。

```xml
{{</* video file="yamap-sr-20250426-orig.mp4" width=360 height=640 */>}}
```
