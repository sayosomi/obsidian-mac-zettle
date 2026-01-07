- [[Source Viewer]]からタイムラインに[[Source Clip (Media Pool)|Source Clip]]をドラッグアンドドロップして追加する

[![](https://i.gyazo.com/995780ecbd56cd85e46b3f10813092b8.png)](https://gyazo.com/995780ecbd56cd85e46b3f10813092b8)
- [[Source Viewer]]からタイムラインビューアに素材をドラッグ・アンド・ドロップして追加する
- この方法だと挿入方法を選ぶオーバーレイが出る。[[Playhead]]の位置を基準に挿入される

## 挿入方法の種別

### 上書き Overwrite

[[Playhead]]より後ろが新しいクリップで上書きされる
- [[Playhead]]は追加したクリップの末尾に移動する
- キーボードショートカット`F10`でも同じ動作

### 挿入 Insert

[[Playhead]]の位置に新しいクリップが挿入され、後ろのクリップがずれる。
- [[Playhead]]は挿入したクリップの末尾に移動する
- キーボードショートカット`F9`でも同じ動作

### 末尾に追加 Append At End

[[Playhead]]の位置に関わらず、新しいクリップは末尾に追加される。
- [[Playhead]]は末尾に移動する

### 最上位トラックに配置（Place on Top）

- タイムライン上に[[In Point]]と[[Out Point]]を配置してから使う
- 新しいクリップは、タイムライン上の[[In Point]]と[[Out Point]]の間に収まるように配置される。
- 新しいクリップの開始位置は、[[Source Viewer]]上で設定した[[In Point]]の位置になる
- 既存のクリップを一切上書きしない
- 既存のクリップと新しいクリップが重なる場合、空き[[Track]]に挿入される。空き[[Track]]がない場合は自動で作成される。
- [[Playhead]]は追加したトラックの末尾に移動する
- Place on Top のショートカットキーは `F12`

#### Place on Topのワークフロー（[[cutaway]]の挿入）

1. タイムライン上の「[[cutaway]]を挿入したい範囲」に[[In Point]]と[[Out Point]]を追加する
2. アイキャッチクリップの開始箇所に [[Source Viewer]] で[[In Point]]を追加する
3. F12、またはドラッグアンドドロップでタイムラインにPlace on Top

[[Source Viwerに表示したクリップの映像のみ or 音声のみをタイムラインに追加する]]
[[Source ViewerにおけるSource Clip と Sorce Tapeの違い]]
