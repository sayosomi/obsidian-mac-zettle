---
cssclasses:
  - sticky
  - pal-sand
---
# flutter
## 開発中の機能名
```
prototype-list-add-today-lane
```
## Flutterエミュレータ起動
```shell
flutter clean
flutter pub get
```
事前にandroid studioで該当のエミュを起動しておくこと。
```
flutter run \
  --dart-define=USE_FIRESTORE_EMULATOR=true \
  --dart-define=FIRESTORE_EMULATOR_HOST=10.0.2.2 \
  --dart-define=FIRESTORE_EMULATOR_PORT=8080 \
  --dart-define=USE_FIREBASE_AUTH_EMULATOR=true \
  --dart-define=FIREBASE_AUTH_EMULATOR_HOST=10.0.2.2 \
  --dart-define=FIREBASE_AUTH_EMULATOR_PORT=9099
```
別ターミナルでfirestoreも起動
```
firebase emulators:start --only firestore,auth --project task-logging-app-27528
```
## エミュ内でのパスワードの入れ方
`adb shell input text 'パスワード'`
- 別ターミナルを起動して行う
## エミュレータのリセットの仕方
```shell
adb shell pm clear com.example.task_logging_app
```
起動中に別のターミナルで行う
## 整形
```
dart format lib test
```
リポジトリのルートで （または必要なサブディレクトリ）実行すると、Dartfmt 準拠で自動整形されます。
## いつもの
```
testとanalyzeとbuildを実行しエラーを確認
修正後再度確認し、全て直ったらcommit（詰まったら承認ダイアログを出す）
```

```
今のcommitに対しAndroidエミュ上で確認することは？
```
## Andrid エミュレータ上で特定のキーが効かない
エミュ画面の右側のツールバーから「…」 → settings → generalタブを選択し、以下の項目を設定
- **Send keyboard shortcuts to → Virtual device**（ショートカットをAndroid側へ送る） 
- **Enforce keycode forwarding → ON**（キーコードを強制転送）
## todo
- [x] 過去ログ表示
- [x] ログの編集
- [x] 予定開始時刻をプロトタイプとレーンに実装。現在時刻を示す区切り線と自動スクロール
- [x] 見積もり時間と終了予測時刻を実装
- [x] 締め作業（見積もり時刻
- [x] レーンタブの「プロトタイプからタスクを追加」ドロワーからもプロトタイプを追加できるようにして
- [x] 仮プロトタイプは期日（デフォルト当日）の締め作業時までにログが作られていなければ削除
- [x] プロトタイプにネクスト要素を追加
- [x] ログタブの個別ログ閲覧画面で、「編集」ボタンだけでなくカード全体をクリックの対象に。押すと編集画面に飛ぶ。スワイプで削除ボタンを出す動作は残す。
- [x] プロトタイプ編集画面でチェーンを選択後、そのチェーンの詳細を見る（+編集する）導線が欲しい。UIの案を出して
	- [x] レーンタブの「プロトタイプからタスクを追加」画面の編集アイコンを削除して、open_in_new アイコンに差し替えて
	- [x] open_in_newで詳細からプロトタイプ編集画面を開いた時、保存ができない。内容を変更しても何も変更しなくても、「保存」を押すと「操作中に問題が発生しました。再度お試しください。」と表示される
	- [x] プロトタイプ編集画面で、仮プロトタイプでない場合は「期日」の編集欄を非表示に
- [x] 仮プロトタイプはいかなる場所で表示される時も頭に`[仮]`の文字を付けて。プロトタイプタブの一覧みたいに。
- [ ] プロトタイプ一覧画面の各行の右端に、今日のレーンに追加するボタンを追加。追加済の場合はボタンは動作せず、追加済であるということが視覚的に区別できる。
- [ ] プロトタイプに「メモ」要素を追加。フォーカスドロワーからも参照・編集可能に
- [ ] オフ日設定と頻度設定の追加
- [ ] プロトタイプのエクスポート/インポート機能
- [ ] Hive導入でローカル対応
