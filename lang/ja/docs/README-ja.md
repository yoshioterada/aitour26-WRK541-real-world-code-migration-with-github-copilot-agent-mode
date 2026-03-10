# GitHub Copilot Agent Mode で実践するコード移行

このワークショップは 下記の手順で行います:


| No. | タイトル | ファイル |
| --- | --- | --- |
| 1 | ホーム | [index.md](./ja/index.md) |
| 2 | ワークショップ・ナビゲーション | [navigating-workshop.md](./ja/navigating-workshop.md) |
| 3 | はじめに: ワークショップ紹介 | [workshop-introduction.md](./ja/workshop-introduction.md) |
| 4 | はじめに: リポジトリを開く（ローカルまたは GitHub Codespaces） | [opening-repository-in-GH-codespaces.md](./ja/opening-repository-in-GH-codespaces.md) |
| 5 | はじめに: プロジェクトを理解する | [understanding-project.md](./ja/understanding-project.md) |
| 6 | Copilot で戦略を立てる: プロジェクトを分析する | [analyze-project.md](./ja/analyze-project.md) |
| 7 | C# への移行: C# スキャフォールディングを作成する | [create-csharp-scaffolding.md](./ja/create-csharp-scaffolding.md) |
| 8 | C# への移行: エンドポイントを実装する | [implementing-endpoints.md](./ja/implementing-endpoints.md) |
| 9 | 検証とテスト: 正しさを確認し、さらにエンドポイントを追加する | [validate-correctness.md](./ja/validate-correctness.md) |
| 10 | 検証とテスト: C# テストを追加する | [add-csharp-tests.md](./ja/add-csharp-tests.md) |
| 11 | まとめ | [summary.md](./ja/summary.md) |
| 12 | ボーナスコンテンツ 1 | [Challenge-1.md](./ja/Challenge-1.md) |
| 13 | ボーナスコンテンツ 2 | [Challenge-2.md](./ja/Challenge-2.md) |
| 14 | 宿題 | [Homework.md](./ja/Homework.md) |
| 15 | 完成例ガイド | [completed-example-guide.md](./ja/completed-example-guide.md) |
| 16 | 用語集 | [glossary.md](./ja/glossary.md) |
| 17 | ドキュメント用語ガイド | [terminology-guide.md](./ja/terminology-guide.md) |
| 18 | 参加者から問い合わせのよくあるある質問: プロクター向け FAQ | [common-questions-faq.md](./ja/proctor-resources/common-questions-faq.md) |
| 19 | プロクター向けトラブルシューティングプレイブック | [troubleshooting-playbook.md](./ja/proctor-resources/troubleshooting-playbook.md) |
| 20 | 参加者進捗トラッカーテンプレート | [progress-tracker-template.md](./ja/proctor-resources/progress-tracker-template.md) |
| 21 | リソース | [resources.md](./ja/resources.md) |

この `docs` フォルダーには、その手順サイトのソースコードが含まれます。

## MKDocs

手順は MKDocs で記述され、この dev container には `mkdocs` コマンドがインストールされています。詳細は [mkdocs.org](https://www.mkdocs.org) を参照してください。

利用している MKDocs 拡張:

* [Material for MkDocs](https://squidfunk.github.io/mkdocs-material/)
* [glightbox MKDocs plugin](https://blueswen.github.io/mkdocs-glightbox/)

## GitHub Pages へのデプロイ

このリポジトリのワークショップ手順を GitHub Pages にデプロイするには次を実行します:

```text
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
