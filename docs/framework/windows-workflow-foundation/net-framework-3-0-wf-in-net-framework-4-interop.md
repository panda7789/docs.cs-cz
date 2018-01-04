---
title: "Pomocí aktivity WF rozhraní .NET Framework 3.0 v rozhraní .NET Framework 4 s spolupráce aktivity"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 71f112ba-abb0-46f7-b05f-a5d2eb9d0c5c
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e551a2a5253232ca7e504ea484601fb935901da4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="using-net-framework-30-wf-activities-in-net-framework-4-with-the-interop-activity"></a>Pomocí aktivity WF rozhraní .NET Framework 3.0 v rozhraní .NET Framework 4 s spolupráce aktivity
<xref:System.Activities.Statements.Interop> Aktivita [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] aktivity (WF 4.5), která zabalí [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] (WF 3.5) aktivitu v rámci [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] pracovního postupu. Aktivita WF 3 může být aktivitu jednoho typu nebo celý strom aktivit. Provádění (včetně zrušení a zpracování výjimek) a perzistence [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] aktivita provedena v kontextu [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] instance pracovního postupu, který spouští.  
  
> [!NOTE]
>  <xref:System.Activities.Statements.Interop> Aktivita se nezobrazí v panelu nástrojů Návrháře pracovního postupu nezadáte pracovního postupu projekt má svůj **cílové rozhraní** nastavení **rozhraní .NET Framework 4.5**.  
  
## <a name="criteria-for-using-a-wf-3-activity-with-an-interop-activity"></a>Kritéria pro používání WF 3 aktivitu aktivitu spolupráce  
 Aktivity WF 3 úspěšně provést v rámci <xref:System.Activities.Statements.Interop> aktivity, musí být splněny následující kritéria:  
  
-   Aktivita WF 3 musí být odvozeny od <xref:System.Workflow.ComponentModel.Activity?displayProperty=nameWithType>.  
  
-   Aktivita WF 3 musí být deklarována jako `public` a nemůže být `abstract`.  
  
-   Aktivita WF 3 musí mít veřejný výchozí konstruktor.  
  
