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

## ❓ なぜGitHubを経由してAzureにアップロードするの？

「Azureに直接HTMLをアップロードすればいいのでは？」と思うかもしれません。
GitHubを間に挟むと、こんなメリットがあります：

### 📝 変更履歴が自動で残る

ファイルを変更するたびに **いつ・誰が・何を変えたか** がすべて記録されます。

- 「先週の変更が間違ってた…」→ **ワンクリックで前のバージョンに戻せる**
- 「3ヶ月前はどんな内容だったっけ？」→ **過去の任意の時点を確認できる**
- 「誰がこの変更をした？」→ **変更者と日時が全部わかる**

Word や PowerPoint の「元に戻す」と似ていますが、**ファイルを閉じても履歴がずっと残る** のが大きな違いです。

### 🔄 自動デプロイ

GitHubにファイルをアップロードするだけで、**Azureのサイトに自動で反映**されます。
手動でAzureにアップロードし直す必要がありません。

```
ファイルを変更 → GitHubにアップロード → 自動でAzureに反映（1〜2分）
```

### 👥 チームでの共同編集

- 複数人で同じファイルを編集しても、GitHubが**差分を自動検出**して衝突を防ぐ
- 「プルリクエスト」で変更内容を**公開前にレビュー**してもらえる

```
例）

Aさん：HTMLを修正 → GitHubにアップロード → 自動でAzureに反映
Bさん：「この変更いいね！」とレビュー承認
Cさん：「やっぱり前に戻して」→ ワンクリックで復元
```

> 💡 個人で使うだけ・ファイルが少ない場合は GitHub なしでもOKですが、
> チームで運用する場合や変更履歴を残したい場合は GitHub 経由がおすすめです。

---

## 🔒 GitHubでソースコードを非公開にしたい場合

今のリポジトリは **Public（公開）** なので、GitHub上で誰でもHTMLのソースコードが見れます。
ソースコードを見せたくない場合は、リポジトリを **Private（非公開）** に変更できます。

> ⚠️ **Privateにしても、Azureにデプロイされたサイト自体はそのまま公開されます。**
> 非公開になるのはGitHub上のソースコードだけです。

### 設定手順

1. GitHubのリポジトリページを開く
2. 上部の「**Settings**」タブをクリック
3. 一番下までスクロールして「**Danger Zone**」セクションを見つける
4. 「**Change repository visibility**」→「**Change visibility**」をクリック
5. 「**Make private**」を選択
6. リポジトリ名を入力して確認

### PublicとPrivateの違い

| | Public（今の状態） | Private |
|---|---|---|
| **GitHub上のソースコード** | 🌍 誰でも見れる | 🔒 自分（と招待した人）だけ |
| **Azureのサイト** | 🌍 誰でもアクセスできる | 🌍 誰でもアクセスできる（変わらない） |
| **自動デプロイ** | ✅ 動作する | ✅ 動作する |
| **料金** | 無料 | 無料（個人アカウントの場合） |

> 💡 **まとめ：** Private に変えても、Azureのサイトの公開状態には影響しません。
> 「ソースコードは見せたくないけど、サイトは公開したい」という場合に最適です。

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
