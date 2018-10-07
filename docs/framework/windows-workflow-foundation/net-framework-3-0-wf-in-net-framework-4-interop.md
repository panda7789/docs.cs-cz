---
title: Používání aktivit WF rozhraní .NET Framework 3.0 v rozhraní .NET Framework 4 pomocí aktivity interoperability
ms.date: 03/30/2017
ms.assetid: 71f112ba-abb0-46f7-b05f-a5d2eb9d0c5c
ms.openlocfilehash: 386f71f21a4164f6f0ffc0ed19aab68abbe5a0b5
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/06/2018
ms.locfileid: "48844745"
---
# <a name="using-net-framework-30-wf-activities-in-net-framework-4-with-the-interop-activity"></a>Používání aktivit WF rozhraní .NET Framework 3.0 v rozhraní .NET Framework 4 pomocí aktivity interoperability
<xref:System.Activities.Statements.Interop> Aktivita je [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] aktivity (WF 4.5), která zabalí [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] aktivitu (WF 3.5) v rámci [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] pracovního postupu. Aktivita WF 3 může být jednoho listu aktivity nebo celý strom aktivit. Spuštění (včetně zrušení a zpracování výjimek) a stálost [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] aktivitu, ke kterým došlo v kontextu [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] instance pracovního postupu, který spouští.  
  
> [!NOTE]
>  <xref:System.Activities.Statements.Interop> Aktivity se nezobrazí v panelu nástrojů návrháře postupu, pokud projekt pracovního postupu neobsahuje jeho **Cílová architektura** nastavení **rozhraní .NET Framework 4.5**.  
  
## <a name="criteria-for-using-a-wf-3-activity-with-an-interop-activity"></a>Kritéria pro používání WF 3 aktivity s aktivitou spolupráce  
 Pro aktivitu WF 3 byl úspěšně spuštěn v rámci <xref:System.Activities.Statements.Interop> aktivity, musí splňovat následující kritéria:  
  
-   Aktivita WF 3 musí být odvozen od <xref:System.Workflow.ComponentModel.Activity?displayProperty=nameWithType>.  
  
-   Aktivita WF 3 musí být deklarována jako `public` a nemůže být `abstract`.  
  
-   Aktivita WF 3 musí mít veřejný výchozí konstruktor.  
  
