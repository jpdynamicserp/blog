<<<<<<< HEAD:articles/D365FO App SCM/cancel-productreceipt-linkso.md
---
title: 販売注文に紐づく発注書の製品受領書のキャンセル方法
date: 2022-09-07
tags: 
    - D365FO SCM
    - Sales order
    - Purchase order    
disableDisclaimer: false
---

こんにちは、Dynamics ERP サポートチームの木村です。  
この記事では、販売注文に紐づく発注書の製品受領書のキャンセル方法についてご案内いたします。  

<!-- more -->
## 検証に用いた製品・バージョン:
Dynamics 365 Finance and Operations  
Application version : 10.0.33  
Platform version : PU 57  
Legal entity : USMF  

販売注文に紐づく発注書の製品受領書のキャンセル方法につきましては以下をご覧ください。  

## 販売注文に紐づく発注書の製品受領書のキャンセル方法
下記エラーメッセージが表示された際のキャンセル方法についてご案内いたします。
> 1.00 cannot be picked because only 0.00 is/are available from the inventory for item: 1000.
>
> 日本語：品目1000の在庫から0.00しか利用できないため、1.00をピッキングできません。
![](./cancel-productreceipt-linkso/cancel-productreceipt-linkso_1.png)

1. 紐づく販売注文画面の [Inventory] > [Maintain] > [Reservation] を押下する
![](./cancel-productreceipt-linkso/cancel-productreceipt-linkso_2.png)

1. "Reservation" を「1」から「0」に変更（引当数量をなくす）
![](./cancel-productreceipt-linkso/cancel-productreceipt-linkso_3.png)  
※ 変更後
![](./cancel-productreceipt-linkso/cancel-productreceipt-linkso_4.png)

1. 再度、発注書を開く
1. [Receive] > [Journals] > [Product receipt] を開く
1. 製品受領書のキャンセルを実施
![](./cancel-productreceipt-linkso/cancel-productreceipt-linkso_5.png) 

## おわりに
---
以上、販売注文に紐づく発注書の製品受領書のキャンセル方法についてご案内いたしました。  
また、設定内容や利用方法により上記の手順が適用できない可能性があることを予めご了承ください。  
=======
---
title: 販売注文に紐づく発注書の製品受領書のキャンセル方法
date: 2022-09-07
tags: 
    - D365FO SCM
    - Sales order
    - Purchase order    
disableDisclaimer: false
---

こんにちは、Dynamics ERP サポートチームの木村です。  
この記事では、販売注文に紐づく発注書の製品受領書のキャンセル方法についてご案内いたします。  

<!-- more -->
## 検証に用いた製品・バージョン:
Dynamics 365 Finance and Operations  
Application version : 10.0.33  
Platform version : PU 57  
Legal entity : USMF  

販売注文に紐づく発注書の製品受領書のキャンセル方法につきましては以下をご覧ください。  

## 販売注文に紐づく発注書の製品受領書のキャンセル方法
下記エラーメッセージが表示された際のキャンセル方法についてご案内いたします。
> 1.00 cannot be picked because only 0.00 is/are available from the inventory for item: 1000.
>
> 日本語：品目1000の在庫から0.00しか利用できないため、1.00をピッキングできません。
![](./cancel-productreceipt-linkso/cancel-productreceipt-linkso_1.png)

1. 紐づく販売注文画面の [Inventory] > [Maintain] > [Reservation] を押下する
![](./cancel-productreceipt-linkso/cancel-productreceipt-linkso_2.png)

1. "Reservation" を「1」から「0」に変更（引当数量をなくす）
![](./cancel-productreceipt-linkso/cancel-productreceipt-linkso_3.png)  
※ 変更後
![](./cancel-productreceipt-linkso/cancel-productreceipt-linkso_4.png)

1. 再度、発注書を開く
1. [Receive] > [Journals] > [Product receipt] を開く
1. 製品受領書のキャンセルを実施
![](./cancel-productreceipt-linkso/cancel-productreceipt-linkso_5.png) 

## おわりに
---
以上、販売注文に紐づく発注書の製品受領書のキャンセル方法についてご案内いたしました。  
また、設定内容や利用方法により上記の手順が適用できない可能性があることを予めご了承ください。  
>>>>>>> repoA/main:articles/FinOps-SCM/cancel-productreceipt-linkso.md
