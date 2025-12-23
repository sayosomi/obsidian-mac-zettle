---
cssclasses:
  - sticky
  - pal-sand
created: 2025-12-20T11:59:01Z
modified: 2025-12-20T14:44:07Z
---
Flutter 
## 開発中の機能名
```
focus-lane-task-logger
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
testとanalyzeとbuildを実行しエラーが出てないか確認
修正後、再度確認して全部直ってたらcommit
```

## todo
- [ ] 終了レーンを押したときの動作を変更する
- [ ] 終了状態を解除するUI
- [ ] running状態のタスクがあるときは、起動時にフォーカスドロワーを表示する
- [ ] hive導入で完全ローカル対応