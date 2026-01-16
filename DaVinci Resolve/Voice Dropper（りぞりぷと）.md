---
tags:
  - 自分用レシピ
---

## トラック名の決め方

- 立ち絵のトラック：  `ZU`
- text+のトラック：`ZU_t`
- 音声トラック：`ZU_a`

## ワークフロー

- （Voicegerのwavなら）右クリック > クイックアクション > Voicegerのwavからtxtを作る
- Voice Dropper の Import ボタンで音声ファイルと字幕を入れる
- 配置を調整
- `option + F9`, `option + command + F9` ですべての [[Auto Track Selector]] をオフにする → 口パク処理するキャラのトラックのみオンにする
- Voice Dropper の口パクボタンで立ち絵分割して口パク処理
- [[Timeline Playback Resolution]] をオフにする
- 口パク処理した立ち絵トラックを選択し、右クリック > Render in Place
    - コーデックはアルファが使えるものを選ぶ（作者は Grass Vally を使っている）
- [[Auto Track Selector]] を元に戻す 
- [[Timeline Playback Resolution]] を元に戻す
