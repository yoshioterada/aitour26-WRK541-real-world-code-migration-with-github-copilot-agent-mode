<p align="center">
<img src="img/Banner-MS-AI-Tour-26.png" alt="decorative banner" width="1200"/>
</p>

# [Microsoft AI Tour 2026](https://aitour.microsoft.com)

## WRK541: GitHub Copilot Agent Mode を使った実践的コード移行

[![Microsoft Foundry Discord](https://dcbadge.limes.pink/api/server/Pwpvf3TWaw)](https://aka.ms/MicrosoftFoundryDiscord-AITour26)
[![Microsoft Foundry Developer Forum](https://img.shields.io/badge/GitHub-Microsoft_Foundry_Developer_Forum-blue?style=for-the-badge&logo=github&color=adff2f&logoColor=fff)](https://aka.ms/MicrosoftFoundryForum-AITour26)

このセッションを担当する方は、スライドやスクリプトなどのリソースがある [session-delivery-resources](./session-delivery-resources/) フォルダーを確認してください。

### セッション概要

- **対象**: GitHub Copilot を使ったペアプロで、言語間移行や翻訳のような難易度の高い作業に挑戦したいすべての技術者
- **学べること**: 言語移行に特に有効な高度な GitHub Copilot テクニックと、Copilot の各モードの使い分け
- **作るもの**: Python から C# (.NET Minimal APIs) への HTTP API 移行。Copilot を使った現実的なコード移行の進め方を体験します。

### 🧠 学習成果

このワークショップで得られること:

- GitHub Copilot の各モードの違い、使いどころ、ベストプラクティスと支援ツール
- Web 開発における Python と C# の違い（構文・ライブラリ・フレームワーク）を理解（FastAPI → ASP.NET Core Minimal APIs）
- C# での JSON シリアライズ／デシリアライズ（System.Text.Json で JSON データを扱い、元の Python API と互換性を確保）
- C# でのエンドポイントを段階的に実装・検証（元の Python API に合わせて逐次テスト）
- Swagger/OpenAPI ドキュメント統合（Swashbuckle と ASP.NET Core の OpenAPI サポート）
- MSTest を使ったユニットテスト（MSTest + WebApplicationFactory で API 機能を検証）

## 📣 前提条件

ワークショップ参加に必要なのは **公開 GitHub アカウント** のみです。リポジトリにすべてのリソース・依存関係・データが含まれています。GitHub Copilot ライセンス（試用版や無料版でも可）を有効にしておいてください。

### 好きな環境でワークショップを実行

- **ローカル環境**: Git / GitHub Copilot を有効にした VS Code / Python 3.12 / .NET 10 SDK が揃っていれば、リポジトリをクローンしてローカルで演習できます。詳細チェックリストは [PREREQUISITES.md](./PREREQUISITES.md) を参照。リソースページに必要ツールの簡易リマインダーもあります。
- **GitHub Codespaces**: インストール不要がよければ、リポジトリから Codespace を起動してクラウドで進められます。手順は [`docs/ja/opening-repository-in-GH-codespaces.md`](./docs/ja/opening-repository-in-GH-codespaces.md) にあります。

### 💻 使用技術

1. GitHub Copilot Chat
1. VS Code
1. Python 3.12
1. C# (.NET 10 Minimal APIs)
1. MSTest（ユニットテスト）
1. Swagger/OpenAPI（API ドキュメント）

### 📚 学習継続のためのリソース

| リソース | リンク | 説明 |
|:-------------------|:----------------------------------|:-------------------|
| AI Tour 2026 リソースセンター | <https://aka.ms/AITour26-Resource-center> | AI Tour 26 セッションの全リポジトリリンク |
| Microsoft Foundry Community Discord | [![Microsoft Foundry Discord](https://dcbadge.limes.pink/api/server/Pwpvf3TWaw)](https://aka.ms/MicrosoftFoundryDiscord-AITour26)| Microsoft Foundry コミュニティに参加！ |
| Learn at AI Tour | <https://aka.ms/LearnAtAITour> | Microsoft Learn で学習を継続 |
| Code with GitHub Codespaces | <https://learn.microsoft.com/training/modules/code-with-github-codespaces/> | GitHub Codespaces を試す |
| GitHub Copilot 高度な機能 | <https://learn.microsoft.com/training/modules/advanced-github-copilot/> | Copilot の高度な機能とツール |

### 🌐 多言語対応

追加言語は順次公開予定です。

## コンテンツオーナー

<!-- TODO: Add yourself as a content owner
1. Change the src in the image tag to {your github url}.png
2. Change INSERT NAME HERE to your name
3. Change the github url in the final href to your url. -->

<table>
<tr>
    <td align="center"><a href="https://github.com/elbruno">
        <img src="https://github.com/elbruno.png" width="100px;" alt="Bruno Capuano"/><br />
        <sub><b> Bruno Capuano</b></sub></a><br />
            <a href="https://github.com/elbruno" title="talk">📢</a>
    </td>
    <td align="center"><a href="https://github.com/gcordido">
        <img src="https://github.com/gcordido.png" width="100px;" alt="Gustavo Cordido"/><br />
        <sub><b>Gustavo Cordido</b></sub></a><br />
            <a href="https://github.com/gcordido" title="talk">📢</a>
    </td>
</tr></table>

## Responsible AI（責任ある AI）

Microsoft は、お客様が AI 製品を責任を持って利用できるよう支援し、透明性の高い情報提供やインパクト評価などの取り組みを通じて信頼関係を構築します。詳細は [https://aka.ms/RAI](https://aka.ms/RAI) を参照してください。

大規模な自然言語・画像・音声モデルは、不公平・信頼性欠如・不快と感じられる出力を生成する可能性があり、害を引き起こす恐れがあります。リスクと制限については [Azure OpenAI Service Transparency note](https://learn.microsoft.com/legal/cognitive-services/openai/transparency-note?tabs=text) を確認してください。

これらのリスクを抑える推奨アプローチは、危険な動作を検知・防止するセーフティシステムをアーキテクチャに組み込むことです。[Azure AI Content Safety](https://learn.microsoft.com/azure/ai-services/content-safety/overview) は、ユーザー生成・AI 生成コンテンツの有害性を検知する独立した保護レイヤーを提供します。テキスト・画像 API を備え、Azure AI Foundry ポータルではサンプルコードを用いて検証できます。[クイックスタート](https://learn.microsoft.com/azure/ai-services/content-safety/quickstart-text?tabs=visual-studio%2Clinux&pivots=programming-language-rest) も参照してください。

また、マルチモーダル・マルチモデルアプリの性能（期待する動作を満たし、有害な出力を抑えること）を評価することも重要です。[Performance and Quality] および [Risk and Safety] の評価指標を利用し、[カスタム評価](https://learn.microsoft.com/azure/ai-studio/how-to/develop/evaluate-sdk#custom-evaluators) も作成できます。

開発環境では [Azure AI Evaluation SDK](https://microsoft.github.io/promptflow/index.html) を使って評価できます。テストデータセットやターゲットに対する生成結果を、組み込みまたはカスタムの評価指標で定量的に計測できます。開始は [クイックスタート](https://learn.microsoft.com/azure/ai-studio/how-to/develop/flow-evaluate-sdk) を参照し、実行結果は [Azure AI Foundry ポータルで可視化](https://learn.microsoft.com/azure/ai-studio/how-to/evaluate-flow-results) できます。
