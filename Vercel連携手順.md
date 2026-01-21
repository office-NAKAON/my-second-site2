# Vercel連携手順

## 概要
GitHubリポジトリ（`https://github.com/office-NAKAON/my-second-site`）をVercelと連携して、自動デプロイを設定する手順です。

## 前提条件
- GitHubアカウントを持っていること
- GitHubリポジトリが公開されていること（またはVercelアカウントでアクセス権限があること）

## 連携手順

### 1. Vercelアカウントの作成・ログイン

1. **Vercelの公式サイトにアクセス**
   - URL: https://vercel.com
   - 「Sign Up」または「Log In」をクリック

2. **GitHubアカウントでログイン**
   - 「Continue with GitHub」を選択
   - GitHubの認証画面で「Authorize Vercel」をクリック
   - 必要に応じて、VercelがGitHubリポジトリにアクセスする権限を許可

### 2. プロジェクトのインポート

1. **ダッシュボードから新規プロジェクトを作成**
   - Vercelダッシュボードで「Add New...」→「Project」をクリック
   - または「Import Project」をクリック

2. **GitHubリポジトリを選択**
   - GitHubリポジトリの一覧から `office-NAKAON/my-second-site` を選択
   - 「Import」をクリック

### 3. プロジェクト設定

1. **プロジェクト名の確認**
   - プロジェクト名は自動的に設定されます（必要に応じて変更可能）
   - 例: `my-second-site`

2. **フレームワークプリセットの設定**
   - 「Framework Preset」で「Other」または「Other」を選択
   - このプロジェクトは静的HTMLサイトなので、特別なフレームワーク設定は不要です

3. **ルートディレクトリの設定**
   - 「Root Directory」は `.`（現在のディレクトリ）のままにします

4. **ビルドコマンドと出力ディレクトリ**
   - **Build Command**: 空欄のまま（または削除）
   - **Output Directory**: 空欄のまま（または削除）
   - 静的HTMLサイトなので、ビルドは不要です

5. **環境変数**
   - 今回は環境変数の設定は不要です

### 4. デプロイの実行

1. **「Deploy」ボタンをクリック**
   - 設定を確認して「Deploy」をクリック

2. **デプロイの完了を待つ**
   - 通常、1〜2分程度でデプロイが完了します
   - デプロイが完了すると、自動的にURLが生成されます
   - 例: `https://my-second-site.vercel.app`

### 5. デプロイ後の確認

1. **生成されたURLにアクセス**
   - デプロイ完了後、表示されるURLをクリック
   - ポートフォリオサイトが正しく表示されることを確認

2. **カスタムドメインの設定（オプション）**
   - プロジェクト設定から「Domains」を選択
   - 独自ドメインを設定することができます

## 自動デプロイの仕組み

VercelとGitHubを連携すると、以下の場合に自動的にデプロイが実行されます：

1. **GitHubへのプッシュ時**
   - `main`ブランチ（またはデフォルトブランチ）にプッシュすると自動デプロイ
   - プルリクエストを作成すると、プレビューURLが生成されます

2. **デプロイの確認**
   - Vercelダッシュボードの「Deployments」タブでデプロイ履歴を確認できます
   - 各デプロイのステータス（成功/失敗）を確認できます

## 今後の作業フロー

1. **ローカルでファイルを編集**
   ```bash
   # ファイルを編集
   # 例: index.html を編集
   ```

2. **GitHubにプッシュ**
   ```bash
   git add .
   git commit -m "変更内容の説明"
   git push origin main
   ```

3. **自動デプロイの確認**
   - Vercelが自動的に変更を検知してデプロイを開始
   - 数分後に新しいバージョンが公開されます

## トラブルシューティング

### 「No Results Found」エラーが表示される場合

このエラーは、VercelがGitHubリポジトリを見つけられないときに表示されます。以下の手順で解決できます：

#### 1. GitHubアカウントの連携を確認

1. **Vercelの設定を確認**
   - Vercelダッシュボード右上のプロフィールアイコンをクリック
   - 「Settings」→「Git」を選択
   - GitHubが連携されているか確認

2. **GitHub連携を再設定**
   - 「Connect Git Provider」または「Configure」をクリック
   - GitHubを選択して、再度認証を行う
   - **重要**: 「All repositories」または「Only select repositories」で適切な権限を付与

#### 2. リポジトリのアクセス権限を確認

1. **GitHubでリポジトリの設定を確認**
   - GitHubリポジトリ（`https://github.com/office-NAKAON/my-second-site`）にアクセス
   - 「Settings」→「Integrations」→「Installed GitHub Apps」を確認
   - Vercelがインストールされているか確認

2. **VercelアプリをGitHubにインストール**
   - Vercelダッシュボードの「Settings」→「Git」→「GitHub」を選択
   - 「Configure」をクリック
   - GitHubの認証画面で、`office-NAKAON/my-second-site` リポジトリへのアクセスを許可
   - または「All repositories」を選択してすべてのリポジトリへのアクセスを許可

#### 3. リポジトリ名の確認

