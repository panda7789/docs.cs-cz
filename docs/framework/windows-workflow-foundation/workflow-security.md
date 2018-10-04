---
title: Pracovní postup zabezpečení
ms.date: 03/30/2017
helpviewer_keywords:
- programming [WF], workflow security
ms.assetid: d712a566-f435-44c0-b8c0-49298e84b114
ms.openlocfilehash: 726e41e8cde028fb86004ff06e2ad0663a042287
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/04/2018
ms.locfileid: "48580073"
---
# <a name="workflow-security"></a>Pracovní postup zabezpečení
Windows Workflow Foundation (WF) je integrovaná s několika různých technologií, jako je například Microsoft SQL Server a Windows Communication Foundation (WCF). Interakce s tyto technologie vznikat potíže se zabezpečením do vašich pracovních postupů v případě aktivace nesprávně.

## <a name="persistence-security-concerns"></a>Zajištění trvalého zabezpečení

1.  Pracovní postupy využívající <xref:System.Activities.Statements.Delay> aktivity a stálost potřeba znovu aktivovat službou. Windows AppFabric pomocí služby správy pracovního postupu (WMS) znovu aktivovat pracovní postupy s vypršenou platností časovače. Vytvoří WMS <xref:System.ServiceModel.WorkflowServiceHost> k hostování opětovně pracovního postupu. Pokud je zastavena služba WMS, trvalý pracovní postupy nebudou znovu aktivovat po vypršení jejich časovače.

2.  Přístup k vytváření instancí trvalý by měly být chráněné proti škodlivým entity externí domény aplikace. Vývojáři navíc se ujistěte, že škodlivý kód nelze provést ve stejné doméně jako trvalý vytvoření instance kódu aplikace.

3.  Vytváření odolných instancí neměli spouštět se zvýšenými oprávněními (správce).

4.  Data zpracovává mimo doménu aplikace by měly být chráněné.

5.  Aplikace, které vyžadují izolaci zabezpečení by neměly sdílet stejnou instanci abstrakce schématu. Tyto aplikace použijte poskytovatele různých úložišť, nebo uložit poskytovatelé umožňují použít různé úložiště instancí.

## <a name="sql-server-security-concerns"></a>Otázky zabezpečení SQL serveru

-   Pokud se používá velké množství podřízené aktivity, umístění, záložek, rozšíření hostitele nebo obory nebo pokud se používají záložky s velmi velkých datových částí, může dojít k vyčerpání paměti nebo odešel množství volného místa databáze může být přidělen při stálost. To lze zmírnit použitím zabezpečení na úrovni objektů a na úrovni databáze.

-   Při použití <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>, musí být zabezpečené úložiště instancí. Další informace najdete v tématu [osvědčené postupy pro SQL Server](https://go.microsoft.com/fwlink/?LinkId=164972).

-   Zašifrovat citlivá data v úložišti instancí. Další informace najdete v tématu [šifrování zabezpečení SQL](https://go.microsoft.com/fwlink/?LinkId=164976).

-   Vzhledem k tomu, že připojovací řetězec databáze je často součástí konfiguračního souboru, zabezpečení na úrovni systému windows (ACL) by měla sloužit k zajištění, že konfigurační soubor (obvykle Web.Config) je zabezpečený a přihlašovací jméno a heslo informace nejsou součástí připojovací řetězec. Ověřování Windows by měl místo toho použít mezi databází a webový server.

## <a name="considerations-for-workflowservicehost"></a>Důležité informace pro hostitele služby pracovního postupu

-   Windows Communication Foundation (WCF) koncových bodů použitých v pracovních postupech by měla být zabezpečená. Další informace najdete v tématu [WCF – Přehled zabezpečení](https://go.microsoft.com/fwlink/?LinkID=164975).

-   Může být implementována autorizaci na úrovni hostitele pomocí <xref:System.ServiceModel.ServiceAuthorizationManager>. Zobrazit [postupy: vytvoření vlastního Správce autorizací pro službu](https://go.microsoft.com/fwlink/?LinkId=192228) podrobnosti.

-   ServiceSecurityContext pro příchozí zprávy je také dostupné v rámci pracovního postupu tak přístup k informacím OperationContext.

## <a name="wf-security-pack-ctp"></a>Balíček zabezpečení WF CTP
 Microsoft WF zabezpečení Pack CTP 1 je první verze preview (CTP) technologie komunity sady aktivit a jejich provedení na základě [Windows Workflow Foundation](https://msdn.microsoft.com/netframework/aa663328.aspx)v [rozhraní .NET Framework 4](https://msdn.microsoft.com/netframework/default.aspx) pracovní postup WF ( (4) a [Windows Identity Foundation (WIF)](https://msdn.microsoft.com/security/aa570351.aspx).  CTP 1 Microsoft WF zabezpečení balíček obsahuje aktivity a jejich návrhářů, které ukazují, jak jednoduše povolit různé scénáře související se zabezpečením pomocí pracovního postupu, včetně:

1.  Zosobnění identity klienta v pracovním postupu

2.  V pracovním postupu autorizace, jako například PrincipalPermission a ověřování deklarací identity

3.  Ověřený zasílání zpráv pomocí ClientCredentials určeným v pracovním postupu, jako je například uživatelské jméno a heslo, nebo token načíst z tokenu služby zabezpečení (STS)

4.  Tok tokenu zabezpečení klienta ke službě back-end (založené na deklaracích delegování) pomocí WS-Trust ActAs

Další informace a stáhnout verzi CTP WF zabezpečení balíčku najdete v tématu: [WF zabezpečení Pack CTP](http://wf.codeplex.com/releases/view/48114)