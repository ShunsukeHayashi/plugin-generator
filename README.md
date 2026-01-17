# Plugin Generator

Claude Codeのプラグイン雛形を自動生成するツールです。

## 🚀 使い方

このプラグインをインストール後、以下のコマンドを実行してください：

```bash
/create-plugin my-awesome-plugin
```

自動的に以下の構成でプラグイン雛形が生成されます：

```
my-awesome-plugin/
├── .claude-plugin/
│   └── plugin.json       # プラグインマニフェスト
├── commands/
│   └── hello.md          # サンプルコマンド
├── README.md             # ドキュメント
└── .gitignore            # Git除外ファイル
```

## 📋 生成される内容

| ファイル | 説明 |
|---------|------|
| `plugin.json` | プラグインの名前、バージョン、説明などを定義 |
| `hello.md` | 「Hello World」を表示するサンプルコマンド |
| `README.md` | プラグインの説明書テンプレート |
| `.gitignore` | Node.js標準の除外設定 |

## 🔧 インストール方法

```bash
# プラグインディレクトリを指定してClaude Codeを起動
claude --plugin-dir /path/to/plugin-generator
```

## 📝 開発の流れ

1. `/create-plugin` コマンドで雛形作成
2. 生成された `commands/` ディレクトリにコマンド追加
3. `plugin.json` を編集してプラグイン情報を更新
4. `claude --plugin-dir ./your-plugin` でテスト

## 🎯 学習ポイント

- **プラグイン構造**: `.claude-plugin/` ディレクトリの役割
- **スラッシュコマンド**: Markdownベースのコマンド定義
- **MCPスキル**: `skills/` ディレクトリでの拡張機能

## 📄 ライセンス

MIT
