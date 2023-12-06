---
title: 固定資産の帳簿に減価償却プロファイルを表示する方法
date: 2022-06-14
tags: 
  - FinOps-Finance
  - Fixed assets
disableDisclaimer: false
---

こんにちは、Dynamics ERP サポートチームの木村です。  
この記事では、固定資産の帳簿に減価償却プロファイルの変更機能を表示する方法についてご案内いたします。  

<!-- more -->
## 検証に用いた製品・バージョン
Dynamics 365 Finance and Operations      
Application version : 10.0.32 
Platform version : PU56
Legal entity : JPMF

パラメータの適用方法、動作につきましては以下をご覧ください。  

## 固定資産の帳簿にて減価償却プロファイルの変更を表示する方法
### "減価償却方法を手動での変更を許可" を**「はい」**に変更した場合
1. [固定資産] > [設定] > [固定資産パラメーター] を開く
1. [固定資産] > [減価償却] タブを開く
1. "減価償却方法を手動での変更を許可" を**「はい」**に変更し、保存する
![](./show-depreciationprofile/show-depreciationprofile_1.png)
1. [固定資産] > [固定資産] > [固定資産] を開く 
1. 任意の固定資産を開き、[帳簿] を押下する
**-> [機能] > [減価償却プロファイルの変更] が表示され、[減価償却] > [減価償却プロファイル] が表示されなくなる**
![](./show-depreciationprofile/show-depreciationprofile_2.png)
***  

### "減価償却方法を手動での変更を許可" を**「いいえ」**に変更した場合
![](./show-depreciationprofile/show-depreciationprofile_3.png)
1. [固定資産] > [固定資産] > [固定資産] を開く 
1. 任意の固定資産を開き、[帳簿] を押下する
**-> [機能] > [減価償却プロファイルの変更] が表示されず、[減価償却] > [減価償却プロファイル] が表示される**
![](./show-depreciationprofile/show-depreciationprofile_4.png)

## おわりに
---
以上、固定資産の帳簿に減価償却プロファイルの変更機能を表示する方法についてご紹介しました。  
減価償却プロファイルを変更する際にご利用ください。
