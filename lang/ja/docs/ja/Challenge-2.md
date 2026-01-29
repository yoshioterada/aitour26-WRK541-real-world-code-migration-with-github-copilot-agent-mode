# ボーナスチャレンジ

## チャレンジ 2: Entity Framework Core による DB 統合

**難易度:** 🔥🔥 上級

!!! info
    静的な JSON データソースを実データベースに置き換えて、さらに踏み込みましょう。

このチャレンジでは、C# の天気 API で JSON ファイルを SQL Server または
SQLite + Entity Framework Core (EF Core) に置き換えます。
データ永続化、マイグレーション、非同期 DB 操作の実践的シナリオです。

### 学習目標

- ASP.NET Core Minimal API への EF Core 統合を理解
- データモデルと DbContext を定義し DB 操作を管理
- DB マイグレーションとスキーマ管理を学ぶ
- 非同期クエリの async/await パターンを実装
- DI を使ったリポジトリパターンを適用

#### チャレンジ手順

##### Step 1: EF Core セットアップ

Agent Mode で:

1. NuGet パッケージを追加（例: `Microsoft.EntityFrameworkCore`,
   `Microsoft.EntityFrameworkCore.Sqlite` または `Microsoft.EntityFrameworkCore.SqlServer`）
2. `weather.json` 構造を基に Country/Weather/City エンティティを作成
3. `DbContext` を継承した `WeatherDbContext` を作成しテーブルを定義

!!! tip
    Copilot に `weather.json` を分析させ、適切なエンティティとリレーションを提案させましょう。

##### Step 2: DB 設定 & マイグレーション作成

Agent Mode で:

1. `Program.cs` に DB 接続を設定
2. `dotnet ef migrations add` で初回マイグレーションを作成
3. `dotnet ef database update` でスキーマを更新

!!! important
    Copilot が `Program.cs` やマイグレーションファイルを変更する際は差分を確認し、適用されるスキーマを理解しましょう。

##### Step 3: 初期データ投入

Agent Mode で:

1. `weather.json` から DB に初期データを投入する仕組みを実装
2. アプリ起動時にシーディングを呼び出す

!!! note
    既存 JSON からシードすることで、元の静的データソースと同じ情報を DB に持たせられます。

##### Step 4: エンドポイントを DB 利用に更新

Agent Mode で:

1. エンドポイントハンドラに `WeatherDbContext` を DI する
2. JSON ファイル読み込みを EF Core クエリに置き換える
3. すべての DB 操作を async/await 化
4. 既存と同じレスポンスになることを保証

!!! success
    更新後、Python テストを実行し、DB バックエンドでも API が正しく動作するか確認しましょう。

##### Step 5: 検証 & テスト

Python テストスイートで以下を確認:

1. `/` エンドポイントが 200 を返す
2. `/countries` が正しい国一覧を返す
3. 指定国の weather エンドポイントが正しいデータを返す
4. 無効な国は 404 を返す

```bash
cd src/python-app/webapp
pytest test_main.py -v
```

### オプション拡張

- 国一覧エンドポイントにフィルタ・ページングを追加
- リレーションを含むよりリッチなデータモデルを実装
- DbContext をモックした xUnit テストを追加
- インデックス最適化などでクエリ性能を改善
