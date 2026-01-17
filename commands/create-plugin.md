---
description: 新しいClaude Codeプラグインの雛形を生成する
argument-hint: <plugin-name> [--force]
allowed-tools: [Bash, Write, Edit, Read]
---

# Create Plugin

ユーザーが `/create-plugin <plugin-name> [--force]` コマンドを実行した際、以下の手順でプラグイン雛形を生成してください。

## 📋 手順

### Step 1: 引数の取得とバリデーション

ユーザーからプラグイン名とオプションを取得してください。

- 引数が提供されている場合: その名前を使用
- 引数がない場合: `my-awesome-plugin` をデフォルト名として使用
- `--force` オプション: 既存ディレクトリがあっても上書きを許可

#### プラグイン名のバリデーション

プラグイン名が以下のルールに従っているか確認してください：

```javascript
// バリデーションルール
const PLUGIN_NAME_REGEX = /^[a-z][a-z0-9-]{2,49}$/;

// ルール:
// - 先頭は英小文字で始める
// - 英小文字（a-z）、数字（0-9）、ハイフン（-）のみ使用可能
// - 3〜50文字以内
```

**無効な名前の場合:**
```
❌ 無効なプラグイン名です: '<plugin-name>'

ルール:
- 英小文字（a-z）のみ使用可能
- 数字（0-9）を使用可能
- ハイフン（-）を使用可能
- 先頭は文字で始める必要があります
- 3〜50文字以内

良い例: my-plugin, hello-world, tool-123
悪い例: MyPlugin, hello_world, 123plugin
```

### Step 2: ディレクトリ存在チェック

既存のディレクトリが存在するか確認してください。

- ディレクトリが存在しない場合: 作成を続行
- ディレクトリが存在する場合:
  - `--force` オプションがある場合: 既存ディレクトリを削除して再作成
  - `--force` オプションがない場合: 警告メッセージを表示して中断

```bash
# ディレクトリ存在チェック
if [ -d "<plugin-name>" ]; then
  if [ "$FORCE" = "true" ]; then
    rm -rf <plugin-name>
    mkdir <plugin-name>
  else
    echo "⚠️ ディレクトリ '<plugin-name>' は既に存在します。"
    echo "   --force オプションを使用すると上書きできます。"
    exit 1
  fi
else
  mkdir <plugin-name>
fi
```

### Step 3: 雛形ファイルの生成

以下のファイル構成を作成してください：

```
<plugin-name>/
├── .claude-plugin/
│   └── plugin.json
├── commands/
│   └── hello.md
├── README.md
└── .gitignore
```

#### 3.1. `plugin.json` の内容

```json
{
  "name": "<plugin-name>",
  "description": "<plugin-name> プラグイン",
  "version": "1.0.0",
  "author": {
    "name": "Your Name"
  }
}
```

#### 3.2. `hello.md` の内容

```markdown
---
description: ユーザーに友好的なメッセージで挨拶する
---
# Hello Command

ユーザーに温かく挨拶し、今日はどのような手助けができるか尋ねてください。
```

#### 3.3. `README.md` の内容

```markdown
# <plugin-name>

## 概要

<plugin-name> プラグインの説明。

## インストール

```bash
claude plugin install ./
```

## 使い方

### コマンド

- `/<plugin-name>:hello` - 挨拶メッセージを表示

## 開発

プラグインの開発方法や拡張方法をここに記述してください。
```

#### 3.4. `.gitignore` の内容

```
# Dependencies
node_modules/

# IDE
.vscode/
.idea/

# OS
.DS_Store
Thumbs.db

# Logs
*.log
npm-debug.log*
```

### Step 4: 完了報告

全てのファイルが生成されたら、以下の形式でユーザーに報告してください：

```
✅ プラグイン雛形が生成されました！

📁 ディレクトリ: <plugin-name>/

📋 生成されたファイル:
- .claude-plugin/plugin.json (マニフェスト)
- commands/hello.md (サンプルコマンド)
- README.md (ドキュメント)
- .gitignore (Git除外設定)

🚀 次のステップ:
1. cd <plugin-name>
2. plugin.json を編集してプラグイン情報をカスタマイズ
3. commands/ に新しいコマンドを追加
4. claude plugin install ./ でインストール

💡 ヒント:
- commands/ディレクトリに .md ファイルを追加するだけで新しいコマンドが作成できます
- ファイル名がコマンド名になります（例: goodbye.md → /<plugin-name>:goodbye）
```

---

## ⚠️ エラーハンドリング

以下のエラーが発生した場合、適切にエラーメッセージを表示してください：

### 1. ディレクトリ作成エラー

```
❌ ディレクトリの作成に失敗しました: <error_message>

原因:
- 権限が不足しています
- ディスク容量が不足しています
- パスが無効です

解決策:
- 書き込み権限を確認してください
- ディスク容量を確認してください
- プラグイン名に使用できない文字が含まれていませんか？
```

### 2. ファイル書き込みエラー

```
❌ ファイルの作成に失敗しました: <file_path>

原因:
- ディレクトリが存在しません
- 書き込み権限がありません

解決策:
- ディレクトリ構造を確認してください
- 権限を確認してください
```

### 3. 無効なプラグイン名

```
❌ 無効なプラグイン名です: '<plugin-name>'

ルール:
- 英小文字（a-z）のみ使用可能
- 数字（0-9）を使用可能
- ハイフン（-）を使用可能
- 先頭は文字で始める必要があります
- 3〜50文字以内

良い例: my-plugin, hello-world, tool-123
悪い例: MyPlugin, hello_world, 123plugin
```

## ⚠️ 注意事項

- プラグイン名は英数字とハイフンのみ使用してください
- 既存のディレクトリがある場合:
  - デフォルトでは警告を表示して中断します
  - `--force` オプションを使用すると既存ディレクトリを削除して上書きします
- ファイル生成時にエラーが発生した場合は、適切にエラーメッセージを表示してください

## 🔧 オプション

| オプション | 説明 |
|-----------|------|
| `--force` | 既存ディレクトリがあっても上書きして生成します |

### 使用例

```bash
# 通常の作成
/create-plugin my-plugin

# 既存ディレクトリを上書きして作成
/create-plugin my-plugin --force
```