-   Z důvodu omezení v rozhraní typy, které <xref:System.Activities.Statements.Interop> aktivity může podporovat, <xref:System.Workflow.Activities.HandleExternalEventActivity> a <xref:System.Workflow.Activities.CallExternalMethodActivity> nelze použít přímo, ale odvozené aktivity vytvořené pomocí nástroje komunikace aktivity pracovního postupu (WCA.exe) lze použít. V tématu [nástroje Windows Workflow Foundation](http://go.microsoft.com/fwlink/?LinkId=178889) podrobnosti.  
  
## <a name="configuring-a-wf-3-activity-within-an-interop-activity"></a>Konfigurace WF 3 aktivitu v rámci spolupráce aktivitu  
 Ke konfiguraci a předávání dat do a z aktivitu WF 3 přes součinnosti hranice, vlastnosti a vlastnosti metadat aktivity WF 3 jsou vystavené <xref:System.Activities.Statements.Interop> aktivity. Vlastnosti metadat aktivity WF 3 (například <xref:System.Workflow.ComponentModel.Activity.Name%2A>) jsou k dispozici prostřednictvím <xref:System.Activities.Statements.Interop.ActivityMetaProperties%2A> kolekce. Toto je kolekce dvojic název hodnota používá k definování hodnoty pro vlastnosti metadat aktivity WF 3. Vlastnost metadat je vlastnost zajišťoval vlastnost závislosti, pro kterou <xref:System.Workflow.ComponentModel.DependencyPropertyOptions.Metadata> je nastavený příznak.  
  
 Vlastnosti aktivity WF 3 se zveřejňují přes <xref:System.Activities.Statements.Interop.ActivityProperties%2A> kolekce. To je sada dvojic název hodnota, kde je každá hodnota <xref:System.Activities.Argument> objekt, používá k definování argumenty pro vlastnosti aktivity WF 3. Protože směr vlastnosti aktivity WF 3 nelze odvodit, jako je prezentované všech vlastností <xref:System.Activities.InArgument> / <xref:System.Activities.OutArgument> pár. V závislosti na aktivity využití vlastnosti, můžete chtít zadat <xref:System.Activities.InArgument> položky <xref:System.Activities.OutArgument> položku, nebo obojí. Očekávaný název <xref:System.Activities.InArgument> položka v kolekci je název vlastnosti, jak je definováno ve aktivity WF 3. Očekávaný název <xref:System.Activities.OutArgument> položka v kolekci je zřetězení názvu vlastnosti a řetězec "Z".  
  
## <a name="limitations-of-using-a-wf-3-activity-within-an-interop-activity"></a>Omezení použití WF 3 aktivitu v rámci spolupráce aktivitu  
 Aktivity WF 3 poskytované systémem nemůže být uzavřen přímo do <xref:System.Activities.Statements.Interop> aktivity. Pro některé aktivity WF 3 jako například <xref:System.Workflow.Activities.DelayActivity>, totiž podobá aktivita WF 4.5 existuje. Pro ostatní nastavení je to proto, že funkce aktivity není podporována. Řada aktivit WF 3 poskytované systémem lze použít v rámci pracovních zabalený pomocí <xref:System.Activities.Statements.Interop> aktivity, které se vztahují následující omezení:  
  
1.  <xref:System.ServiceModel.Activities.Send>a <xref:System.ServiceModel.Activities.Receive> nelze použít v <xref:System.Activities.Statements.Interop> aktivity.  
  
2.  <xref:System.Workflow.Activities.WebServiceInputActivity>, <xref:System.Workflow.Activities.WebServiceOutputActivity>, a <xref:System.Workflow.Activities.WebServiceFaultActivity> nelze použít v rámci <xref:System.Activities.Statements.Interop> aktivity.  
  
3.  <xref:System.Workflow.Activities.InvokeWorkflowActivity>nelze použít v rámci <xref:System.Activities.Statements.Interop> aktivity.  
  
4.  <xref:System.Workflow.ComponentModel.SuspendActivity>nelze použít v rámci <xref:System.Activities.Statements.Interop> aktivity.  
  
5.  Aktivity související s kompenzace nelze použít v rámci <xref:System.Activities.Statements.Interop> aktivity.  
  
 Existují také některé chování specifika pochopit souvislosti s používáním aktivity WF 3 v rámci <xref:System.Activities.Statements.Interop> aktivity:  
  
1.  WF 3 aktivity obsažené v rámci <xref:System.Activities.Statements.Interop> aktivity jsou inicializovány při <xref:System.Activities.Statements.Interop> je aktivita spuštěna. V WF 4.5 není žádná fáze inicializace pro instanci pracovního postupu před jeho spuštění.  
  
2.  Modul runtime pracovního postupu 4.5 nemá kontrolního bodu stav instance pracovního postupu při zahájení transakce, bez ohledu na to, kde začíná této transakce (uvnitř nebo mimo <xref:System.Activities.Statements.Interop> aktivity).  
  
3.  Zaznamenává 3 sledování WF aktivity v rámci <xref:System.Activities.Statements.Interop> aktivita se poskytuje WF 4.5 sledování účastníkům jako <xref:System.Activities.Tracking.InteropTrackingRecord> objekty. <xref:System.Activities.Tracking.InteropTrackingRecord>je odvozený z <xref:System.Activities.Tracking.CustomTrackingRecord>.  
  
4.  Vlastní aktivity WF 3 přístup k datům pomocí fronty pracovního postupu prostředí součinnosti stejným způsobem jako v modulu runtime pracovního postupu WF 3. Nejsou vyžadovány žádné změny kódu vlastní aktivity. Na hostiteli, data, je zařazených do fronty, do fronty pracovní postup WF 3 obnovení <xref:System.Activities.Bookmark>. Název záložky je řetězec formátu <xref:System.IComparable> název fronty pracovního postupu.  
  
## <a name="see-also"></a>Viz také  
 [Použití aktivity rozhraní .NET Framework 3.0 nebo .NET Framework 3.5 v pracovním postupu rozhraní .NET Framework 4.5](../../../docs/framework/windows-workflow-foundation/samples/using-a-net-3-0-or-net-3-5-activity-in-a-net-4-5-workflow.md)
