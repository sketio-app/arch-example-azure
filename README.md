# arch-example-azure

[日本語](#日本語) | [English](#english)

## 日本語

[Sketio Arch](https://arch.sketio.app) のパーサー検証用サンプルです。実際に動くアプリではなく、Azure の構成を Terraform（azurerm）で書いた見本です。`terraform apply` はしません。

構成は、Linux の Function App（App Service プラン上）が、ストレージ アカウントと Azure Cosmos DB につながります。Cosmos DB のキーは Azure Key Vault の secret に入れ、Function App の `app_settings` から `@Microsoft.KeyVault(SecretUri=...)` で参照します。Function App は仮想ネットワークのサブネットに接続し、Application Insights にログを送ります。

| 書き方 | 場所 |
|---|---|
| Terraform（HCL、azurerm） | `terraform/main.tf` |

Terraform のラベルは小文字です（`uploads` `orders` `main` `api` など）。サブスクリプション ID や秘密の値は書いていません。

`.sketio.yml` で `ai.enabled: true` にしてあります。静的に読めないファイルは、Arch の AI が読んで補います。

ライセンスは MIT です。

## English

A sample for testing the parsers of [Sketio Arch](https://arch.sketio.app). It is not a working app; it is a reference showing an Azure setup written in Terraform (azurerm). It is never applied.

The setup: a Linux Function App (on an App Service plan) connects to a storage account and Azure Cosmos DB. The Cosmos DB key lives in an Azure Key Vault secret, which the Function App's `app_settings` reference with `@Microsoft.KeyVault(SecretUri=...)`. The Function App joins a virtual network subnet and sends telemetry to Application Insights.

| Way of writing it | Where |
|---|---|
| Terraform (HCL, azurerm) | `terraform/main.tf` |

The Terraform labels are lowercase (`uploads`, `orders`, `main`, `api`, and so on). No subscription id or secret value is written.

`.sketio.yml` sets `ai.enabled: true`, so Arch's AI reads the files the static parsers cannot.

MIT licensed.
