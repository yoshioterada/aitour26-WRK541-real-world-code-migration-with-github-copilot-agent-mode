# 用語集

この用語集はワークショップ全体で使用する主要な用語を定義します。わからない用語が出てきたら手早く参照してください。

## API 関連

**API (Application Programming Interface)**
: 異なるソフトウェア同士がやり取りするためのルールとプロトコル。

**Endpoint**
: API 内の特定の URL パス（例: `/countries`, `/weather`）。

**REST (Representational State Transfer)**
: 標準 HTTP メソッド（GET/POST/PUT/DELETE）を用いたネットワークアプリ設計スタイル。

**JSON (JavaScript Object Notation)**
: 人間が読み書きしやすく、機械も扱いやすい軽量データ形式。

**HTTP Methods**
: GET（取得）、POST（作成）、PUT（更新）、DELETE（削除）などの標準リクエスト種別。

**Status Code**
: リクエスト結果を示す 3 桁コード（例: 200 OK, 404 Not Found, 500 Internal Server Error）。

**Swagger/OpenAPI**
: REST API の仕様とツール群。対話的なドキュメントやテスト UI を提供。

## .NET & C# 関連

**ASP.NET Core**
: モダンな Web アプリ/API 向けのクロスプラットフォーム高速フレームワーク。

**Minimal APIs**
: ASP.NET Core で最小限のコードと設定で API を作るアプローチ。

**.NET SDK (Software Development Kit)**
: .NET アプリ構築・実行に必要なツール、ライブラリ、ランタイム。

**Runtime**
: .NET アプリの実行環境。メモリ管理やセキュリティを提供。

**NuGet**
: .NET のパッケージマネージャー。サードパーティライブラリや依存関係の管理に使用。

**System.Text.Json**
: JSON のシリアライズ/デシリアライズ用 .NET 組み込みライブラリ。

**Program.cs**
: .NET アプリのエントリポイント。アプリ設定と起動を行うファイル。

**Namespace**
: コードを整理し名前衝突を避けるための .NET の仕組み。

## Python 関連

**FastAPI**
: 自動ドキュメント生成を備えた高速な Python Web フレームワーク。

**Uvicorn**
: Python Web アプリを実行する ASGI サーバー。

**pip**
: Python のパッケージインストーラー。

**requirements.txt**
: プロジェクト依存の Python パッケージ一覧。

**Virtual Environment (venv)**
: プロジェクトごとに依存を分離する Python 仮想環境。

## テスト関連

**Unit Test**
: 関数/メソッド/クラスなど単一単位を検証するテスト。

**Integration Test**
: 複数コンポーネントの連携を検証するテスト。

**Test Client**
: 実サーバー不要で HTTP リクエストをシミュレートするツール。

**Assertion**
: 条件が真か検証するテスト記述。偽ならテスト失敗。

**Test Coverage**
: テストが実行したコード量の指標。

**pytest**
: Python の代表的なテストフレームワーク。

**MSTest**
: .NET アプリ用の Microsoft 製テストフレームワーク。

**WebApplicationFactory**
: .NET のインメモリ統合テストサーバー作成ツール。

## GitHub Copilot 関連

**GitHub Copilot**
: AI によるコード補完ツール。リアルタイムにコードや関数を提案。

**Copilot Chat**
: 質問・説明を自然言語でやりとりするチャットインターフェース。

**Context**
: Copilot が提案生成に利用する情報（開いたファイル、選択コード、チャット履歴）。

**Prompt**
: Copilot に投げる指示や質問。

**Ask Mode**
: 説明・質問・学習用モード。コード変更は行わない。

**Edit Mode**
: 自然言語指示に基づくピンポイントコード変更モード。

**Agent Mode**
: 計画・編集・コマンド実行を自律的に行うモード。

**Plan Mode**
: タスクを分解し計画を提示するモード。

**#file: Reference**
: Copilot チャットで特定ファイル文脈を与える記法（例: `#file:main.py`）。

**#codebase Tool**
: リポジトリ全体を分析し構造やコードに関する質問に答える機能。

## 開発ツール

**VS Code (Visual Studio Code)**
: 拡張機能が豊富な軽量エディタ。

**GitHub Codespaces**
: ブラウザで動作する事前構成済みのクラウド開発環境。

**Git**
: コード変更履歴管理とコラボレーションのためのバージョン管理システム。

**Terminal/Command Line**
: OS と対話しコマンドを実行するテキストインターフェース。

**Port**
: ネットワークリクエスト待ち受けの番号付きエンドポイント（例: 8000, 5000）。

## 一般的なプログラミング概念

**Migration**
: コードを別言語・フレームワーク・プラットフォームへ移行すること。

**Scaffolding**
: 初期開発を迅速にするためのプロジェクト構造や雛形生成。

**Serialization**
: データ構造/オブジェクトを保存・転送可能な形式（例: JSON）に変換。

**Deserialization**
: 形式化されたデータ（例: JSON）をデータ構造/オブジェクトに戻すこと。

**Type Safety**
: コンパイル時に型エラーを防ぐ仕組み。

**Compile-time**
: ソースコードを実行可能コードに変換する段階。ここで検出されるエラーは実行前に防げる。

**Runtime**
: プログラム実行中の段階。エラーは実行時に発生。

**Dependency**
: プロジェクトが動作に必要とする外部ライブラリやパッケージ。

**Boilerplate Code**
: 必要だが固有ロジックを持たない定型コード。

---

!!! tip "用語が見つからない？"
    ここにない用語は GitHub Copilot に尋ねるか、Resources ページの公式ドキュメントリンクを参照してください。
