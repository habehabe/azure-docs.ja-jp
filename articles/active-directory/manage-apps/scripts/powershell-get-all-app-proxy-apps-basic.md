---
title: PowerShell サンプル - アプリケーション プロキシ アプリの基本情報の一覧表示
description: アプリケーション ID (AppId)、名前 (DisplayName)、オブジェクト ID (ObjId) と共に Azure Active Directory (Azure AD) アプリケーション プロキシ アプリケーションを一覧表示する PowerShell の例。
services: active-directory
author: msmimart
manager: CelesteDG
ms.service: active-directory
ms.subservice: app-mgmt
ms.workload: identity
ms.topic: conceptual
ms.date: 12/05/2019
ms.author: mimart
ms.reviewer: japere
ms.collection: M365-identity-device-management
ms.openlocfilehash: 009aabb8b742a752a29d775efbd11b153588c09b
ms.sourcegitcommit: 2ec4b3d0bad7dc0071400c2a2264399e4fe34897
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/27/2020
ms.locfileid: "75475673"
---
# <a name="get-all-application-proxy-apps-and-list-basic-information"></a>すべてのアプリケーション プロキシ アプリを取得し、基本情報を一覧表示する

この PowerShell スクリプトの例では、アプリケーション ID (AppId)、名前 (DisplayName)、オブジェクト ID (ObjId) など、すべての Azure Active Directory (Azure AD) アプリケーション プロキシ アプリケーションに関する情報を一覧表示します。

[!INCLUDE [quickstarts-free-trial-note](../../../../includes/quickstarts-free-trial-note.md)]

[!INCLUDE [updated-for-az](../../../../includes/updated-for-az.md)]

[!INCLUDE [cloud-shell-try-it.md](../../../../includes/cloud-shell-try-it.md)]

このサンプルでは、[AzureAD V2 PowerShell for Graph モジュール](https://docs.microsoft.com/powershell/azure/active-directory/install-adv2?view=azureadps-2.0) (AzureAD)、または[AzureAD V2 PowerShell for Graph モジュール プレビュー バージョン](https://docs.microsoft.com/powershell/azure/active-directory/install-adv2?view=azureadps-2.0-preview) (AzureADPreview) が必要です。
## <a name="sample-script"></a>サンプル スクリプト

[!code-azurepowershell[main](~/powershell_scripts/application-proxy/get-all-appproxy-apps-basic.ps1 "Get all Application Proxy apps")]

## <a name="script-explanation"></a>スクリプトの説明

| command | メモ |
|---|---|
|[Get-AzureADServicePrincipal](https://docs.microsoft.com/powershell/module/azuread/get-azureadserviceprincipal?view=azureadps-2.0) | サービス プリンシパルを取得します。 |

## <a name="next-steps"></a>次のステップ

Azure AD PowerShell モジュールの詳細については、[Azure AD PowerShell モジュールの概要](https://docs.microsoft.com/powershell/azure/active-directory/overview?view=azureadps-2.0)に関する記事を参照してください。

アプリケーション プロキシのその他の PowerShell の例については、[Azure AD アプリケーション プロキシの Azure AD PowerShell の例](../application-proxy-powershell-samples.md)に関する記事を参照してください。