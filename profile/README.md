# AI社員システム 司令塔

> **管理者**がゼロ少佐たちに指示を出す組織です。

## 指示の出し方

```
GitHub Issues に type:project または role:xxx ラベルを付けて作成するだけ
```

## 組織図

```mermaid
graph TD
    User("👤 管理者")

    subgraph GitHub["🏢 bft-regional-nk/00_claudecode"]
        Boss["⚔️ ザ・ボス<br/>インシデント検知<br/><i>毎時自動監視</i>"]
        PM["🎯 ゼロ少佐<br/>PMエージェント<br/><i>type:project を分解</i>"]
        Dev["🔫 ネイキッドスネーク<br/>開発エンジニア<br/><i>role:dev</i>"]
        DevOps["🔧 オセロット<br/>DevOps<br/><i>role:devops</i>"]
        Docs["🕵️ EVA<br/>ドキュメント<br/><i>role:docs</i>"]
        QA["💊 パラメディック<br/>QA・レビュー<br/><i>role:qa</i>"]
        Sigint["📡 シギント<br/>MCP管理<br/><i>role:mcp</i>"]
    end

    User -->|"type:project Issue 作成"| PM
    User -->|"role:mcp Issue 作成"| Sigint

    PM -->|"タスク分解"| Dev
    PM -->|"タスク分解"| DevOps
    PM -->|"タスク分解"| Docs
    PM -->|"タスク分解"| QA

    Dev -->|"PR作成→レビュー依頼"| QA
    Docs -->|"PR作成→レビュー依頼"| QA
    QA -->|"承認→自動マージ"| GitHub

    Boss -->|"異常検知→報告"| PM
    PM -->|"対応指示"| Boss
```

## エージェント一覧

| キャラ | 役割 | 起動条件 |
|---|---|---|
| ⚔️ **ザ・ボス** | インシデント検知・ゼロ少佐へ報告 | 毎時自動（schedule） |
| 🎯 **ゼロ少佐** | プロジェクト分解・指揮 | `type:project` |
| 🔫 **ネイキッドスネーク** | コード実装 | `role:dev` |
| 🔧 **オセロット** | インフラ・DevOps | `role:devops` |
| 🕵️ **EVA** | ドキュメント生成 | `role:docs` |
| 💊 **パラメディック** | QA・テスト・レビュー | `role:qa` |
| 📡 **シギント** | MCPサーバー管理 | `role:mcp` |

## リポジトリ

| リポジトリ | 用途 |
|---|---|
| [00_claudecode](https://github.com/bft-regional-nk/00_claudecode) | AI社員システム司令塔 |
| [00_powerautomate_hub](https://github.com/bft-regional-nk/00_powerautomate_hub) | Power Automate管理 |
