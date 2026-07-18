# DevStack | 案件で使うWeb開発

技術メディア「DevStack」のポートフォリオサイトです。Astro 5で生成する静的サイトとして構成し、GitHub Pagesで公開します。画面はJavaScriptに依存せず、AstroコンポーネントとCSSを中心に実装しています。

## 開発

Node.js 22以降とpnpm 10を用意してください。

```sh
pnpm install
pnpm dev
```

本番用ファイルの生成とローカル確認は次のコマンドで行います。

```sh
pnpm build
pnpm preview
```

生成先は `dist/` です。`main` ブランチへpushすると、GitHub ActionsがビルドしてGitHub Pagesへデプロイします。

## データの更新

成果物は `src/data/works.json`、記事は `src/data/articles.json` を編集すると画面へ反映されます。JSONにはコメントを書けないため、各項目の意味をここにまとめています。

### `works.json`

```json
{
  "title": "画面に表示する成果物名",
  "description": "1行程度の説明",
  "tags": ["技術タグ1", "技術タグ2"],
  "url": "https://成果物のURL",
  "placeholder": false
}
```

- 公開済みカードは `url` を設定し、`placeholder` を `false` にします。
- 予告カードは `url` を空文字にし、`placeholder` を `true` にします。
- カードを追加するときは、直前の項目末尾にカンマを付けてから同じ形のオブジェクトを追加します。

### `articles.json`

```json
{
  "title": "記事タイトル",
  "description": "記事の短い説明",
  "url": "https://記事のURL"
}
```

- `url` が空文字の項目は「Preparing...」としてリンクなしで表示されます。
- URLを設定すると、自動的にリンクへ切り替わります。

更新後は `pnpm build` を実行し、JSONの構文とサイト生成を確認してください。
