# terrafrom tutorial

- document : https://learn.hashicorp.com/tutorials/terraform/install-cli?in=terraform/gcp-get-started

## 実行環境など

- ブラウザでの操作
- gcp
- gcp cloud shell

## 事前準備

### terraform のインストール

- 各ディストリビューションのパッケージマネージャーを利用すると手順がバラバラになるため、curlでインストール。

´´´
curl -O https://releases.hashicorp.com/terraform/0.15.3/terrafrom_0.15.3_linux_amd64.zip
unzip terrafrom_0.15.3_linux_amd64.zip
mv terraform /usr/bin/terraform
´´´

### GCP credential ファイルの用意

- terraform での操作に必要な権限・サービスアカウントを用意
- サービスアカウントの作成はブラウザで実施
- 下記コマンドでcloud shell上にcredentialファイルをダウンロード

´´´
gcloud iam service-accounts keys create path_to_save/account.json \
--iam-account [service-account name]@[PROJECT_ID].iam.gserviceaccount.com
´´´

### terraform init



### terraform plan

### terraform apply

