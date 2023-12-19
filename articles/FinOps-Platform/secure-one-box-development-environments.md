---
title: 新規で配置したクラウドホスト環境で証明書のエラーが発生した際の対処法
date: 2023-12-11
tags:
  - FinOps-Platform
  - Cloud-hosted
  - Certificate

disableDisclaimer: false
---

こんにちは、日本マイクロソフトの佐藤です。  
この記事では、新規で配置したクラウドホスト環境で証明書のエラーが発生した際の対処法をご案内します。
<!-- more -->

> [!NOTE]  
> 2023 年 11 月 15 日以降、Microsoft Entra テナントの証明書は、既定で新しいクラウドホスト環境にインストールされなくなりました。  
>この変更により、2023 年 11 月 15 日以降に構築されたクラウドホスト環境では、外部統合 (例: ユーザーのインポート、Microsoft Entra ID グループのインポート、電子申告 (ER) コンフィギュレーションのインポート) をデフォルトでは使用することができません。  
> 有効化するには、テナントへの証明書のアクセスを構成する必要があるため、本ブログではその手順をご案内いたします。

## 検証に用いた製品・バージョン
Dynamics 365 Finance and Operations  
Application version: 10.0.37  
Platform version: PU61  

## 新規で配置したクラウドホスト環境で証明書のエラーが発生した際の対処法
下記の手順で新しいアプリケーションと証明書の登録を設定します。また以下の手順は、下記の公開資料に記載されている手順となっております。

[Set up a new application and certificate registration - Finance & Operations | Dynamics 365 | Microsoft Learn](https://learn.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/dev-tools/secure-developer-vm#set-up-a-new-application-and-certificate-registration)  

1. [Azure Portal](https://portal.azure.com/) から下記の手順でアプリケーションをテナントに作成します。  
[アプリケーションを登録する - Finance & Operations | Dynamics 365 | Microsoft Learn](https://learn.microsoft.com/ja-jp/entra/identity-platform/quickstart-register-app#register-an-application)  
![](./secure-one-box-development-environments/secure-one-box-development-environments01.png)

1. 証明書を作成し、アプリケーションに追加します。  
発行の手順の例として、LCS の [環境の詳細] 画面から、クラウドホスト環境にリモート デスクトップ接続し、接続先にて Power Shell を起動します。  
Power Shell起動後、下記のコマンドを C:\Users\Admin*** ディレクトリで実行します。  
    ```powershell
    New-SelfSignedCertificate -CertStoreLocation Cert:\LocalMachine\My -DnsName "CHECert" -KeyExportPolicy Exportable -HashAlgorithm sha256 -KeyLength 2048 -KeySpec Signature -Provider "Microsoft Enhanced RSA and AES Cryptographic Provider" -NotBefore (Get-Date -Year 2020 -Month 5 -Day 1) -NotAfter (Get-Date -Year 2033 -Month 12 -Day 31)
    ```
    ![](./secure-one-box-development-environments/secure-one-box-development-environments02.png)  

1. CHECert という証明書ファイルがクラウドホスト環境のマシン上に作成されますので、リモート デスクトップ接続先で [Manage computer certificate] を開きます。  
![](./secure-one-box-development-environments/secure-one-box-development-environments03.png)  

1. リモートデスクトップ接続先で、CHECert 証明書をエクスポートし、cer ファイルを出力します。  
![](./secure-one-box-development-environments/secure-one-box-development-environments04.png)  

1. 出力した cer ファイルをリモート デスクトップ接続先からローカルの端末にコピーし、[Azure Portal](https://portal.azure.com/) から手順 1 で作成したアプリケーションに cer ファイルをアップロードします。  
![](./secure-one-box-development-environments/secure-one-box-development-environments05.png)  

1. リモート デスクトップ接続先の K:\AosService\webroot\ の下の web.config ファイルで、キーの値をアプリケーション ID/ クライアント ID に置き換え、キーとキーの値を、インストールされている証明書の拇印の値に置き換えます。  
    ```xml
    <add key="Aad.Realm" value="spn:<your application ID>" />
    <add key="Infrastructure.S2SCertThumbprint" value="<certificate thumbprint>" />
    <add key="GraphApi.GraphAPIServicePrincipalCert" value="<certificate thumbprint>" />
    ```

1. 環境 URL をアプリケーションのリダイレクト URI として追加します。詳細は [リダイレクト URI を追加する- Finance & Operations | Dynamics 365 | Microsoft Learn](https://learn.microsoft.com/ja-jp/entra/identity-platform/quickstart-register-app#add-a-redirect-uri) を参照してください。  

1. アプリケーションの API アクセス許可を割り当てます。  
    1. [Azure Portal](https://portal.azure.com/) から手順1で作成したアプリケーションにて、[APIのアクセス許可] から下記の項目について設定します。  
        - Dynamics ERP – このアクセス許可は、Dynamics 365 Finance and Operations 環境にアクセスするために必要になります。  
        - Microsoft Graph (User.Read.All および Group.Read.All のアクセス許可) - クラウドホスト環境で、新しくインストールした証明書のネットワーク サービスへの読み取りアクセス権を付与します。  
        ![](./secure-one-box-development-environments/secure-one-box-development-environments06.png)  
    1. リモート デスクトップ接続先のクラウドホスト環境にて、[Manage computer certificate] を開き、CHECert に対し、[Manage Private Key] を設定します。  
    ![](./secure-one-box-development-environments/secure-one-box-development-environments07.png)  
    1. [Permissions for CHECert private keys] の画面が開いたら、[Add] を選択します。  
    ![](./secure-one-box-development-environments/secure-one-box-development-environments08.png)  
    1. "NETWORK SERVICE" を入力し、Check Name を選択し、OK を選択します。  
    ![](./secure-one-box-development-environments/secure-one-box-development-environments09.png)  
    1. 作成された“NETWORK SERVICE” に対し、Read を有効化し、Apply を選択します。  
    ![](./secure-one-box-development-environments/secure-one-box-development-environments10.png)  

上記の設定により、テナントへの証明書のアクセスを構成できます。  

---
## おわりに  

以上、新規で配置したクラウドホスト環境で証明書のエラーが発生した際の対処法をご紹介いたしました。  