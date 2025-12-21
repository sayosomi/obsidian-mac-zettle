---
color: citrus
created: 2025-12-20T11:59:01Z
modified: 2025-12-20T14:44:07Z
---
Flutter 
## 開発中の機能名
**focus-lane-task-logger**
[tasks.md](file:///Users/yosomi/Code/task-logging-app/.kiro/specs/focus-lane-task-logger/tasks.md)
## Flutterエミュレータ起動
```shell
flutter clean
flutter pub get
```
必要なら初期化してから起動
```
flutter run -d emulator-5554 \
--dart-define=USE_FIRESTORE_EMULATOR=true \
--dart-define=FIRESTORE_EMULATOR_HOST=10.0.2.2 \
--dart-define=FIRESTORE_EMULATOR_PORT=8080 \
--dart-define=USE_FIREBASE_AUTH_EMULATOR=true \
--dart-define=FIREBASE_AUTH_EMULATOR_HOST=10.0.2.2 \
--dart-define=FIREBASE_AUTH_EMULATOR_PORT=9099
```
別ターミナルでfirestoreも起動
```
firebase emulators:start --only firestore,auth
```
## エミュ内でのパスワードの入れ方
`adb shell input text 'パスワード'`
- 別ターミナルを起動して行う
## エミュレータのリセットの仕方
```shell
adb shell pm clear com.example.task_logging_app
```
起動中に別のターミナルで行う