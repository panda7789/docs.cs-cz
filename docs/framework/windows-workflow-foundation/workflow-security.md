---
title: Zabezpečení pracovních postupů
ms.date: 03/30/2017
helpviewer_keywords:
- programming [WF], workflow security
ms.assetid: d712a566-f435-44c0-b8c0-49298e84b114
ms.openlocfilehash: 36d03a2fca8f143b98338050fc9da4490960bda9
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837516"
---
# <a name="workflow-security"></a>Zabezpečení pracovních postupů
Programovací model Windows Workflow Foundation (WF) je integrováno s několika různými technologiemi, jako je například Microsoft SQL Server a Windows Communication Foundation (WCF). Interakce s těmito technologiemi může v případě nesprávného dokončení způsobit problémy se zabezpečením do pracovního postupu.

## <a name="persistence-security-concerns"></a>Otázky zabezpečení trvalosti

1. Pracovní postupy, které používají <xref:System.Activities.Statements.Delay> aktivity a trvalosti, je nutné znovu aktivovat službou. Technologie Windows AppFabric používá službu Řízení pracovního postupu (WMS) k opětovné aktivaci pracovních postupů s časovači s vypršenou platností. WMS vytvoří <xref:System.ServiceModel.WorkflowServiceHost> pro hostování znovu aktivovaného pracovního postupu. Pokud se služba WMS zastaví, trvalé pracovní postupy se po vypršení platnosti jejich časovače znovu neaktivují.

2. Přístup k trvalým vytvářením instancí by měl být chráněn proti škodlivým entitám mimo doménu aplikace. Kromě toho by vývojáři měli zajistit, aby škodlivý kód nemohl být spuštěn ve stejné doméně aplikace jako trvalý kód vytváření instancí.

3. Trvalé vytváření instancí by se nemělo spouštět se zvýšenými oprávněními (správce).

4. Data zpracovaná mimo doménu aplikace by měla být chráněna.

5. Aplikace, které vyžadují izolaci zabezpečení, by neměly sdílet stejnou instanci abstrakce schématu. Takové aplikace by měly používat jiné poskytovatele úložiště nebo poskytovatele úložiště nakonfigurované na používání různých instancí úložiště.

## <a name="sql-server-security-concerns"></a>Problémy se zabezpečením SQL Server

- Pokud se používá velký počet podřízených aktivit, umístění, záložek, rozšíření hostitelů nebo oborů, nebo když se používají záložky s velkými objemy dat, může být paměť vyčerpána nebo je možné během trvalosti přidělit neoprávněné množství místa v databázi. To lze zmírnit použitím zabezpečení na úrovni objektů a databáze.

- Při použití <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>musí být úložiště instancí zabezpečené.

- Citlivá data v úložišti instancí by měla být zašifrovaná. Další informace najdete v tématu [šifrování SQL Server](/sql/relational-databases/security/encryption/sql-server-encryption).

- Vzhledem k tomu, že připojovací řetězec databáze je často součástí konfiguračního souboru, měli byste použít zabezpečení na úrovni systému Windows, aby se zajistilo, že konfigurační soubor (Web. config je obvykle) je zabezpečený a že informace o přihlašovacích údajích a heslech nejsou zahrnuté v připojovací řetězec Místo toho by se mělo používat ověřování systému Windows mezi databází a webovým serverem.

## <a name="considerations-for-workflowservicehost"></a>Předpoklady pro hostitelskou hostitele

- Koncové body Windows Communication Foundation (WCF) použité v pracovních postupech by měly být zabezpečené. Další informace najdete v tématu [Přehled zabezpečení služby WCF](../wcf/feature-details/security-overview.md).

- Autorizaci na úrovni hostitele je možné implementovat pomocí <xref:System.ServiceModel.ServiceAuthorizationManager>. Podrobnosti najdete v tématu [Postup: Vytvoření vlastního Správce autorizací pro službu](../wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md) .

- ServiceSecurityContext pro příchozí zprávy je také k dispozici v rámci pracovního postupu přístupem k OperationContext.

## <a name="wf-security-pack-ctp"></a>WF Security Pack CTP
 Microsoft WF Security Pack CTP 1 je první vydání sady aktivit (Community Technology Preview) a jejich implementace na základě [programovací model Windows Workflow Foundation](index.md) v [.NET Framework 4](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/w0x726c2(v=vs.100)) (WF 4) a [Windows Identity Foundation (WIF)](../security/index.md).  Microsoft WF Security Pack CTP 1 obsahuje obě aktivity a jejich návrháře, které ukazují, jak snadno povolit různé scénáře související se zabezpečením pomocí pracovního postupu, včetně těchto:

1. Zosobnění identity klienta v pracovním postupu

2. Autorizace v rámci pracovního postupu, jako je například PrincipalPermission a ověřování deklarací identity

3. Ověřené zasílání zpráv pomocí ClientCredentials zadané v pracovním postupu, jako je uživatelské jméno/heslo nebo token načtený ze služby tokenů zabezpečení (STS)

4. Přenos tokenu zabezpečení klienta do back-endové služby (delegování založené na deklaracích) pomocí WS-Trust ActAs

Další informace a stažení balíčku zabezpečení WF Security Pack CTP najdete v tématu: [WF Security Pack CTP](https://archive.codeplex.com/?p=wf)
