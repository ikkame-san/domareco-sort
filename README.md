# ドマレコ楽曲ソート

ドラマチックレコードの好きな曲を選び、自分のランキングを作る非公式ファンサイトです。「デビルアンセムソート」を参考にしています。

## 起動

親フォルダーの「起動.cmd」、または親フォルダーで npm start を実行し、http://127.0.0.1:4180 から選べます。Node.js 20.9以上が必要です。画像は同梱済みで起動にnpm installは不要です。

このフォルダーだけの場合は node scripts/serve.mjs で起動し、http://127.0.0.1:4183 を開きます。index.htmlの直接ダブルクリックには対応していません。

## 機能

- 曲名検索、公開年による絞り込み、ランキング対象の選択、自分で曲を追加
- 上位15曲・25曲・全曲・任意の順位数、2曲比較、3～4曲の順番選択
- 途中保存・再開、30回分の戻る操作
- ジャケット入りPNG、結果リンク・テキストのコピー、Xへの共有
- 公式MV・ダンス動画・ライブ映像の表示、未確認曲はYouTube検索
- スマートフォン対応、他グループから独立した保存キー domareco-sort:v1

## 曲目と出典

2026-10-08確認、42曲・YouTube公式映像28曲。TuneCore Japanの公式アーティストページ41作品と、別レーベルから配信された「ふたりシトラス」のApple Music情報を照合。

- [配信一覧](https://www.tunecore.co.jp/artists/DramaticRecord?lang=ja)
- [公式YouTube](https://www.youtube.com/@dmrcofficial)

公式YouTubeの全220投稿を追加ページまで取得し、採用動画の投稿元、曲名、公開日、尺を確認しました。MV、ダンス動画、ライブ映像の順で優先し、同種では新しい映像を採用します。通常のMVを確認できない「帯びていく青」などのLive Music Videoはライブ映像と表示します。

SE・OVERTURE、インスト、カラオケは除外し、同じ曲の再収録はまとめています。リミックス・別言語版がある場合は別曲です。個人名義のみの作品、コンサート全編、告知、Shorts、舞台裏は曲別リンクに採用していません。日付は確認した作品のうち最も早い発売日で、初披露日とは限りません。配信前・未配信の曲は、UIから手動で追加できます。

曲別の出典はsongs.jsのsources、ジャケットの取得元はartworkSource、映像の取得元はvideo.sourceに残しています。コピー用の曲一覧は曲一覧.txt、映像の一覧は動画確認一覧.mdです。音源・歌詞は同梱していません。

## 保存と保守

選択・途中結果・追加曲・名前はブラウザ内に保存します。共有URLのフラグメントには順位・曲名・任意の名前・作成日・対象曲数が入ります。ローカル起動中のリンクは他の端末から開けません。

通常の確認は npm run check と npm test。画像の再取得時だけ npm ci を実行してから node scripts/build-jackets.mjs を実行します。画像は256pxのWebPで、PNG出力も同一オリジンの画像を使います。データ再調査は親READMEを参照してください。

単独公開に必要なファイルは index.html、app.js、engine.js、songs.js、jackets.js、catalog.js、styles.css、favicon.svg、jackets/ です。参考プロジェクトがなくても動作します。

本サイトは非公式で各グループ・関係会社とは関係ありません。

## GitHub Pages

公開先: https://ikkame-san.github.io/domareco-sort/

リポジトリ: https://github.com/ikkame-san/domareco-sort

mainブランチのルートをGitHub Pagesの公開元に設定します。.nojekyllで静的ファイルをそのまま配信します。変更をmainへpushすると自動で再公開されます。

## 2026-10-25 新曲追加

「ノーマルエンド」「未明論」を追加し、全44曲。両曲は[TWIN PLANET公式発表](https://prtimes.jp/main/html/rd/p/000000994.000025517.html)に基づき、2026-10-21のShibuya LOVEZ公演での初披露日を記録しています。配信の発売日とは区別し、ジャケットは未設定です。公式YouTubeの新着一覧と曲名検索では曲別公式動画を確認できなかったため、検索リンクを表示します。従来の公式映像28曲は維持。

ルートの `node scripts/add-domareco-202610.mjs` で再適用できます。基礎データの再生成後にも本スクリプトを実行してください。
