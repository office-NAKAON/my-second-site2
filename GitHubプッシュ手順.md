# GitHubプッシュ手順

## 概要
中尾先生のポートフォリオサイト（`index.html`、`README.md`）をGitHubリポジトリにプッシュする手順です。

## リポジトリ情報
- **リポジトリURL**: https://github.com/office-NAKAON/my-second-site

## 作成済みファイル
- `index.html` - ポートフォリオサイト（中尾和博先生の自己紹介）
- `README.md` - プロジェクト説明

## プッシュ方法

### 方法1: Gitコマンドラインを使用（推奨）

#### 1. Git for Windowsのインストール
- ダウンロード: https://git-scm.com/download/win
- インストール後、PowerShellまたはコマンドプロンプトを再起動

#### 2. コマンドの実行
プロジェクトディレクトリで以下のコマンドを順番に実行してください：

```bash
# プロジェクトディレクトリに移動
cd "C:\Users\〇〇中学校\Desktop\Day1-2"

# Gitリポジトリの初期化
git init

# ファイルをステージング
git add index.html README.md

# コミット
git commit -m "Initial commit: ポートフォリオサイトの作成"

# リモートリポジトリの追加
git remote add origin https://github.com/office-NAKAON/my-second-site.git

# ブランチ名をmainに設定（必要に応じて）
git branch -M main

# プッシュ
git push -u origin main
```

**注意**: 初回プッシュ時は、GitHubの認証情報（ユーザー名とパスワード、またはPersonal Access Token）の入力が求められます。

### 方法2: GitHub Desktopを使用

#### 1. GitHub Desktopのインストール
- ダウンロード: https://desktop.github.com/
- インストール後、GitHubアカウントでログイン

#### 2. リポジトリの追加と公開
1. GitHub Desktopを起動
2. **File** → **Add Local Repository** を選択
3. プロジェクトディレクトリ `C:\Users\〇〇中学校\Desktop\Day1-2` を選択
4. **Publish repository**（リポジトリを公開）をクリック
5. リモートURL: `https://github.com/office-NAKAON/my-second-site.git` を指定
6. **Publish repository** をクリック

## トラブルシューティング

### Gitコマンドが見つからない場合
- Git for Windowsがインストールされているか確認
- インストール後、PowerShell/コマンドプロンプトを再起動
- 環境変数PATHにGitが含まれているか確認

### 認証エラーが発生する場合
- GitHubのユーザー名とパスワードを確認
- Personal Access Tokenを使用する場合は、適切な権限（repo）が設定されているか確認
- 2要素認証（2FA）が有効な場合は、Personal Access Tokenの使用を推奨

### パスのエンコーディング問題
- パスに日本語が含まれている場合、エンコーディングの問題が発生する可能性があります
- その場合は、Git Bashを使用するか、パスを短縮名（8.3形式）で指定することを検討してください

## 参考情報
- Git公式ドキュメント: https://git-scm.com/doc
- GitHub公式ドキュメント: https://docs.github.com/ja
