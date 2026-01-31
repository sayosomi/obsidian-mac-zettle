# DaVinci Resolve（Fairlight）で複数WAVを同条件で処理→元ファイル単位で書き出す手順メモ

## 目的

- 複数wavをまとめて
    
    - **ラウドネス正規化：ITU-R BS.1770-4 / Independent / -18 LKFS**
        
    - **コンプレッサー：Ratio 3:1 / Threshold -20dB（GR -6dB前後）**
        
    - （必要なら）Make up 相当を +6dB
        
- **出力は「元wavごとに1ファイル」**
    
- Deliver の **Individual clips** ではトラックDynamicsが反映されないことがあるため、**Export Audio Files** を使う
    

---

## 0) 前提（重要）

- タイムライン上は **1ファイル＝1クリップ（切ってない）**
    
- トラック/バスのDynamicsは、個別書き出しでは効かないことがある  
    → **クリップ側に処理を寄せる** のが確実
    

---

## 1) wavをタイムラインに並べる

1. Media Pool に wav をまとめて入れる
    
2. タイムラインに配置（順番は自由）
    
3. クリップが分割されていないことを確認（1ファイル=1クリップ）
    

---

## 2) ラウドネスを揃える（-18 LKFS）

1. タイムライン上の対象クリップを全部選択（Cmd+A）
    
2. 右クリック → **Normalize Audio Levels…**
    
3. 設定：
    
    - **Normalization Mode：ITU-R BS.1770-4（LUFS/LKFS）**
        
    - **Set Level：Independent**
        
    - **Target Loudness：-18 LKFS**
        
4. OK
    

---

## 3) コンプレッサーを“クリップ側”に適用（トラックDynamicsじゃなく）

> Deliver/個別書き出しで確実に反映させるため、**クリップFX（Clip EQ and FX）**としてかける

1. クリップ全選択のまま、Inspector（Audio）または Clip Effects から **Compressor** を追加
    
2. 設定：
    
    - **Ratio：3:1**
        
    - **Threshold：-20 dB**
        
    - **Attack：1.4 ms**
        
    - **Release：93 ms**
        
    - **Knee：0**
        
    - **Mix：100%**（パラレルにしない）
        
3. GRが -6dB前後になるか目視で確認（素材で多少ズレてもOK）
    

### Make up +6 dB について

- この手順では「Make upノブ」が無い場合があるので、代替はどちらか：
    
    - **Clip Gain を +6 dB**（クリップゲイン）
        
    - または書き出し後に別工程で +6 dB  
        （今回は“最終的に狙い通りの音量になればOK”で運用）
    Busを + 6するって意味だよ！
        

---

## 4) 元wavごとに書き出す（ここが肝）

1. タイムラインで書き出したいクリップを全部選択（Cmd+A）
    
2. 右クリック → **Export Audio Files…**
    
3. ダイアログ設定：
    

### 上段

- **Folder**：出力先フォルダ指定
    
- **File name：Clip name**（元ファイル名で出したい）
    
- （任意）**Also add to Media Pool**：ONだと書き出し物がメディアプールにも入る
    

### File format（音の仕様）

- **File format：BWAV**（WAVでもOK）
    
- **Sample rate：Same as project**
    
- **Bit depth：24**
    
- **Channel format：Mono か Stereo（素材に合わせる）**
    
    - ※`Multi mono` は意図がない限り避ける（L/Rが別扱いになることがある）
        

### Export（分割）

- **Export：Individual clips**
    
- **From：Selected clips**
    

### Export with（反映させるもの）

- ✅ **Clip level**
    
- ✅ **Clip fades**
    
- ✅ **Clip EQ and FX** ← これが重要（クリップ側コンプを含める）
    
- （任意）Clip XML：不要ならOFFでもOK
    

### Normalize（ここではしない）

- **Normalize：No normalization**
    
    - ※すでに -18LKFS をやってるので二重にしない
        

4. **Export** を押す
    

---

## 5) うまくいったか確認

- 書き出した各wavを再生して、コンプ感がある／音量が揃ってる
    
- Single clip書き出しで聴いた“効いてる音”に近いことを確認
    

---

## つまづきポイント（原因と回避）

- Deliver の **Individual clips** は「ソース直書き」寄りになり、**トラックDynamicsが反映されない**ことがある  
    → **Export Audio Files** を使う（またはクリップFX化する）
    
- 「Rボタンがオンにできない」  
    → 録音用なので今回不要