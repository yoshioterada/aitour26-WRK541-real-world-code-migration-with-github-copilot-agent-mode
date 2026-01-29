# WRK541 - GitHub Copilot Agent Mode で実践するコード移行

![Microsoft AI Tour Banner](./media/aitour-banner.png)

## 別言語へのチャレンジングな移行を実行

- **対象**: 言語間移行/翻訳など難度の高い作業を GitHub Copilot のペアプロで行いたい技術者
- **学べること**: 複数言語への移行に特に有効な Copilot の高度テクと各モードの使い分け
- **取り組む内容**: Python で書かれた季節データ取得 HTTP API を C# (.NET Minimal APIs) と完全互換で実装

## 学習目標

このワークショップで:

- GitHub Copilot 各モードの違いと使い時、ベストプラクティス、活用ツールを理解
- Web 開発における Python と C# の違いを理解
- FastAPI → ASP.NET Core Minimal APIs の構文/ライブラリ/フレームワーク差異を把握
- C# で JSON シリアライズ/デシリアライズを実装
- System.Text.Json で JSON データを扱い、元の Python API と互換性を確保
- C# で段階的にエンドポイントを実装・検証
- 個別エンドポイントを段階的にテストし、Python API と整合性を維持
- Swagger/OpenAPI ドキュメントを統合（Swashbuckle + ASP.NET Core 組み込み OpenAPI）

## 📣 前提条件

必要なのは **GitHub アカウント** のみ。リポジトリ内にすべてのリソース・依存・データが含まれます。GitHub Copilot（有料/試用/無料版）の利用を有効にしてください。

### ✅ 事前チェックリスト

開始前に以下を確認:

- [ ] **GitHub アカウント**: 作成済み・ログイン可
- [ ] **GitHub Copilot**: 有効化済み（有料/試用/無料）
- [ ] **環境選択**:
  - ☁️ **GitHub Codespaces**（推奨・ゼロセットアップ）
  - 💻 **ローカル開発**（Python 3.12, .NET 10 SDK, VS Code が必要。詳細は [Resources.md](./resources.md)）
- [ ] **ローカルの場合**: 事前条件インストール済み・検証済み

!!! tip "環境に迷ったら"
    **GitHub Codespaces** を推奨。事前構成済みでインストール不要です。

### GitHub アカウント作成手順

1. [GitHub サインアップページ](https://github.com/join)へ
2. メール/パスワード/ユーザー名を入力（個人メール推奨）
3. 国/地域を選択し、規約に同意
4. **Create account** クリック→メールの認証コードを入力
5. 完了！

![GitHub Account Sign Up](./media/github_signup.png)

準備ができたら右下の **"Workshop Navigation"** ボタンで次へ進みましょう。
