  [ホーム]
  1) プロトタイプ作成
  2) ダミー（今後機能追加予定）
  …
  q) 終了
  > 1

  [プロトタイプ作成]
  名前（必須）:
  > Focus

  [プロトタイプ作成 ＞ 確認]
  3) 変更なし
  4) プロトタイプ名: Focus
  5) 予定開始時刻: null
  6) 見積もり（分）: null
  7) タグ: []
  8) URI: []
  9) 頻度: null
  q) 終了 
  > 1

  ... POST /prototypes

  [プロトタイプ作成 ＞ 完了]
  id: 7c9f...a21
  name: Focus

  10) ホームへ戻る
  11) 今日のタスクに追加
  12) プロトタイプ作成を続ける
  q) 終了 

----
## [プロトタイプ作成 ＞ 確認]の分岐

  1. 変更なし
     POST /prototypes を実行して完了画面へ。

  2. nameを編集
     nameを再入力 → [プロトタイプ作成 ＞ 確認] に戻る。

  3. plannedStartTimeを編集
     反映して [プロトタイプ作成 ＞ 確認] に戻る。

  4. dailyEstimateSecondsを編集
     秒換算して反映 → [プロトタイプ作成 ＞ 確認] に戻る。

  5. tagElementsを編集

  6. urlElementsを編集


  7. frequencyを編集
     頻度サブメニューへ（none/daily/weekday/monthly...）→ 決定後 [プロトタイプ作成 ＞ 確認] に戻る。
----
## 頻度サブメニュー

[プロトタイプ作成 > 頻度]
  現在: null
  1) なし
  2) 毎日
  3) 曜日指定 (weekday)
  4) 毎月の日付指定 (monthly_day)
  5) 毎年の日付指定 (yearly_date)
  6) 毎月 第N曜日 (monthly_nth_weekday)
  7) 最終実行境界 (last_execution_boundary)
  b) 確認画面へ戻る
  q) 終了

### 頻度設定詳細
1. 即確定: { "type": "null" }
2. 即確定: { "type": "daily" }
3. 曜日サブメニューへ
4. 