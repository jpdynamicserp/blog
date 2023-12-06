---
title: ワークスペース「経費管理」から特定のプロジェクトに経費カテゴリ「日当」を紐づける方法
date: 2022-10-04
tags:
  - FinOps-Finance
  - Project management
  - Japan localization
disableDisclaimer: false
---
こんにちは、Dynamics ERP サポートチームの西田です。  
この記事では、ワークスペース「経費管理」から特定のプロジェクトに経費カテゴリ「日当」を紐づける方法ついてご紹介します。  
<!-- more -->

## 検証に用いた製品・バージョン:
Dynamics 365 Finance and Operations  
Application version: 10.0.26  
Platform version: PU50  

## 手順詳細
**1. 機能管理にて「経費レポートの再想像 (Expense reports re-imagined) 」「経費精算書の再設計されたインターフェイスの日当 (Per-diem for expense report re-imagined) 」を有効化する**  
    経路 : ワークスペース > 機能管理  
    以下 2 つの機能を有効化してください。
   ![](./perdiem-expense-project/image-name1.png)

**2. 共有カテゴリ (Shared categories) を作成する**  
    経路 : モジュール > 経費管理 > 設定 > 全般 > 共有カテゴリ  
    「新規」から経費タイプ「日当」の共有カテゴリを作成してください。 (すでに既存のカテゴリがある場合はそちらをご利用いただくことも可能です)  
    その際、「プロジェクトで使用可」「経費で使用可」にチェックを入れてください。  
   ![](./perdiem-expense-project/image-name2.png)

**3. 経費カテゴリ (Expense categories) を作成する**  
    経路 : モジュール > 経費管理 > 設定 > 全般 > 経費カテゴリ  
    「新規」からカテゴリ ID に手順 2 で作成したカテゴリ ID を使用した経費カテゴリを作成してください。 (すでに既存のカテゴリがある場合はそちらをご利用いただくことも可能です)  
    その際、「プロジェクトでの使用」にチェックを入れ、必須項目「カテゴリグループ」「既存の支払方法」を入力してください。  
   ![](./perdiem-expense-project/image-name3.png)

**4. 経費フィールドの表示 (経費レポートの再設計) (Expense fields visibility (Expense reports re-imagined)) を設定する**  
    経路 : モジュール > 経費管理 > 設定 > 全般 > 経費フィールドの表示 (経費レポートの再設計)  
    「経費」タブから「プロジェクト ID 」を「推奨」にしてください。  
   ![](./perdiem-expense-project/image-name4.png)

**5. 日当の場所 (Per diems) を作成する**  
    経路 : モジュール > 経費管理 > 設定 > 計算とコード > 日当の場所  
    「新規」から日当の場所を作成してください。  
   ![](./perdiem-expense-project/image-name5.png)

**6. 日当金額 (Per diem amounts) を作成する**  
    経路 : モジュール > 経費管理 > 設定 > 計算とコード > 日当  
    「新規」から場所に手順5で作成した場所を選んで日当金額を作成してください。  
   ![](./perdiem-expense-project/image-name6.png)

**7. 経費を作成する**  
    経路 : モジュール > 経費管理 > ワークスペース > 経費管理  
    「新しい経費精算書」から新しい経費精算書を作成し、「新しい経費」から詳細情報を入力してください。  
    (このとき、カテゴリは手順 3 で作成したカテゴリを指定し、日付は手順 6 で作成した日当の開始日・終了日内に含めてください)  
   ![](./perdiem-expense-project/image-name7.png)  
   ![](./perdiem-expense-project/image-name7-2.png)

**8. 「一括編集」からプロジェクト ID を設定し、「保存して続行」を押下する**  
   ![](./perdiem-expense-project/image-name8.png)  
   ![](./perdiem-expense-project/image-name8-2.png)

   これにて経費とプロジェクトの関連付けが完了です。

## おわりに  
以上、ワークスペース「経費管理」から特定のプロジェクトに経費カテゴリ「日当」を紐づける方法ついてご紹介しました。
