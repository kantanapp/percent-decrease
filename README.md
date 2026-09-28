# Percent Decrease Practice（割合の減少 練習アプリ）

McGraw-Hill の宿題7問＋類題30問、計37問の練習アプリです。
`index.html` 1ファイルだけで動きます（サーバー・ビルド不要）。

## できること
- 37問を1問ずつ解く（McGraw-Hill と同じく各問2回まで）
- 画面に出るのは「問題文」と「解答欄」だけ。計算は本人が紙でやる前提です
  （公式・グラフ・解説・間違いのヒントは意図的に入れていません）
- 1回目を外すと「もう一度」、2回目も外すと正解の数字だけ表示
- 進捗画面：解いた数、正答率、1回目で正解した数、レベル別（Basic / Standard / Challenge）、全問の履歴
- 「間違えた問題だけ」「まだ解いていない問題だけ」に絞り込み
- 進捗はブラウザ（localStorage）に保存。同じ端末・同じブラウザなら閉じても残ります

## GitHub Pages で公開する手順
1. GitHub で新しいリポジトリを作る（例：`percent-decrease`）
2. `index.html` / `README.md` / `CLAUDE.md` をアップロード（Add file → Upload files）
3. Settings → Pages → Branch を `main`、フォルダを `/ (root)` にして Save
4. 1〜2分後に `https://<ユーザー名>.github.io/percent-decrease/` で開けます

## Claude Code で続きを作る
```bash
git clone https://github.com/<ユーザー名>/percent-decrease.git
cd percent-decrease
claude
```
Claude Code は起動時に `CLAUDE.md` を読むので、アプリの構成とルールを把握した状態で作業できます。
依頼例：
- 「percent increase（割合の増加）の問題を20問追加して、単元切り替えを付けて」
- 「進捗をCSVで書き出すボタンを付けて」
- 「1回目で正解した問題は次回から出にくくして」

公開URL：https://kantanapp.github.io/percent-decrease/

## 注意
- 進捗は端末ごとに別々です（iPhone と PC で共有されません）。
- 答えは小数第1位への四捨五入（0.5は切り上げ）で判定します。
