---
description: 新しいClaude Codeプラグインの雛形を生成する
---

# Create Plugin Skill

ユーザーが `/create-plugin <plugin-name>` コマンドを実行した際、以下の手順でプラグイン雛形を生成してください。

## 📋 手順

### Step 1: 引数の取得

ユーザーからプラグイン名を取得してください。

- 引数が提供されている場合: その名前を使用
- 引数がない場合: `my-awesome-plugin` をデフォルト名として使用

### Step 2: ディレクトリ作成

プラグイン名のディレクトリを現在の作業ディレクトリに作成してください。

```bash
mkdir <plugin-name>
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
claude --plugin-dir ./<plugin-name>
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
4. claude --plugin-dir ./<plugin-name> でテスト

💡 ヒント:
- commands/ディレクトリに .md ファイルを追加するだけで新しいコマンドが作成できます
- ファイル名がコマンド名になります（例: goodbye.md → /<plugin-name>:goodbye）
```

---

## ⚠️ 注意事項

- プラグイン名は英数字とハイフンのみ使用してください
- 既存のディレクトリがある場合は上書きせずに警告してください
- ファイル生成時にエラーが発生した場合は、適切にエラーメッセージを表示してください
