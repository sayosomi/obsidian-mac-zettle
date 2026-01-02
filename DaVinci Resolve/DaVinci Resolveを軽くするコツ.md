---
tags:
  - ChatGPT
---
Resolveは設定と運用で体感がガラッと軽くなります。M1 Mac mini（16GB）＋ZV-E10 4K30p（XAVC S系＝Long-GOP）だと、特に **「デコードを軽くする」**のが効きます。

## まずこれだけやる（効果が大きい順）

### 1) プロキシを作る（最重要）

ZV-E10の4KはH.264/HEVCのLong-GOPなので、そのまま編集すると重くなりがち。
Resolveで **ProRes Proxy** にして編集すると一気に軽くなります。

* メディアプールで素材を選択 → 右クリック → **Generate Proxy Media**
* 事前に設定：**DaVinci Resolve > Preferences > Media Storage / Proxies** あたりで

  * Proxy codec：**Apple ProRes Proxy**
  * Proxy resolution：**Half** か **Quarter**
* 使う設定：上メニュー **Playback > Proxy Handling > Prefer Proxies**

※Optimized Mediaでも良いけど、最近のResolveは「Proxy運用」が分かりやすくて強いです。

### 2) タイムラインの“表示だけ”軽くする

* **Playback > Timeline Proxy Mode > Half / Quarter**
* ビューアの再生が重い時に即効。

### 3) Render Cacheを使う（合成・テロップ多いほど効く）

* **Playback > Render Cache > Smart**（まずはこれ）
* 重い所だけなら **User** にして、該当クリップ右クリック → **Render Cache Color Output** など

Project Settings（歯車）→ **Master Settings**

* Optimized media / Render cache format：**ProRes 422 LT** か **ProRes Proxy**（軽さ優先ならProxy）

### 4) 編集中は“解像度を下げて”、書き出しだけ4K

プロジェクト設定で

* Timeline Resolution：**1920×1080**（編集用）
* Deliverで **4K書き出し**（最終出力）

これ、見た目はほぼ変わらず体感が軽くなりやすいです（特にテロップ多い時）。

---

## 地味に効くやつ（詰まったら）

### 5) 保存場所を速いSSDにする

* 素材・キャッシュ・プロキシは **内蔵SSD** か **速い外付けSSD**へ
* Project Settings → **Working Folders** の Cache を速い場所へ

### 6) 重い機能を“編集時だけ”オフにする

* ノイズ除去、ブラー、強いシャープ、速度変更の高品質補間、AI系（Studio機能）などは重いです
  → 編集中は無効化して、仕上げでONに

### 7) Fusionは“溜め込まない”

口パク・まばたき等でFusionを使うなら

* Fusionページで **Cache to Disk** を活用
* ある程度固まったら **Fusionをレンダー済み素材に書き出して置き換え**（最強に軽い）