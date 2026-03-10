# C# スキャフォールディングを作成

> *このステップ以降は GitHub Copilot を Agent Mode で使いましょう。*

プロジェクトとテストの理解ができたら、C# スキャフォールディングを作成します。
まず **Copilot Instructions** ファイルを用意します。ファイルは
.github/instructions フォルダーに置きます。空のファイルは用意済みなので、
instructions.md に内容を記述します。

`.github\instructions\instructions.md` に以下を追加:

```markdown
# C# .NET 10 WebApi Migration Instructions

## Overview

This guide helps developers migrate the Python Weather API to
C# .NET 10 using ASP.NET Core Minimal APIs.

## Requirements

- **Framework**: ASP.NET Core Minimal APIs (.NET 10)
- **JSON Serialization**: System.Text.Json (built-in)
- **API Documentation**: Swashbuckle (OpenAPI/Swagger support)

## Development Workflow

- **Build**: `dotnet build`
- **Run**: `dotnet run`
- **Test**: `dotnet test` (tests in `WeatherApi.Tests` directory)
- **API Docs**: Available at `/swagger` endpoint when running

## C# API Guidelines

- Use **Minimal APIs** for endpoint definitions in `Program.cs`
- Use **System.Text.Json** for all serialization
- Add Swashbuckle attributes to endpoints for automatic Swagger documentation
- Follow PascalCase for class names, camelCase for methods
- Example: See `src/csharp-app/WeatherApi/Program.cs`

## Key Files

- `src/csharp-app/WeatherApi/Program.cs` - API configuration and endpoints
- `src/csharp-app/WeatherApi.Tests/` - Unit tests
- `src/csharp-app/WeatherApi/Models.cs` - Data models
- `src/csharp-app/WeatherApi/weather.json` - Sample data
```

<!-- markdownlint-disable MD046 -->
??? warning
    新しいチャットを開始するとコンテキストがリセットされ、Copilot がより鮮明に動作する場合があります。
    Copilot チャット上部の ![New Chat Button on GitHub Copilot](./media/copilot-newchat.png)
    をクリックしてください。
<!-- markdownlint-enable MD046 -->

複雑度が上がるため **Agent Mode** で進めます。切り替えたら、C# プロジェクトのスキャフォールディング作成を
Copilot に依頼し、開始手順とコマンドも聞きましょう。

<!-- markdownlint-disable MD046 -->
??? question "Tip"
    Prompt *(Agent Mode)*

    ```text
    Create a new folder named `csharp-app` in the `src` directory.
    Create the C# scaffolding in csharp-app folder, where we are going to
    migrate the python project.
    Use .NET Minimal APIs.
    Don't perform any code migration for now.
    Provide me with guided steps to run the project afterwards.
    Create the minimal code necessary to have a running C# .NET 10 Web API
    project.
    ```
<!-- markdownlint-enable MD046 -->

Copilot がスキャフォールディングを作成したら、`csharp-app` フォルダー内を確認します。
`.csproj` と `Program.cs` があるはずです。

（任意）作成ファイルの目的や内容について、Copilot に質問してください。
