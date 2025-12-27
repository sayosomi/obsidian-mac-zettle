---
cssclasses:
  - sticky
  - pal-sand
created: 2025-12-20T11:59:01+00:00
modified: 2025-12-24T12:33:29+09:00
---

# flutter

## 開発中の機能名
```
planned-start-time
```
## Flutterエミュレータ起動
```shell
flutter clean
flutter pub get
```
事前にandroid studioで該当のエミュを起動sておくこと。
```
flutter run \
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
修正後再度確認し、全て直ったらcommit
```
## todo
- [x] 過去ログ表示
- [x] ログの編集
- [ ] 予定開始時刻をプロトタイプとレーンに実装。現在時刻を示す区切り線と自動スクロール
- [ ] 見積もり時間と終了予測時刻を実装
- [ ] 締め作業（見積もり時刻、仮プロトタイプ実装
- [ ] ）
	- 仮プロトタイプは期日（デフォルト当日）の締め作業時までにログが作られていなければ削除
- [ ] Hive導入でローカル対応
