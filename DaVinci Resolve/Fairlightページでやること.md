https://chatgpt.com/c/696e5828-7640-8324-9eaf-3b18ee9e61bf

## 0) 前提（トラック構成）

1. **A1＝BGM**
2. **A2＝SE**
3. **A3＝VOICEPEAK（東北ずん子）**
4. **A4＝VOICEGER（ずんだもん）**

---

## 1) 声（A3/A4）を基準音量にそろえる

### 1-1. クリップをLUFSでノーマライズ（クリップごとに揃える）

1. A3のクリップをまとめて選択（トラック単位選択など）
2. **Right click > Normalize Audio Levels…**
3. 設定
    - **Normalization Mode：ITU-R BS.1770-4（LUFS/LKFS）**
    - **Set Level：Independent**
    - **Target Loudness：-18 LKFS**
4. A4も同じ設定で実行

---

## 2) 

### 2-1. Dynamics（内蔵）を使う

1. **Fairlight > Mixer**
2. A4チャンネルの **Dynamics（斜め線の四角）** を **ダブルクリック**
3. **Compressor ON**
4. 設定（最終的にあなたはこれで安定）
    - **Ratio：3:1*        
    - **Threshold：-20 dB**（結果として Gain Reduction が -6dB 前後）
    - **Make Up：+2 dB**
5. 確認：Gain Reduction の **C** がだいたい **-3〜-6 dB** くらい

---

## 3) 声の左右問題（A3が右だけ）を解決

1. A3が片耳だけに聞こえる問題が発生
2. 解決：トラックをモノラル化
    - **Track Header（A3）右クリック > Change Track Type To > Mono*
3. これで両耳（センター）に戻った

---

## 4) 声同士の最終バランスを耳で合わせる

1. Mixerで **A3 S（Solo）→再生**
2. **A4 S（Solo）→再生**
3. 体感で同じくらいになるように調整
    - 最終的にあなたは **A4＝+2.0 dB** で確定

---

## 5) BGM（A1）を声の邪魔にならない位置に固定＋冒頭だけ上げる

1. 声がある区間で「ちょうどいい」を決める
    - 最終：**A1＝-24 dB**（あなたの最終値）
2. 冒頭だけBGMを大きくしたい
    - 冒頭クリップを選択 → **Inspector > Audio > Volume** で **+9 dB**（-27→-18相当の発想）

---

## 6) SE（A2）の“うるさい個体”を一括で下げる（同一ソース多数）

1. 「同じSEが何度も出る」ので、個別調整を一括化したい
2. Media Pool の **Usage** は「場所一覧」だけで一括選択できなかった
3. 解決：**Indexパネルで検索 → 一括選択 → Inspectorで一括Volume**
    - **Workspace > Show Panel in Workspace > Index（Edit Index）**
    - 検索欄にSEのファイル名の一部を入力して絞り込み
    - リストをクリック → **⌘A（Command + A／コマンド エー）**で全選択
    - **Inspector > Audio > Volume** を下げて一括反映（タイムライン内の該当SE全部）

---

## 7) マスター（Bus1）で事故防止＋YouTubeラウドネス合わせ

### 7-1. Bus1にLimiter（保険）

1. **Fairlight > Mixer > Bus1 > Dynamics**（ダブルクリック）
2. **Limiter ON**
3. **Limiter Threshold：-1 dB**

### 7-2. Loudness MeterでIntegratedを見て全体ゲイン調整

1. Loudness Meter を **Reset**
2. 再生して **Integrated** を確認
3. 最終：Bus1を上げて **-14 LUFS付近**へ
    - 一度 +6 まで上げてから、最終的に **Bus1＝+5.0** に落ち着いた
4. Limiter の **L** がほとんど動かないことを確認（過圧縮になってない）

---

## 8) Deliver（書き出し）で二重正規化しな

1. 出力：**Audio＝Bus 1 (Stereo)、AAC**
2. **Normalize Audio：OFF**（Fairlight側で合わせたため）

---

必要なら、このまとめを「次回チェックリスト（順番固定の短い版）」にもできます。  
次は、**同じ作業をもっと自動化**するなら「テンプレ（Project Template）」や「Preset（Dynamics/Track）」の作り方も手順1つずつ案内できます。
