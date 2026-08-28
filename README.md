# でてくログ サポートサイト

iOS アプリ「でてくログ」のプライバシーポリシーとサポートページ。
App Store Connect の「プライバシーポリシーURL」と「サポートURL」に登録するために置いている。

GitHub のユーザーサイト（リポジトリ名 `detekulog.github.io`）として公開するので、
URL にリポジトリ名が入らない。

| ページ | URL |
|---|---|
| ホーム | https://detekulog.github.io/ |
| プライバシーポリシー | https://detekulog.github.io/privacy/ |
| サポート | https://detekulog.github.io/support/ |

素の HTML と CSS だけで、JavaScript もビルド手順も無い。審査で開かれるページなので、
表示に何かを必要とする作りにしない。

```
index.html          ホーム（アプリの紹介）
privacy/index.html  プライバシーポリシー
support/index.html  サポート・よくある質問
assets/style.css    共通のスタイル（アプリのブランド色・角丸に合わせてある）
.nojekyll           GitHub Pages の Jekyll 変換を止める（素の HTML をそのまま出す）
```

リンクはすべて相対パス。独自ドメインへ移してもそのまま動く。

## 公開の手順

1. GitHub で `detekulog.github.io` という名前の**公開**リポジトリを作る。
   ユーザーサイトはこの名前でなければならない（`<ユーザー名>.github.io`）。
   アプリ本体のリポジトリとは分けること。private リポジトリで Pages を使うには
   有料プランが要るうえ、ポリシーを公開するためにアプリのソースまで公開することになる。
2. push する。

   ```bash
   git remote add origin git@github.com:detekulog/detekulog.github.io.git
   git push -u origin main
   ```

3. Settings > Pages で Source が `Deploy from a branch` / `main` / `/ (root)` になっていることを確認する。
   ユーザーサイトは既定で有効になっていることが多い。
4. 数分待つと https://detekulog.github.io/ で開ける。

## 公開したら

- https://detekulog.github.io/privacy/ を App Store Connect の「プライバシーポリシーURL」に登録
- https://detekulog.github.io/support/ を「サポートURL」に登録

アプリ側の `DetekuLog/Support/AppLinks.swift` には、この URL を記入済み。

**提出前に、実際にブラウザで開いて確認すること。** 審査担当者はこのリンクを開く。
404 だとガイドライン 1.5 で差し戻される。

## 更新するとき

- ポリシーの中身を変えたら、`privacy/index.html` の「最終更新日」も必ず直す
- ポリシーの記述と、App Store Connect の「App のプライバシー」の回答を食い違わせない
  （現在はどちらも「データを収集しない」）
- アプリに機能を足して扱うデータが変わったら、公開前にポリシーを更新する
- 一度 App Store Connect に登録した URL は変えない
