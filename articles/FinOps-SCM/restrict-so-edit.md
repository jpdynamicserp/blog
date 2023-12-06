---
title: 請求後の販売注文の編集制御方法
date: 2022-06-14
tags: 
    - FinOps-SCM
    - Sales order
    - Accounts receivable parameters
disableDisclaimer: false
---

こんにちは、Dynamics ERP サポートチームの木村です。  
この記事では、請求後の販売注文の編集を制御するパラメータについてご案内いたします。  

<!-- more -->
## 検証に用いた製品・バージョン
Dynamics 365 Finance and Operations      
Application version : 10.0.32
Platform version : PU56
Legal entity : USMF

パラメータの適用方法、動作につきましては以下をご覧ください。  

## 請求後の販売注文の編集制御方法
### "請求済注文の安全レベル" を**「ロック済み」**に変更した場合
1. [売掛金管理] > [設定] > [売掛金勘定パラメーター] を開く
1. [更新] タブを開く
1. "請求済注文の安全レベル" を**「ロック済」**に変更し、保存する
![](./restrict-so-edit/restrict-so-edit_1.png)
1. 請求済の販売注文を開く  </br></br>
**-> [明細行の追加] などのボタンが非活性になる**
![](./restrict-so-edit/restrict-so-edit_2.png)
***  

### "請求済注文の安全レベル" を**「警告」**に変更した場合
![](./restrict-so-edit/restrict-so-edit_3.png)
1. [明細行の追加] などのボタンを押下する
1. 以下ダイアログが表示され、[はい] を押下する  
![](./restrict-so-edit/restrict-so-edit_4.png)  </br></br>
**-> ダイアログは表示されるが、請求済の販売注文は編集可能となる**
![](./restrict-so-edit/restrict-so-edit_5.png)
***  

### "請求済注文の安全レベル" を**「なし」**に変更した場合
![](./restrict-so-edit/restrict-so-edit_6.png)</br></br>
**-> 請求済の販売注文は常に編集可能**

## おわりに
---
以上、請求後の販売注文の編集を制御するパラメータについてご紹介いたしました。  
請求した販売注文に対して編集を制御されたいなどの場合には、上記パラメータをご利用ください。
