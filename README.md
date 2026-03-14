# Azure Static Web Apps で HTMLを全体公開するデモ

## 🔓 このサイトは誰でもアクセスできます

このリポジトリのHTMLファイルは、Azure Static Web Apps にデプロイされ、**認証なし・全世界に公開**されています。

🔗 **サイトURL：** https://mango-tree-0ee71ed10.6.azurestaticapps.net

---

## 🔐 認証をかけたバージョンもあります

同じHTMLファイルに **設定ファイルを1つ追加する**だけで、Entra ID による認証付きにできます。

| | このリポジトリ（認証なし） | [認証ありバージョン](https://github.com/FukudaRikako/azure-entra-auth-demo) |
|---|---|---|
| **サイト** | [🔓 認証なし](https://mango-tree-0ee71ed10.6.azurestaticapps.net) | [🔐 認証あり](https://gentle-pebble-053949610.1.azurestaticapps.net) |
| **アクセス** | 誰でも見れる | Entra ID ログインが必要 |
| **ファイル構成** | `index.html` のみ | `index.html` + `staticwebapp.config.json` |

> **HTMLファイルは完全に同じ。** 違いは `staticwebapp.config.json` が **あるかないか** だけ！

---

## 📁 ファイル構成

```
azure-no-auth-demo/
├── index.html       ← 公開するHTMLファイル
└── og-image.png     ← OGP画像
```

認証をかけたい場合は、ここに `staticwebapp.config.json` を追加するだけです。
詳しい手順は [認証ありバージョンのREADME](https://github.com/FukudaRikako/azure-entra-auth-demo) をご覧ください。

---

## 📖 このサイトを作った手順（Step by Step）

### Step 1 ― GitHubにリポジトリを作る

1. https://github.com にログイン
2. https://github.com/new を開く
3. 「Repository name」に名前を入力（例：`azure-no-auth-demo`）
4. 「**Public**」を選択
5. 「**Create repository**」をクリック

### Step 2 ― HTMLファイルをアップロードする

1. リポジトリのページで「**uploading an existing file**」をクリック
2. HTMLファイルをドラッグ＆ドロップ
   - ⚠️ ファイル名は **`index.html`** にしてください
3. 「**Commit changes**」をクリック

### Step 3 ― Azure PortalでStatic Web Appを作る

1. https://portal.azure.com にサインイン
2. 検索バーに「**Static Web Apps**」と入力して選択
3. 「**＋ 作成**」をクリック
4. 以下を入力：
   - **サブスクリプション**：使用するものを選択
   - **リソースグループ**：「新規作成」→ 好きな名前
   - **名前**：好きな名前
   - **プランの種類**：Free
   - **ソース**：GitHub
5. 「**GitHubでサインイン**」→ 認証
6. 以下を選択：
   - **組織**：自分のGitHubユーザー名
   - **リポジトリ**：Step 1 で作ったリポジトリ
   - **分岐**：main
7. ビルドの詳細：
   - **ビルドのプリセット**：Custom
   - **アプリの場所**：`/`
8. 「**確認および作成**」→「**作成**」

### Step 4 ― 完成！

数分待つと自動デプロイが完了します。Azure Portal の Static Web App リソースページに表示される **URL** をクリックすると、サイトが見れます🎉

> ✅ 認証なしなので、URLを知っている人なら誰でもアクセスできます。
>
> 🔐 アクセス制限をかけたい場合は → [認証ありバージョンの手順](https://github.com/FukudaRikako/azure-entra-auth-demo) を参照
