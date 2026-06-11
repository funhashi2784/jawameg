# 🏮 Nebuta Map

ねぶたの設置場所がわかるPWA地図アプリ（Leaflet + OpenStreetMap）。

## 起動方法

PWA（Service Worker）はローカルサーバー経由で動きます:

```bash
cd nebuta-map
python3 -m http.server 8000
# → http://localhost:8000 を開く
```

※ index.html をダブルクリックでも地図は動きますが、オフライン機能とインストールは無効になります。

## スマホへのインストール

HTTPSで公開（GitHub Pages / Netlify / Vercel など、無料）すると:

- **iPhone**: Safariで開く → 共有 → 「ホーム画面に追加」
- **Android**: Chromeで開く → 「アプリをインストール」

## Google My Mapsのデータ取り込み

1. My Mapsを開く → レイヤ名横の「⋮」→「KML/KMZにエクスポート」
2. アプリ右下の 📂 ボタンでそのファイルを選択
3. 「置き換え」or「追加」を選ぶ（端末に保存され、次回も維持されます）

My Mapsのレイヤ（フォルダ）名はカテゴリとして取り込まれ、description内の画像は詳細パネルの写真になります。

動作確認用に `sample-import.kml` を同梱しています。

## 機能

- カテゴリ別カラーピン + 絞り込みチップ
- 名前・説明の検索
- ピンタップで詳細パネル（写真・説明・Googleマップ経路案内）
- 📍 現在地表示 / 🗺️ 全ピン表示
- KML/KMZインポート（localStorageに永続化）
- オフライン対応（閲覧済み地図タイルもキャッシュ）

## ファイル構成

```
index.html            アプリ本体（HTML/CSS/JS一体）
manifest.webmanifest  PWA設定
sw.js                 Service Worker（オフラインキャッシュ）
icons/                アプリアイコン
sample-import.kml     インポートテスト用データ
```

サンプルピンのデータは `index.html` 内の `SAMPLE_NEBUTA` 配列にあります。
