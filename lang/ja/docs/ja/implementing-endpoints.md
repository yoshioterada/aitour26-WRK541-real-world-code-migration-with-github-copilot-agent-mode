<!-- markdownlint-disable MD046 -->
# エンドポイント実装

スキャフォールディングができたら、まず単一のエンドポイントを作りましょう。
`Program.cs` に最初のエンドポイントを追加する初稿を Copilot に提案させます。
**ファイル全体ではなく `/` エンドポイントのみ**を生成するよう Copilot に伝えてください。

## 6. 単一エンドポイントを作成

- `Program.cs` を開き、Copilot に `/` エンドポイントのみ生成させる

!!! important
    進めるごとに部分的に検証できるよう、ファイル全体を生成させないこと。小さな単位で検証する方が容易です。

??? question "Tip"
    Prompt *(Agent Mode)*

    ```text
    #file:Program.cs add the root of the API only.
    This is the '/' endpoint, do not generate other endpoints yet,
    focus only on the single root endpoint for now.
    ```

最小コード例:

```csharp
var builder = WebApplication.CreateBuilder(args);

var app = builder.Build();

if (app.Environment.IsDevelopment())
{
    app.UseDeveloperExceptionPage();
}

app.MapGet("/", () =>
    Results.Ok(new { message = "Welcome to the C# minimal API root." }))
   .WithName("Root");

app.Run();
```

### 7. 最初の C# エンドポイントを検証

C# の最初のエンドポイントを検証しましょう。新言語移行ではコード生成と検証を反復するのが重要です。

- Python プロジェクトが停止していることを確認
- Copilot に Python と同じアドレス/ポートで C# を起動する方法を尋ねる
- Python テストを実行し、失敗があれば修正

2 つのターミナルを使用:

- 1つ目: C# アプリを実行

```bash
cd src/csharp-app
dotnet run --urls "http://localhost:8000"
```

- 2つ目: Python テストを実行

```bash
cd src/python-app/webapp
pytest test_main.py -v
```

??? question "Tip"
    Prompt *(Agent Mode)*

    ```text
    Please stop any process on port `8000`, then start the C# minimal API in
    `src\csharp-app` with `ASPNETCORE_URLS=http://0.0.0.0:8000`.
    Do not change any C# code.
    Start the C# app in the foreground in one terminal and open a second
    terminal to run
    the Python tests so they can execute while the app is running.
    In the second terminal, run the Python tests from `src/python-app/webapp/test_main.py`
    using pytest. Only verify the `/` endpoint for now and report the test output.
    Use the workspace root and a shell.
    ```

### 8. 残りのエンドポイントを実装

Agent Mode または Plan Mode で、他のエンドポイントを追加し、Swagger 注釈も付けます。

#### 8.1 Agent Mode で続行

同じ流れでエンドポイントを1つずつ作成し、検証します。Python テストで互換性を確認してください。

!!! important
    Copilot の操作要求に注意:

    - ファイル編集（Program.cs, weather.json など）
    - ターミナルコマンド実行
    - ファイル/ディレクトリ作成
    - 依存パッケージインストール

    提案内容を確認し、必要に応じて承認してください。

!!! tip
    次のエンドポイント（例: `/countries`）実装時は、Python と同じ `weather.json` のデータを使うよう指示しましょう。

JSON のデシリアライズが必要です。手順が不明なら Copilot に相談し、**最小コード**で実装・即検証してください。

!!! success "小さく検証すると楽"  小さな部分を検証・デバッグする方が簡単です。Copilot 利用時の良い習慣です。

#### 8.2 Plan Mode を活用

> *このステップは Plan Mode も試せます。*

次のエンドポイント実装時、**Plan Mode** で手順を分解してもらいましょう。

??? question "Tip"
    Prompt *(Plan Mode)*

    Analyze the other endpoints in the #file:main.py and implement this in the
    #file:Program.cs file using .NET Minimal APIs.
    Implement the swagger annotations for each endpoint.
    The root of the API should redirect to the swagger UI page.

Plan 完了後、**Agent Mode** に切り替え、計画に沿ってステップごとに実装を依頼します。

!!! important
    Copilot 実行時の要求に注意:

    - ファイル変更（Program.cs, モデル追加など）
    - コマンド実行（dotnet コマンド、テストなど）
    - ファイル作成（新クラス、設定ファイル）
    - パッケージインストール

    提案内容を確認して承認し、早めに問題を検出しましょう。
