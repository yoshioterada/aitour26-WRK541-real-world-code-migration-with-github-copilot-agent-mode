# ドキュメントの用語ガイド

WRK541 ドキュメントで用いる用語を統一し、明確さとプロフェッショナルさを保つためのガイドです。

## 製品名（正式表記）

### 初出では正式名称を使用

**GitHub Copilot**
: 各ドキュメントの初出は "GitHub Copilot"、以降は "Copilot"。
: ✅ 例: "GitHub Copilot helps you write code. Copilot uses AI..."
: ❌ 初出で "Copilot helps you write code"

**ASP.NET Core Minimal APIs**
: "ASP.NET Core" と "Minimal APIs" を正しく大文字に。

**FastAPI**
: 一語、F と API を大文字。

**.NET**
: 先頭に '.' を付けて大文字表記（`.NET 10`）。CLI コマンドの `dotnet` は小文字。

**Visual Studio Code**
: 初出は正式名、その後は "VS Code"。

## Copilot モード

特定モード名は大文字で:

- **Ask Mode**
- **Agent Mode**
- **Plan Mode**

例: "Use Agent Mode to scaffold the project" ✅

## フレームワーク/ライブラリ名

**Python**: ✅ "Python 3.12"

**C#**: ✅ "C#"

**JSON**: ✅ "JSON"

**Swagger**: ✅ "Swagger"

**OpenAPI**: ✅ "OpenAPI"

## テストフレームワーク

**pytest**: 小文字、一語

**MSTest**: 先頭 MS + T を大文字

## ファイル/コード参照

**Program.cs**: 大文字小文字を厳守

**main.py**: 小文字

**weather.json**: 小文字

## 技術用語

**API Endpoint**: 2語。文頭のみ大文字。

**Repository/Repo**: フォーマルは "repository"、カジュアルは "repo"。

**GitHub Codespaces**: 2語、大文字。

**port**: "port 8000" のように記述（環境変数を除き大文字にしない）。

## CLI ツール

**dotnet**: コマンドは小文字

**git**: 小文字

**pip**: 小文字

## ドキュメントスタイル

### 見出し

タイトルケース:
✅ "Understanding the Project"
❌ "Understanding The Project"

### 箇条書き

- 先頭は大文字
- 完全文なら末尾にピリオド
- 断片ならピリオド不要

### コードブロック

言語を指定すること:

```csharp
var app = WebApplication.Create();
```

```python
app = FastAPI()
```

## よくある誤り

|❌ 誤り|✅ 正|Note|
|---|---|---|
|Copilot Chat|GitHub Copilot Chat|初出はフル名称|
|.Net|.NET|大文字|
|Minimal api|Minimal API|API を大文字|
|fast api|FastAPI|1語|
|Github|GitHub|大文字 H|
|VScode|VS Code|スペース必要|
|Csharp|C#|`#` を使用|

## バージョン表記

✅ "Python 3.12", ".NET 10", "VS Code 1.85"
❌ "Python 3", ".NET"

## プラットフォーム/OS

**Windows**: ✅ "Windows 10/11"
**macOS**: ✅ "macOS"
**Linux**: ✅ "Linux" または "Ubuntu 20.04"

## まとめ

用語統一は以下を向上:

- **信頼性**: 正しい製品名で専門性を示す
- **明確性**: 読者が意図を正しく理解
- **検索性**: 正しい用語で情報が見つかりやすい
- **信用**: 正確な用語使用は専門性の証

迷ったら公式ドキュメントを確認しましょう。
