---
title: 適格請求書等保存方式 (インボイス制度) の対応状況について
date: 2023-03-23
tags:
  - FinOps-Finance
  - New Invoicing system requirements
  - Japan localization
disableDisclaimer: false
---

こんにちは、Dynamics ERP サポートチームの木村です。  
この記事では、 2023 年 10 月 1 日より開始される適格請求書等保存方式 (インボイス制度) について  
Dynamics 365 Finance における対応状況を随時更新して参ります。  

<!-- more -->
弊社では各チャネルでお客様への情報公開の準備を進めています。  
記事更新時点で公開が確認されているものおよび公開が予定されているものについて記載しています。  

なお制度の詳細については国税庁ホームページをご確認ください。  
[No.6498 適格請求書等保存方式（インボイス制度）](https://www.nta.go.jp/taxes/shiraberu/taxanswer/shohi/6498.htm)  

## 目次
1. [変更予定の内容](#update-contents)
1. [情報公開チャネル](#information-channel)
1. [現時点における既知の事象一覧](#bug-list)
1. [公開済みの機能](#published-function)
1. [経過措置について](#transitional-measures)


<a id='update-contents'></a>

## 変更予定の内容
売掛金管理の請求書、買掛金管理の請求書、プロジェクト請求書および各種月次締め請求書にて  
適格請求書発行事業者としての登録番号が記載されるようになります。  
また、請求書の消費税欄には総額から算出した消費税額を表示するように変更が行われております。  
  
<a id='information-channel'></a>

## 情報公開チャネル
公開資料  
  [Registration IDs - Finance | Dynamics 365 | Microsoft Learn](https://learn.microsoft.com/en-us/dynamics365/finance/localizations/europe/emea-registration-ids)  
  [Qualified Invoice System in Japan - Finance | Dynamics 365 | Microsoft Learn](https://learn.microsoft.com/en-us/dynamics365/finance/localizations/japan/apac-jpn-qualified-invoice-system)


<a id='bug-list'></a>

## 現時点における既知の事象一覧
| No. | 事象 | 方針 | 関連情報 |
| ---- | ---- | ---- | ---- |
| 1 | 消費税の照会をすると「実際の消費税の合計金額」に関係ない値が表示される | 修正済み | [Issue 862723](https://fix.lcs.dynamics.com/Issue/Details?bugId=862723) |
| 2 | 10 %と 8 %の税調整金額の合計が 0 円のときに消費税金額に再計算された金額が月次締め請求書に表示されていない | 修正予定 | [Issue 868315](https://fix.lcs.dynamics.com/Issue/Details?bugId=868315) |
| 3 | 10 %と 8 %の税調整金額の合計が 0 円のときに作成される消費税調整の伝票トランザクションに顧客 ID が設定されていない | 対応予定<br>(時期未定) | - |
| 4 | 消費税調整で作成された顧客トランザクションに支払期日が自動計算されておらず<br>転記日と同じ日付が設定されていて、支払条件や支払方法も設定されていない。 | 対応予定<br>(時期未定) | - |
| 5 | 税調整金額に対して入金消込を実行したが月次締め請求書の未払金額に税調整金額が表示される | 修正予定 | [Issue 864075](https://fix.lcs.dynamics.com/Issue/Details?bugId=864075) |
| 6 | 税調整金額がマイナス金額の場合に入金処理を実行して全額消込したが<br>支払済金額には税調整分の金額しか表示されず、全額消込しているのに未払い金額に金額が表示される | 修正予定 | No.5 と同様 |
| 7 | プロジェクト請求書で適格請求書を出力できない | 対応予定<br>(時期未定) | - |


<a id='published-function'></a>

## 公開済みの機能
適格請求書発行事業者の登録番号を入力する機能がバージョン 10.0.34 にてリリースされております。  
登録方法は以下の記事にてご案内しております。  
[適格請求書等保存方式 (インボイス制度) における事業者番号の登録および請求書への印字について | Japan Dynamics ERP Support Blog](https://jpdynamicserp.github.io/blog/FinOps-Finance/new-invoicing-system-requirements-QIInumber-setting/)


<a id='transitional-measures'></a>

## 経過措置について
免税事業者などとの仕入取引に対する経過措置の対応方法を以下の記事で公開しております。  
[適格請求書等保存方式 (インボイス制度) における経過措置の対応方法について | Japan Dynamics ERP Support Blog](https://jpdynamicserp.github.io/blog/FinOps-Finance/new-invoicing-system-requirements-transitional-measures/)

## おわりに  
以上、適格請求書等保存方式 (インボイス制度) の対応状況についてご案内いたしました。  