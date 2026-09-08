# Gitでホームページを元に戻す練習

架空のカフェ「KOMOREBI」の静的ホームページです。インストールやビルドは不要です。

## 表示する

`index.html` をブラウザで開きます。編集後は再読み込みしてください。

## 用意した状態

- `good-style` タグ：正常なデザインの保存地点。
- `main` の最新コミット：CSSをわざと崩した状態。復元はまだ実行していません。
- 崩した内容：配色、文字サイズ、余白、カラム配置、カップの形。

## 自分で復元する

作業フォルダでターミナルを開き、以下を順番に実行します。

```sh
git switch main
git pull --ff-only origin main
git status
git log --oneline -5
```

未コミットの変更がないことと、最新コミットが `practice: intentionally break homepage styles` であることを確認します。最新が別のコミットなら、以下の `HEAD` を履歴にある破損コミットのIDに置き換えます。

```sh
git revert --no-edit HEAD
git push origin main
```

`git revert` は破損コミットの変更を打ち消す新しいコミットを作ります。過去の履歴は残ります。実行後にブラウザを再読み込みして、正常なデザインに戻ったことを確認してください。

## 復元前に正常な見た目を見る

未コミットの変更がない状態で実行します。

```sh
git switch --detach good-style
```

ブラウザで表示を確認したら、次で壊れた状態のブランチに戻ります。

```sh
git switch main
```

## 差分を見る

```sh
git diff good-style -- style.css
```

GitHubへのpushはコードの保存です。GitHub PagesでのWeb公開設定は含みません。
