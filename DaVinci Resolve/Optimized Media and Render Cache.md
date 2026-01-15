
[[Master Settings]]内の一項目。
[[Timeline Format]]と合わせて最初に設定する。

## 推奨設定

![](https://i.gyazo.com/33d49ad41d6b0fc346eebe999db63b5d.png)

- Proxy media resolution: Generate Proxy Media で作られるプロキシの解像度
- Proxy media format: プロキシのコーデック
- Render cache format: Render Cache が作るキャッシュファイルのコーデック
- Enable background caching after `N` seconds: 再生ヘッドを止めて `N`秒間何もしないと、バックグラウンドでキャッシュ作成を始める
- Automatically cache transitions in user mode: **Playback > Render Cache > User** のときに、トランジションを自動でキャッシュ対象にする
- Automatically cache composites in user mode: **Playback > Render Cache > User** のときに、**合成系**（複数レイヤー/ブレンド/キー/一部の複合処理）を自動キャッシュ対象にする
- Automatically cache Fusion effects in user mode: **Playback > Render Cache > User** のときに、**Fusion系エフェクト**を自動キャッシュ対象にする

## 特にいじらなくていい設定

- Optimized media resolution: Generate Optimized Media で作られる最適化メディアの解像度
- Optimized media format: 最適化メディアのコーデック

## 関連

[[Proxy Media と Optimized Media の違い]]
