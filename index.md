# terrafrom tutorial

- document : https://learn.hashicorp.com/tutorials/terraform/install-cli?in=terraform/gcp-get-started

## terrafrom  とは

- Hashicorp によって公開されたOSS プロダクト
- インフラをコードで作成することができる(IaC)
  - コードをバージョン管理することで、変更履歴を追跡することが容易となる
- terrafrom のコードはHCLと呼ばれるHashicorpが設計した言語で実装する

## tutorial 実行環境

- ブラウザでの操作
- gcp
- gcp cloud shell

## 事前準備

### terraform のインストール

- 各ディストリビューションのパッケージマネージャーを利用すると手順がバラバラになるため、バイナリを取得してインストール。

```
curl -O https://releases.hashicorp.com/terraform/0.15.3/terrafrom_0.15.3_linux_amd64.zip
unzip terrafrom_0.15.3_linux_amd64.zip
mv terraform /usr/bin/terraform
```

### GCP credential ファイルの用意

- terraform での操作に必要な権限・サービスアカウントを用意
- サービスアカウントの作成はブラウザで実施
- 下記コマンドでcloud shell上にcredentialファイルをダウンロード

```
gcloud iam service-accounts keys create path_to_save/account.json \
--iam-account [service-account name]@[PROJECT_ID].iam.gserviceaccount.com
```

## terrafromコマンドについて

### terraform init

- [document](https://www.terraform.io/docs/cli/commands/init.html)
- terrafrom の初期に実施するコマンド
  - provider に指定したものに関してダウンロードとかをしている

### terraform plan

- [document](https://www.terraform.io/docs/cli/commands/plan.html)
- terrafrom の実行前に変更を確認できるコマンド(dry-run)

### terraform apply

- [document](https://www.terraform.io/docs/cli/commands/apply.html)
- terraform の設定反映

## terraform tutorial ディレクトリ構成

### terraform 実行前

```
[cloudshell ~/terraform-tutorial]$ tree
.
tqq account.json
mqq main.tf

0 directories, 2 files
[cloudshell ~/terraform-tutorial]$
```

### terraform 実行後

- terrafrom apply後、tfstateファイルが作成される(tfstateをローカルに保存した場合)

```
[cloudshell ~/terraform-tutorial]$ tree
.
tqq account.json
tqq main.tf
mqq terraform.tfstate

0 directories, 3 files
[cloudshell ~/terraform-tutorial]$
```

## 所感

- コードを使いまわす(変数利用)ことで、同じインフラ構築を簡単に作成することができる
- tutrorial 実施時点では、インフラの変更にはクセがあるため最初に設計・方針を決めておいたほうが良いと感じた


## 疑問や検討事項

### GCPのアカウントの保存先

- account.jsonをローカルに置いているが、別の管理方法はないのか？
  - 複数の担当者のローカルPC上にCredentialを置いて利用するような運用は避けたい

### tfstateの保存先

- tutorial ではローカル保存であるが、別の保存先について調査し選択肢を増やしておいたほうがよいと感じた