1. **正確なリポジトリ名を確認**
   - GitHubでリポジトリのURLを確認
   - 形式: `https://github.com/[ユーザー名または組織名]/[リポジトリ名]`
   - この場合: `office-NAKAON/my-second-site`

2. **検索で見つからない場合**
   - Vercelのインポート画面で、リポジトリ名を直接検索
   - 大文字小文字を正確に入力
   - 組織名（`office-NAKAON`）が正しいか確認

#### 4. リポジトリの可視性を確認

1. **プライベートリポジトリの場合**
   - プライベートリポジトリは、Vercelの無料プランでも使用可能ですが、適切な権限設定が必要です
   - Vercelの設定で、該当リポジトリへのアクセス権限を付与してください

2. **公開リポジトリに変更する（オプション）**
   - GitHubリポジトリの「Settings」→「Danger Zone」→「Change visibility」
   - 「Make public」を選択（必要に応じて）

#### 5. 手動でリポジトリを追加する方法

もし上記の方法で解決しない場合：

1. **Vercel CLIを使用する方法**
   ```bash
   # Vercel CLIをインストール（未インストールの場合）
   npm i -g vercel
   
   # プロジェクトディレクトリで実行
   cd "C:\Users\〇〇中学校\Desktop\Day1-2"
   vercel
   ```
   - 対話形式で設定を進めます
   - GitHubリポジトリとの連携も設定できます

2. **GitHubから直接デプロイ**
   - Vercelダッシュボードで「Add New...」→「Project」
   - 「Import Git Repository」で、リポジトリURLを直接入力
   - `https://github.com/office-NAKAON/my-second-site` を入力

#### 6. 「The specified name is already used」エラーが表示される場合

このエラーは、Vercelで既に同じプロジェクト名が使用されている場合に表示されます。

**解決方法1: プロジェクト名を変更する（推奨）**

1. **プロジェクト設定画面で名前を変更**
   - 「Project Name」フィールドを編集
   - 新しい名前を入力（例: `my-second-site-2`, `nakao-portfolio`, `portfolio-site`）
   - 「Deploy」をクリック

2. **推奨される命名規則**
   - 小文字とハイフンのみ使用
   - 例: `nakao-portfolio`, `my-portfolio-site`, `nakao-sensei-portfolio`

**解決方法2: 既存のプロジェクトを確認・削除する**

1. **既存のプロジェクトを確認**
   - Vercelダッシュボードの「Projects」タブを確認
   - `my-second-site` という名前のプロジェクトがあるか確認

2. **既存プロジェクトを削除（必要に応じて）**
   - プロジェクトを選択
   - 「Settings」→「General」→ 最下部の「Delete Project」をクリック
   - 確認後、削除を実行

3. **削除後、再度インポート**
   - 上記の手順で再度プロジェクトをインポート

**解決方法3: 既存のプロジェクトを使用する**

既にプロジェクトが存在する場合、それをそのまま使用できます：

1. **既存プロジェクトを確認**
   - Vercelダッシュボードで `my-second-site` プロジェクトを開く
   - 「Settings」→「Git」で、正しいリポジトリが連携されているか確認

2. **リポジトリを変更する**
   - 「Settings」→「Git」→「Disconnect」をクリック
   - 再度「Connect Git Repository」をクリック
   - `office-NAKAON/my-second-site` を選択

#### 7. よくある原因と解決策

| 原因 | 解決策 |
|------|--------|
| GitHubアカウントが連携されていない | Vercel設定でGitHubを連携 |
| リポジトリへのアクセス権限がない | GitHubでVercelアプリに権限を付与 |
| リポジトリ名の入力ミス | 正確なリポジトリ名を確認 |
| 組織アカウントの権限問題 | 組織の設定でVercelアプリを承認 |
| プロジェクト名が既に使用されている | プロジェクト名を変更するか、既存プロジェクトを削除 |

### デプロイが失敗する場合

1. **ビルドログを確認**
   - Vercelダッシュボードの「Deployments」→失敗したデプロイをクリック
   - 「Build Logs」でエラー内容を確認

2. **よくある原因**
   - ファイルパスの問題（大文字小文字の違いなど）
   - 画像ファイルが見つからない
   - HTMLの構文エラー

### 画像が表示されない場合

1. **画像ファイルのパスを確認**
   - 画像ファイル（`profile.png`, `book.JPG`, `movie.jpg`, `AI.JPG`）がリポジトリに含まれているか確認
   - パスが正しいか確認（相対パスを使用）

2. **GitHubに画像をプッシュ**
   ```bash
   git add profile.png book.JPG movie.jpg AI.JPG
   git commit -m "画像ファイルを追加"
   git push origin main
   ```

## 参考情報

- Vercel公式ドキュメント: https://vercel.com/docs
- Vercel GitHub連携ガイド: https://vercel.com/docs/concepts/git
- Vercelダッシュボード: https://vercel.com/dashboard

## 注意事項

- Vercelの無料プランでも十分に使用できますが、使用量に制限があります
- カスタムドメインを設定する場合、DNS設定が必要です
- リポジトリがプライベートの場合、Vercelの有料プランが必要な場合があります
