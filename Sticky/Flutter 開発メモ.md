---
cssclasses:
  - sticky
  - pal-sand
created: 2025-12-20T11:59:01Z
modified: 2025-12-20T14:44:07Z
---
## 開発中の機能名
```
log-time-edit
```
[tasks.md](file:///Users/yosomi/Code/task-logging-app/.kiro/specs/focus-lane-task-logger/tasks.md)
## Flutterエミュレータ起動
```shell
flutter clean
flutter pub get
```
事前にandroid studioで該当のエミュを起動sておくこと。
```
flutter run -d emulator-5554 \
--dart-define=USE_FIRESTORE_EMULATOR=true \
--dart-define=FIRESTORE_EMULATOR_HOST=10.0.2.2 \
--dart-define=FIRESTORE_EMULATOR_PORT=8080 \
```
別ターミナルでfirestoreも起動
```
firebase emulators:start --only auth,firestore
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
修正後、再確認して全部直ってたらcommit
codexの
git実行を許可する
```

## todo
- [x] 過去ログ表示
- [ ] ログの編集
- [ ] 未着手タスクのみレーンに表示できる
- [ ] 予定開始時刻をプロトタイプとレーンに実装
- [ ] 見積もり時間と終了予測時刻を実装
- [ ] 締め作業（見積もり時刻、仮プロトタイプ実装）
	- 仮プロトタイプは期日（デフォルト当日）の締め作業時までにログが作られていなければ削除
- [ ] Hive導入でローカル対応