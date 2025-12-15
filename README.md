# 価値観診断 AI要約テスト

9つの価値観マトリクスの診断結果から、AIによる総合的なプロファイルを生成するテストサイトです。

## 機能

- 9つの価値観マトリクスから診断タイプを選択
- AI による総合プロファイル生成
- サンプル入力（リーダー型 / サポート型）
- ランダム入力

## セットアップ

### 1. 依存パッケージのインストール

```bash
pip install -r requirements.txt
```

### 2. APIキーの設定

`server.py` の以下の部分を編集：

```python
API_KEY = os.environ.get('ANTHROPIC_API_KEY', 'ここにAPIキーを入力')
```

または環境変数で設定：

```bash
# Mac/Linux
export ANTHROPIC_API_KEY="sk-ant-api03-xxxxxxxx"

# Windows
set ANTHROPIC_API_KEY=sk-ant-api03-xxxxxxxx
```

### 3. サーバー起動

```bash
python server.py
```

### 4. ブラウザでアクセス

http://localhost:5000

## ファイル構成

```
values-diagnosis-test/
├── index.html        # フロントエンド
├── server.py         # バックエンドAPI
├── requirements.txt  # 依存パッケージ
└── README.md         # このファイル
```

## 価値観マトリクス

| # | マトリクス名 | タイプ数 |
|---|------------|---------|
| 1 | 向き合い方と関わり方 | 9 |
| 2 | 発想と進め方 | 9 |
| 3 | 見せ方と中身 | 9 |
| 4 | 自立と協働 | 9 |
| 5 | 組織との関わり方 | 9 |
| 6 | スピードと裁量 | 9 |
| 7 | 判断の軸と視点 | 9 |
| 8 | 目的と見返り | 9 |
| 9 | 表現と伝え方 | 9 |

## API仕様

### POST /api/generate

診断結果からプロファイルを生成

**リクエスト:**
```json
{
  "diagnosis": [
    { "matrix": "向き合い方と関わり方", "type": "先導型チャレンジャー" },
    { "matrix": "発想と進め方", "type": "自由奔放クリエイター" },
    ...
  ]
}
```

**レスポンス:**
```json
{
  "profile": "あなたは変化を恐れず先頭に立って..."
}
```

## 本番環境へのデプロイ

本番環境では以下の点に注意してください：

- APIキーは環境変数で管理する
- 適切なレート制限を設ける
- HTTPS を使用する

## ライセンス

MIT License
