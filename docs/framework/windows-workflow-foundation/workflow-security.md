---
title: Zabezpečení pracovních postupů
ms.date: 03/30/2017
helpviewer_keywords:
- programming [WF], workflow security
ms.assetid: d712a566-f435-44c0-b8c0-49298e84b114
ms.openlocfilehash: 2a9b26f8da7616480f69a6c4580b8d351833c9ee
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646317"
---
# <a name="workflow-security"></a>Zabezpečení pracovních postupů
Windows Workflow Foundation (WF) je integrován s několika různými technologiemi, jako je například Microsoft SQL Server a Windows Communication Foundation (WCF). Interakce s těmito technologiemi může způsobit problémy se zabezpečením do pracovního postupu, pokud se provádí nesprávně.

## <a name="persistence-security-concerns"></a>Obavy o zabezpečení trvalosti

1. Pracovní postupy, <xref:System.Activities.Statements.Delay> které používají aktivitu a trvalost, musí být znovu aktivovány službou. Windows AppFabric používá službu správy pracovních postupů (WMS) k opětovné aktivaci pracovních postupů s časovači, jejichž platnost vypršela. WMS vytvoří <xref:System.ServiceModel.WorkflowServiceHost> pro hostování znovu aktivovaného pracovního postupu. Pokud je služba WMS zastavena, trvalé pracovní postupy nebudou znovu aktivovány, jakmile vyprší jejich časovače.

2. Přístup k trvalé instance by měl y chránit před škodlivými entitami mimo doménu aplikace. Kromě toho by vývojáři měli zajistit, že škodlivý kód nelze spustit ve stejné doméně aplikace jako trvalý instance kódu.

3. Trvalé instance by neměla být spuštěna se zvýšenými oprávněními (Správce).

4. Data zpracovávaná mimo doménu aplikace by měla být chráněna.

5. Aplikace, které vyžadují izolaci zabezpečení, by neměly sdílet stejnou instanci abstrakce schématu. Tyto aplikace by měly používat různé zprostředkovatele úložiště nebo zprostředkovatele úložiště nakonfigurované pro použití různých instancí úložiště.

## <a name="sql-server-security-concerns"></a>Obavy o zabezpečení serveru SQL Server

- Při použití velkého počtu podřízených aktivit, umístění, záložek, rozšíření hostitele nebo oborů nebo při použití záložek s velmi velkými datovými částmi může být paměť vyčerpána nebo během trvalosti může být přiděleno nesplatné množství místa v databázi. To lze zmírnit pomocí zabezpečení na úrovni objektu a databáze.

- Při <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>použití musí být úložiště instancí zabezpečeno.

- Citlivá data v úložišti instancí by měla být zašifrována. Další informace naleznete v tématu [SQL Server Encryption](/sql/relational-databases/security/encryption/sql-server-encryption).

- Vzhledem k tomu, že připojovací řetězec databáze je často součástí konfiguračního souboru, zabezpečení na úrovni systému Windows (ACL) by mělo být použito k zajištění zabezpečení konfiguračního souboru (Web.Config obvykle) a že informace o přihlášení a hesle nejsou zahrnuty v připojovacím řetězci. Ověřování systému Windows by mělo být použito mezi databází a webovým serverem.

## <a name="considerations-for-workflowservicehost"></a>Důležité informace pro WorkflowServiceHost

- Koncové body WCF (Windows Communication Foundation) používané v pracovních postupech by měly být zabezpečeny. Další informace naleznete v tématu [Přehled zabezpečení WCF](../wcf/feature-details/security-overview.md).

- Autorizace na úrovni hostitele <xref:System.ServiceModel.ServiceAuthorizationManager>lze implementovat pomocí . Podrobnosti najdete [v tématu Postup: Vytvoření vlastního správce autorizací pro službu.](../wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md)

- ServiceSecurityContext pro příchozí zprávy je také k dispozici v rámci pracovního postupu přístupem OperationContext.

## <a name="wf-security-pack-ctp"></a>CTP balíčku zabezpečení WF
 Microsoft WF Security Pack community technology preview (CTP) 1 je sada aktivit a jejich implementace založená na [Windows Workflow Foundation](index.md) v rozhraní [.NET Framework 4](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/w0x726c2(v=vs.100)) (WF 4) a Windows [Identity Foundation (WIF)](https://docs.microsoft.com/previous-versions/dotnet/framework/security/index). Aktualizace CTP 1 sady Microsoft WF Security Pack obsahuje aktivity i jejich návrháře, které ilustrují, jak snadno povolit různé scénáře související se zabezpečením pomocí pracovního postupu, včetně:

1. Zosobnění identity klienta v pracovním postupu

2. Autorizace v pracovním postupu, například PrincipalPermission a ověření deklarací identity

3. Ověřené zasílání zpráv pomocí klientských pověření zadaných v pracovním postupu, například uživatelské jméno nebo heslo nebo token načtený ze služby tokenů zabezpečení (STS).

4. Přenašeče tokenu zabezpečení klienta do back-endové služby (delegování založené na deklaracích identity) pomocí služby WS-Trust ActA

Další informace a stažení ctp sady WF Security Pack naleznete v [tématu: WF Security Pack CTP](https://archive.codeplex.com/?p=wf)
