# GitHub Copilot Agent Mode で実践するコード移行

このワークショップの手順は GitHub Pages で公開されています:
[https://aka.ms/WRK541Workshop](https://aka.ms/WRK541Workshop)

この `docs` フォルダーには、その手順サイトのソースコードが含まれます。

## MKDocs

手順は MKDocs で記述され、この dev container には `mkdocs` コマンドがインストールされています。詳細は [mkdocs.org](https://www.mkdocs.org) を参照してください。

利用している MKDocs 拡張:

* [Material for MkDocs](https://squidfunk.github.io/mkdocs-material/)
* [glightbox MKDocs plugin](https://blueswen.github.io/mkdocs-glightbox/)

## GitHub Pages へのデプロイ

このリポジトリのワークショップ手順を GitHub Pages にデプロイするには次を実行します:

```
cd docs
mkdocs gh-deploy
```

### その他の mkdocs コマンド

* `mkdocs serve` - ライブリロード付きドキュメントサーバーを起動
* `mkdocs build` - ドキュメントサイトをビルド
* `mkdocs -h` - ヘルプを表示して終了

## プロジェクト構成

    mkdocs.yml    # 設定ファイル
    docs/
        docs/
            index.md  # ドキュメントのホームページ
            ...       # その他の Markdown、画像、ファイル
