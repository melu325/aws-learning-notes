# Gitの使い方ガイド
---

## Gitとは

**Git** は、ファイルの変更履歴を管理するツール

## インストール

### Windows

1. [https://git-scm.com/](https://git-scm.com/) からダウンロード
2. インストーラーを実行（設定はすべてデフォルトでOK）
3. 「Git Bash」というアプリが使えるようになる

「インストールしますか？」と聞かれたら「はい」を選ぶ。

### 確認

インストール後、以下コマンドでバージョンが表示されればOK：

```
git --version
```

---

## 最初の設定（一度だけやればOK）

自分の名前とメールアドレスを登録します（GitHubを使うならGitHubのアカウントと同じものを推奨）。

```
git config --global user.name "あなたの名前"
git config --global user.email "your@email.com"
```

確認方法：

```
git config --list
```

---

## Gitの基本的な流れ

```
作業フォルダ（ワーキングツリー）
    ↓  git add
ステージング（次のコミットに含めるもの）
    ↓  git commit
リポジトリ（変更履歴の保存場所）
```

### 覚えるのはたったこれだけ

| コマンド | 何をするか |
|----------|------------|
| `git init` | フォルダをGit管理下に置く |
| `git add` | 変更をステージングに追加する |
| `git commit` | 変更を記録（セーブ）する |
| `git status` | 今の状態を確認する |
| `git log` | 変更履歴を見る |

---

## 実際にやってみよう

### ステップ1：フォルダを作ってGitを始める

```
mkdir my-project        # フォルダを作る
cd my-project           # フォルダに移動
git init                # Git管理を開始
```

`Initialized empty Git repository` と表示されればOK。

---

### ステップ2：ファイルを作る