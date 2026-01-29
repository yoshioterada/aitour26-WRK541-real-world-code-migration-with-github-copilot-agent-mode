# プロクター トラブルシューティング・プレイブック

ワークショップ中によく発生する技術的問題へのクイック対処集です。素早い解決で進行への影響を最小に抑えましょう。

## 🚨 クリティカル: 即対応が必要な問題

### Codespace が起動しない

**症状:**

- 「Starting...」のまま進まない
- 作成時エラー
- 起動後すぐ停止

**対応:**

1. **GitHub ステータス確認 (30秒):** [githubstatus.com](https://githubstatus.com)  
   影響有ならローカル手順へ切替
2. **ブラウザ変更 (1分):** 拡張機能干渉回避。シークレット/プライベートモード。Chrome/Edge 推奨
3. **削除して再作成 (2分):**

   ```text
   github.com/codespaces で該当を削除 → リポジトリ → Code → Codespaces → New
   ```

4. **ローカルに切替:** `PREREQUISITES.md` 参照。Python 3.12, .NET 10 SDK を確認

**予防:** 事前に Codespaces 作成をテスト。ローカル手順の準備。

---

### Copilot が動作しない

**症状:**

- Copilot アイコンがエラー
- 提案が出ない
- 「Copilot is not available」

**対応:**

1. **ステータス確認 (30秒):** ステータスバーのアイコンをクリック→詳細
2. **サブスクリプション確認 (1分):** [github.com/settings/copilot](https://github.com/settings/copilot)
3. **再認証 (2分):**

   ```text
   Ctrl+Shift+P → Sign out of GitHub → 10秒待つ → Sign in to GitHub
   ```

4. **VS Code リロード (30秒):** `Ctrl+Shift+P → Reload Window`
5. **拡張機能確認 (1分):** GitHub Copilot / Copilot Chat をインストール・更新

**ワークアラウンド:** Chat が動けば Chat だけでも完走可能。インラインがダメでも Chat で補完。

**予防:** 事前案内で Copilot 動作確認を促す。

---

### 大量のテスト失敗（複数参加者）

**原因と対応:**

1. **アプリ未起動 (最頻):**

   ```bash
   # Terminal1
   cd src/csharp-app
   dotnet run --urls "http://localhost:8000"
   
   # Terminal2
   cd src/python-app/webapp
   pytest test_main.py -v
   ```

1. **ポート違い:**

   ```bash
   dotnet run --urls "http://localhost:8000"  # 5000 ではなく 8000
   ```

1. **BASE_URL 未設定:**

   ```powershell
   $env:BASE_URL="http://localhost:8000"  # Windows
   ```

   ```bash
   export BASE_URL="http://localhost:8000"  # Linux/Mac
   ```

**アナウンス例:**

```text
アプリ起動していますか？ポートは 8000 ですか？
http://localhost:8000 にアクセスできるか確認してください。
```

---

### ネットワーク障害

**対応:**

1. **接続確認:**

   ```bash
   ping github.com
   curl https://api.github.com
   ```

1. **プロキシ/ファイアウォール:** 会場ITへ確認
1. **オフラインで進行:**
   - `src/csharp-app-complete` の完成コード参照
   - 印刷資料使用
   - 他参加者とペア

**予防:** 会場 WiFi 事前テスト。オフライン資料準備。ホットスポット検討。

---

## ⚠️ よくあるが致命的でない問題

### ポート 8000 が使用中

**Windows PowerShell:**

```powershell
Get-NetTCPConnection -LocalPort 8000
Stop-Process -Id <PID> -Force
```

**Linux/Mac:**

```bash
lsof -i :8000
kill -9 <PID>
```

**別ポート:**

```bash
dotnet run --urls "http://localhost:8001"
export BASE_URL="http://localhost:8001"
```

---

### Python 依存関係がない

**症状:** `ModuleNotFoundError: No module named 'fastapi'`

**対応:**

```bash
cd src/python-app/webapp
pip3 install -r ../requirements.txt
# または
cd src/python-app
pip3 install -r requirements.txt
```

**確認:**

```bash
pip3 list | grep fastapi  # fastapi==0.103.2
```

---

### .NET SDK が見つからない（ローカル）

**症状:** `dotnet: command not found` / SDK なし

**対応:**

```bash
dotnet --version  # 10.0.x
```

- 未インストール: <https://dotnet.microsoft.com/download/dotnet/10.0> からインストール
- パス問題: `export PATH="$PATH:/usr/share/dotnet"`

---

### JSON デシリアライズエラー

**原因:**

1. パス誤り:

   ```csharp
   var json = File.ReadAllText("weather.json");
   ```

   ※実行ディレクトリに注意。必要に応じてプロジェクトルートからのフルパスを使用

1. JSON とモデルの不一致

1. 文字コード:

   ```csharp
   File.ReadAllText("weather.json", Encoding.UTF8)
   ```

**対処:**

```csharp
if (weatherData == null)
{
    return Results.Problem("Failed to load weather data");
}
```

---

### Copilot Chat が表示されない

**症状:**

- チャットアイコンがない
- Copilot Chat パネルが開けない
- 拡張機能はインストール済みだが表示されない

**対応:**

1. **Chat パネルを開く:**

   ```text
   Ctrl+Alt+I (Win/Linux)
   Cmd+Shift+I (Mac)

   View → Command Palette → "GitHub Copilot: Open Chat"
   ```

2. **拡張機能を確認:**

   ```text
   拡張機能 → "GitHub Copilot Chat" を検索
   インストール済み・有効化を確認、なければインストール
   ```

3. **ウィンドウをリロード:**

   ```text
   Ctrl+Shift+P → "Reload Window"
   ```

---

### テストはローカルで通るが CI/CD で失敗する

このワークショップでは非対象ですが参考までに:

**よくある原因:**

- 環境差異
- CI のポート競合
- タイミング問題（アプリ起動前にテスト実行）

**ワークショップ文脈:**

- CI/CD は使用しません
- テストはローカルのみ
- 聞かれたら「今回の範囲外」と説明してください

---

## 🛠️ デバッグプロトコル（5分ルール）

1. **問題把握 (1分):** 何をしようとしたか、エラー内容、最後に動いた状態
2. **基本確認 (1分):** アプリ起動、ディレクトリ、保存、ポート
3. **エラーを読む (1分):** 行/ファイルを確認、必要ならググる
4. **仮説テスト (1分):** 小さい変更→すぐ検証
5. **継続 or エスカレーション (1分):** 改善中なら続行、ダメならリードへ、解決なら記録

**Copilot でデバッグを教える:**

```text
"このエラーが出ています: [エラー]
コードはこちら: [コード]
原因と修正方法を教えて"
```

---

## 📊 イシューの記録

```text
時刻 | イシュー | 人数 | 解決 | 時間
-----|----------|------|------|-----
9:15 | Port 8000 in use | 3 | kill | 2m
...
```

**使い道:** パターン検知（3人以上→アナウンス）、時間管理、資料改善

---

## 🎯 予防策

**開始1時間前チェック:**

- Codespace 作成テスト
- GitHub へアクセス
- 新規 Codespace で Copilot 動作確認
- 最初の 3 ステップを実行
- ドキュメントリンク確認
- 会場 WiFi テスト

**開始時アナウンス:**

```text
エラーはまずよく読む / テスト失敗はアプリ起動を確認 / Copilot アイコン確認 / 保存してから Copilot へ
困ったらすぐヘルプを
```

**チェックポイント後:**

```text
Python 起動・C# スキャフォールディング・最初のエンドポイントの進捗を挙手で確認
```

---

## 🚀 クイックコマンド

**プロセス確認:**

```bash
lsof -i :8000      # Mac/Linux
netstat -ano | findstr :8000  # Windows
ps aux | grep python
ps aux | grep dotnet
```

**プロセス終了:**

```bash
kill -9 <PID>      # Mac/Linux
Stop-Process -Id <PID> -Force  # PowerShell
```

**名前で終了（注意）:**

```bash
pkill python
pkill dotnet
```

**インストール確認:**

```bash
python3 --version
dotnet --version
git --version
code --version
```

**エンドポイントテスト:**

```bash
curl http://localhost:8000
curl http://localhost:8000/countries | jq
```

**Git:**

```bash
git status
git diff
git checkout -- <file>
git reset --hard HEAD
ls src/csharp-app-complete
```

---

## 📞 エスカレーション

**リードへ繋ぐタイミング:**

- 3人以上影響
- ブロッキング
- セキュリティ/アクセス問題
- 会場設備問題
- 10分以上同一問題

**先に進む提案:**

- Nice-to-have 領域なら後回しを提案
- 代替アプローチがある
- 完走に支障なし

**声かけ例:**

```text
後で戻れるので先に進みましょう。完走後にこの問題に戻りましょう。よろしいですか？
```

---

## 💡 プロクターTips

**初心者プロクター:**

- 即 fix ではなくデバッグを教える
- Copilot でエラー説明を依頼させる
- 冷静に、問題は学習機会
- イシューを記録
- 5分で区切る

**経験者プロクター:**

- パターンを先読み・3人以上で全体説明
- 進んでいる参加者にヘルプ依頼
- 資料改善点をフィードバック
- 他プロクターと情報共有

---

## サマリ

**頻出イシュー:**

1. テスト実行時にアプリ未起動
2. ポート設定ミス (8000以外)
3. Copilot サインイン問題
4. ポート 8000 使用中
5. 依存未インストール

**クイックフィックス:**

- 90% は「アプリ起動・ポート確認・リロード」で解決
- 困ったら**エラーを読む**
- Copilot にエラーを説明させる（デバッグ練習）

**覚えておくこと:**

- 問題は学びのチャンス
- 落ち着いて前向きに
- 新しいイシューは記録
- 情報共有で全体効率アップ