-   Z důvodu omezení rozhraní typy, které <xref:System.Activities.Statements.Interop> aktivity může podporovat, <xref:System.Workflow.Activities.HandleExternalEventActivity> a <xref:System.Workflow.Activities.CallExternalMethodActivity> nesmí být použité přímo, ale odvozená díla aktivity vytvořené pomocí nástroje pro komunikační aktivity pracovního postupu (WCA.exe) lze použít. Zobrazit [nástroje Windows Workflow Foundation](https://go.microsoft.com/fwlink/?LinkId=178889) podrobnosti.  
  
## <a name="configuring-a-wf-3-activity-within-an-interop-activity"></a>Konfigurace pracovního postupu 3 aktivitu v rámci aktivitu spolupráce  
 Ke konfiguraci a předávání dat do a z aktivitu WF 3 napříč hranicemi, vlastnosti a vlastnosti aktivity WF 3 jsou vystavené <xref:System.Activities.Statements.Interop> aktivity. Metadata vlastnosti aktivity WF 3 (například <xref:System.Workflow.ComponentModel.Activity.Name%2A>) jsou přístupné prostřednictvím <xref:System.Activities.Statements.Interop.ActivityMetaProperties%2A> kolekce. Jde o kolekci dvojic název hodnota slouží k definování hodnot pro vlastnosti metadat aktivity WF 3. Vlastnost metadata má vlastnost se opírá o vlastnost závislosti pro kterou <xref:System.Workflow.ComponentModel.DependencyPropertyOptions.Metadata> je nastavený příznak.  
  
 Vlastnosti aktivity WF 3 jsou vystaveny prostřednictvím <xref:System.Activities.Statements.Interop.ActivityProperties%2A> kolekce. Toto je sada dvojic název hodnota, kde je každá hodnota <xref:System.Activities.Argument> objekt slouží k definování argumenty pro vlastnosti aktivity WF 3. Protože směr vlastnost aktivity WF 3 nelze odvodit, každé vlastnosti je prezentované jako <xref:System.Activities.InArgument> / <xref:System.Activities.OutArgument> pár. V závislosti na využití aktivitu vlastnosti, můžete chtít poskytnout <xref:System.Activities.InArgument> položku <xref:System.Activities.OutArgument> položky nebo obojí. Očekávaný název <xref:System.Activities.InArgument> položka v kolekci je název vlastnosti, jak jsou definovány pro aktivitu WF 3. Očekávaný název <xref:System.Activities.OutArgument> položka v kolekci je zřetězením názvu vlastnosti a řetězec "Out".  
  
## <a name="limitations-of-using-a-wf-3-activity-within-an-interop-activity"></a>Omezení použití WF 3 aktivitu v rámci aktivitu spolupráce  
 Aktivity WF 3 poskytované systémem nemohou být zabaleny přímo do <xref:System.Activities.Statements.Interop> aktivity. Pro některé aktivity WF 3 jako například <xref:System.Workflow.Activities.DelayActivity>, důvodem je, že je obdobou aktivita WF 4.5. Pro ostatní uživatele nastavení je to proto, že funkce aktivity není podporována. Řada aktivit WF 3 poskytované systémem lze použít v zabalený pomocí pracovních postupů <xref:System.Activities.Statements.Interop> aktivity v souladu s následujícími omezeními:  
  
1.  <xref:System.ServiceModel.Activities.Send> a <xref:System.ServiceModel.Activities.Receive> nelze použít v <xref:System.Activities.Statements.Interop> aktivity.  
  
2.  <xref:System.Workflow.Activities.WebServiceInputActivity>, <xref:System.Workflow.Activities.WebServiceOutputActivity>, a <xref:System.Workflow.Activities.WebServiceFaultActivity> nelze použít v rámci <xref:System.Activities.Statements.Interop> aktivity.  
  
3.  <xref:System.Workflow.Activities.InvokeWorkflowActivity> nelze použít v rámci <xref:System.Activities.Statements.Interop> aktivity.  
  
4.  <xref:System.Workflow.ComponentModel.SuspendActivity> nelze použít v rámci <xref:System.Activities.Statements.Interop> aktivity.  
  
5.  Aktivity související s popisovači Compensation nelze použít v rámci <xref:System.Activities.Statements.Interop> aktivity.  
  
 Existují také některé behaviorální specifika pochopit souvislosti s používáním aktivity WF 3 v rámci <xref:System.Activities.Statements.Interop> aktivity:  
  
1.  WF 3 aktivity obsažené v rámci <xref:System.Activities.Statements.Interop> aktivity jsou inicializovány při <xref:System.Activities.Statements.Interop> provádění aktivity. V systému Windows 4.5 není žádná fáze inicializace pro instanci pracovního postupu před jeho provedením.  
  
2.  Modul runtime WF 4.5 nemá kontrolního bodu stavu instance pracovního postupu při zahájení transakce, bez ohledu na to, kde začíná transakce (uvnitř nebo mimo <xref:System.Activities.Statements.Interop> aktivit).  
  
3.  WF 3 sledování záznamy aktivity v rámci <xref:System.Activities.Statements.Interop> aktivit jsou k dispozici WF 4.5 sledování účastníci jako <xref:System.Activities.Tracking.InteropTrackingRecord> objekty. <xref:System.Activities.Tracking.InteropTrackingRecord> je odvozený z <xref:System.Activities.Tracking.CustomTrackingRecord>.  
  
4.  Vlastní aktivity WF 3 můžou přistupovat k datům pomocí fronty pracovního postupu v součinnosti prostředí stejným způsobem jako v modulu runtime pracovního postupu WF 3. Nejsou potřeba žádné změny kódu vlastní aktivity. Na hostiteli, data jsou ve frontě do fronty pracovního postupu WF 3 pomocí obnovení <xref:System.Activities.Bookmark>. Název záložky se formátu řetězce <xref:System.IComparable> název fronty pracovního postupu.
