---
tags:
  - ChatGPT
---
Resolve は設定と運用で体感がガラッと軽くなります。M1 Mac mini（16GB）＋ZV-E10 4K30p（XAVC S 系＝Long-GOP）だと、特に **「デコードを軽くする」**のが効きます。

## まずこれだけやる（効果が大きい順）

### 1) プロキシを作る（最重要）

ZV-E10 の 4K は H.264/HEVC の Long-GOP なので、そのまま編集すると重くなりがち。
Resolve で **ProRes Proxy** にして編集すると一気に軽くなります。

* メディアプールで素材を選択 → 右クリック → **Generate Proxy Media**
* 事前に設定：**DaVinci Resolve > Preferences > Media Storage / Proxies** あたりで
  * Proxy codec：**Apple ProRes Proxy**
  * Proxy resolution：**Half** か **Quarter**
* 使う設定：上メニュー **Playback > Proxy Handling > Prefer Proxies**

※Optimized Media でも良いけど、最近の Resolve は「Proxy 運用」が分かりやすくて強いです。

### 2) タイムラインの“表示だけ”軽くする

* **Playback > Timeline Proxy Mode > Half / Quarter**
* ビューアの再生が重い時に即効。

### 3) Render Cache を使う（合成・テロップ多いほど効く）

* **Playback > Render Cache > Smart**（まずはこれ）
* 重い所だけなら **User** にして、該当クリップ右クリック → **Render Cache Color Output** など

Project Settings（歯車）→ **Master Settings**

* Optimized media / Render cache format：**ProRes 422 LT** か **ProRes Proxy**（軽さ優先なら Proxy）

### 4) 編集中は“解像度を下げて”、書き出しだけ 4K

プロジェクト設定で

* Timeline Resolution：**1920×1080**（編集用）
* Deliver で **4K 書き出し**（最終出力）

これ、見た目はほぼ変わらず体感が軽くなりやすいです（特にテロップ多い時）。

---

## 地味に効くやつ（詰まったら）

### 5) 保存場所を速い SSD にする

* 素材・キャッシュ・プロキシは **内蔵 SSD** か **速い外付け SSD**へ
* Project Settings → **Working Folders** の Cache を速い場所へ

### 6) 重い機能を“編集時だけ”オフにする

* ノイズ除去、ブラー、強いシャープ、速度変更の高品質補間、AI 系（Studio 機能）などは重いです
  → 編集中は無効化して、仕上げで ON に

### 7) Fusion は“溜め込まない”

口パク・まばたき等で Fusion を使うなら

* Fusion ページで **Cache to Disk** を活用
* ある程度固まったら **Fusion をレンダー済み素材に書き出して置き換え**（最強に軽い）
