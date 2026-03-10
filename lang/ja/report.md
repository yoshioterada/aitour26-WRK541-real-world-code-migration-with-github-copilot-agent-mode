# プロジェクト解析レポート

## 1. 全体概要

本リポジトリは、GitHub Copilot Agent Mode を用いて Python の API を
C# (.NET Minimal APIs) へ移行するワークショップ教材です。
ドキュメントは MkDocs で構築され、英語と日本語の手順が併存して
います。サンプルアプリとして FastAPI の API と、移行先の .NET
Minimal API 実装が含まれています。

関連ファイル:

- ルート README: [README.md](README.md)
- MkDocs 設定 (ルート): [mkdocs.yml](mkdocs.yml)
- ドキュメント README: [docs/README.md](docs/README.md)
- ドキュメント README (日本語): [docs/README-ja.md](docs/README-ja.md)
- MkDocs 設定 (docs): [docs/mkdocs.yml](docs/mkdocs.yml)

## 2. リポジトリ構成の要点

- docs/ に MkDocs サイトのソースがあり、英語と日本語の手順ページが
  並列で存在します。
- src/ にワークショップ用のコードが集約されています。
  - Python 版 API: [src/python-app](src/python-app)
  - C# 版 API (完成例): [src/csharp-app-complete](src/csharp-app-complete)

関連ファイル:

- ソース概要: [src/readme.md](src/readme.md)

## 3. ドキュメントシステム (MkDocs)

- ルートの [mkdocs.yml](mkdocs.yml) は i18n プラグインを使って
  言語切り替えを行います。
- docs/ 配下の [docs/mkdocs.yml](docs/mkdocs.yml) は英語ドキュメント
  専用の構成です。
- Material for MkDocs と glightbox などの拡張を使用しています。

特徴:

- 手順は GitHub Pages で公開する前提。
- ナビゲーションに Workshop の各ステップが定義済み。

## 4. Python アプリ (FastAPI)

### 4.1 機能とエンドポイント

FastAPI で公開される API は次の 3 つです。

- `/` : `/docs` へリダイレクト
- `/countries` : すべての国名を返却
- `/countries/{country}/{city}/{month}` : 月別の最高/最低気温を返却

実装ファイル:

- API 実装: [src/python-app/webapp/main.py](src/python-app/webapp/main.py)

### 4.2 データ

- `weather.json` を起動時に読み込んでメモリに保持します。
- JSON 構造は `国 -> 都市 -> 月 -> {high, low}` です。

データファイル:

- [src/python-app/webapp/weather.json](src/python-app/webapp/weather.json)

### 4.3 テスト

- `pytest` で API の疎通とレスポンスを確認します。
- BASE_URL は環境変数で指定可能で、未指定の場合は
  `http://localhost:8000`。
- アプリが起動していない場合は全テストをスキップします。

テストファイル:

- [src/python-app/webapp/test_main.py](src/python-app/webapp/test_main.py)

### 4.4 依存関係

主要依存:

- FastAPI / Uvicorn / Requests / Pytest

依存定義:

- [src/python-app/requirements.txt](src/python-app/requirements.txt)

## 5. C# アプリ (ASP.NET Core Minimal API)

### 5.1 概要

C# 版は Minimal API で実装され、Swagger UI を標準で提供します。
Python 版と同等の API を提供し、データは同じ `weather.json` を
利用します。

実装ファイル:

- API エントリ: [src/csharp-app-complete/Program.cs](src/csharp-app-complete/Program.cs)
- Program 公開 (テスト用):
  [src/csharp-app-complete/ProgramEntry.cs](src/csharp-app-complete/ProgramEntry.cs)

### 5.2 エンドポイント

- `/` : `/swagger` へリダイレクト
- `/countries` : 国名一覧
- `/countries/{country}/{city}/{month}` : 月別の最高/最低気温

### 5.3 サービス層

- `IWeatherService` が抽象化を提供。
- `WeatherService` は `weather.json` を読み込み、辞書で保持。
- `TryGetMonthlyAverage` は `country/city/month` が存在すれば
  `TemperatureDto` を返します。

実装ファイル:

- [src/csharp-app-complete/Services/IWeatherService.cs](src/csharp-app-complete/Services/IWeatherService.cs)
- [src/csharp-app-complete/Services/WeatherService.cs](src/csharp-app-complete/Services/WeatherService.cs)
- [src/csharp-app-complete/Models/TemperatureDto.cs](src/csharp-app-complete/Models/TemperatureDto.cs)

### 5.4 データ

- `weather.json` はビルド出力へコピーされる設定。

データファイル:

- [src/csharp-app-complete/weather.json](src/csharp-app-complete/weather.json)

### 5.5 テスト

- MSTest で `WeatherService` の振る舞いを検証。
- 期待値として `England/London/January` の温度を固定値で確認。

テストファイル:

- [src/csharp-app-complete/WeatherService.UnitTests/WeatherServiceTests.cs](src/csharp-app-complete/WeatherService.UnitTests/WeatherServiceTests.cs)

### 5.6 プロジェクト設定

- ターゲットフレームワークは `net8.0`。
- Swashbuckle と OpenAPI を参照。
- `weather.json` を出力へコピーする設定あり。

プロジェクトファイル:

- [src/csharp-app-complete/csharp-app.csproj](src/csharp-app-complete/csharp-app.csproj)
- [src/csharp-app-complete/WeatherService.UnitTests/WeatherService.UnitTests.csproj](src/csharp-app-complete/WeatherService.UnitTests/WeatherService.UnitTests.csproj)

## 6. 仕様上の注意点と観察

- Python 版は `/docs` を自動表示するため、ルートは 301 リダイレクト。
- C# 版は `/swagger` を採用しており、Python 版とのドキュメント URL
  が異なります。
- Python の `test_main.py` には `/weather/InvalidCountry` のテストが
  含まれていますが、API 定義には存在しないため 404 を期待する
  テストとして機能しています。
- README では .NET 10 を前提に記載がありますが、C# プロジェクト設定は
  `net8.0` です。移行演習の過程で変更される前提の可能性があります。

## 7. 解析まとめ

- ワークショップの中心は「Python FastAPI の小さな API を C# Minimal
  API に移植する」こと。
- Python と C# の両方に同一 JSON データが含まれており、仕様の比較が
  容易。
- ドキュメントは MkDocs で整備され、多言語で演習手順を追える構成。
- C# 側は完成例として、Swagger と MSTest を含む実践的な構成に
  なっています。
