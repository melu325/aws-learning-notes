# Stage 1 ハンズオン#1 学習ノート — EC2入門

## 📅 学習日
2025-06-14

## ✅ やったこと
- AWS CLIのインストール（apt不可→公式バイナリで解決）
- IAMユーザーの作成・アクセスキーの設定
- キーペア（HirakeGoma.pem）の作成
- CDKでEC2インスタンスをデプロイ
- SSHでEC2に接続してコマンドを実行
- cdk destroyでリソースを削除

## 📖 学んだこと

### クラウドの種類
- IaaS / PaaS / FaaS / SaaSの違い
- EC2はサーバー側の仮想マシン（クライアントではない）

### IAM
- ユーザー・グループ・ロール・ポリシーの役割
- 最小権限の原則
- アクセスキーはコードに書かない

### EC2
- インスタンスタイプの読み方（t2.micro = 汎用・最小・無料枠）
- AMI = OSのテンプレート
- stopped状態でもEBSの課金は続く

### VPC / Security Group
- EC2はVPCの中に配置する
- Security GroupでポートごとにIN/OUTを制御
- SSH接続にはポート22を開ける必要がある

### CDK
- app.pyにインフラの設計図を書く
- cdk deploy でAWSにリソースが作られる
- cdk destroy で全リソースを一括削除できる

## 🚨 苦戦したこと・解決策

### apt install awscliが失敗した
- 原因：Ubuntu24.04のaptリポジトリにAWS CLI v2がない
- 解決：公式サイトからバイナリを直接インストール

### git cloneのURLにが混入していた
- 原因：コピペ時にURLの末尾に]が混入
- 解決：URLを正確にコピーし直した

### handson/01-ec2が存在しなかった
- 原因：フォルダ名が実際はec2-get-startedだった
- 解決：lsで中身を確認してから移動

### キーペアエラー
- 原因：AWSコンソールでキーペアをまだ作っていなかった
- 解決：EC2コンソール→キーペアからHirakeGomaを作成

### Free Tierエラー
- 原因：アカウントの無料枠でt2.microが使えなかった
- 解決：describe-instance-typesで確認しt3.microに変更

## 💪 できるようになったこと
- AWS CLIのセットアップ
- IAMユーザーの作成とアクセスキーの設定
- CDKを使ってEC2をコードでデプロイ
- SSHでリモートサーバーに接続して操作
- クラウドリソースの後片付け（cdk destroy）

## 📌 コマンドメモ
```bash
# AWS CLIインストール
curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
unzip awscliv2.zip && sudo ./aws/install

# 認証確認
aws sts get-caller-identity

# CDKデプロイ
cdk deploy -c key_name="HirakeGoma"

# SSH接続
ssh -i ~/.ssh/HirakeGoma.pem ec2-user@<IP>

# 後片付け
cdk destroy
```

## 🔗 参考
- [コードで学ぶAWS入門](https://tomomano.github.io/learn-aws-by-coding/)
