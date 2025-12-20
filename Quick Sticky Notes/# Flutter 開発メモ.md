---
color: citrus
created: 2025-12-20T11:59:01Z
modified: 2025-12-20T14:44:07Z
---
# 開発中の機能名
focus-lane-task-logger

# Flutterエミュレータ起動
```shell
flutter clean
flutter pub get
flutter run -d emulator-5554 \
  --dart-define=USE_FIRESTORE_EMULATOR=true \
  --dart-define=FIRESTORE_EMULATOR_HOST=10.0.2.2 \
  --dart-define=FIRESTORE_EMULATOR_PORT=8080
```
別ターミナルでfirestoreも起動
```
firebase emulators:start --only firestore
```
# エミュ内でのパスワードの入れ方
`adb shell input text 'パスワード'`
- 別ターミナルを起動して行う