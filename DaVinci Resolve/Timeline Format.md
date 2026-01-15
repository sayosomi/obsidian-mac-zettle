---
Menu:
  - File > Project Settings
---
[[Master Settings]]内の一項目。
タイムラインの解像度とフレームレートを**必ず最初に**設定する。

## 推奨設定

![](https://i.gyazo.com/959243f4ad8116e7d2ed430e33c32173.png)

- Timeline resolution: タイムラインの解像度
- Use vertical resolution: ここにチェックを入れると縦長解像度になる
- Pixel aspect ratio: 1ピクセルの形状。絶対 `Square` で
- Timeline frame rate: フレームレート。Sonyの30pは `29.97`。**一度でも[[Clip]]を置くと後から変更不可**

----

## 特にいじらなくてよい設定

- [[Use drop frame timecode]]: 尺を厳密に決めたいときはオン
- Enable interlace processing: インターレース素材をフィールド単位で正しく処理するための設定らしい。よくわからんが YouTube では不要らしい
- Align Clips to Frame Boundaries: インターレース処理時に、編集（カット/移動）や再生ヘッドの進み肩を決めるらしい。よくわからんが同上
- Playback frame rate: [[Video Monitoring]]での再生フレームレート

## 関連

[[Timeline Format とVideo Monitoring の違い (Master settings)]]
