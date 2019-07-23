---
title: Použití aktivit pracovních postupů .NET Framework 3.0 v rozhraní .NET Framework 4 pomocí aktivity interoperability
ms.date: 03/30/2017
ms.assetid: 71f112ba-abb0-46f7-b05f-a5d2eb9d0c5c
ms.openlocfilehash: baca65da29fd0b18bd61f9b79ce82429faaed432
ms.sourcegitcommit: 30a83efb57c468da74e9e218de26cf88d3254597
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/20/2019
ms.locfileid: "68364146"
---
# <a name="using-net-framework-30-wf-activities-in-net-framework-4-with-the-interop-activity"></a>Použití aktivit pracovních postupů .NET Framework 3.0 v rozhraní .NET Framework 4 pomocí aktivity interoperability
Aktivita je aktivita [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] (WF[!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] 4,5), která zabalí aktivitu (WF 3,5) v rámci pracovního postupu. [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] <xref:System.Activities.Statements.Interop> Aktivita WF 3 může být jedna koncová aktivita nebo celá struktura aktivit. Spuštění (včetně zrušení a zpracování výjimek) a trvalost [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] aktivity dojde v kontextu [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] instance pracovního postupu, která je spuštěna.  
  
> [!NOTE]
>  Tato <xref:System.Activities.Statements.Interop> aktivita se nezobrazuje v sadě nástrojů návrháře pracovních postupů, pokud má projekt pracovního postupu nastavenou **cílovou architekturu** na hodnotu **.NET Framework 4,5**.  
  
## <a name="criteria-for-using-a-wf-3-activity-with-an-interop-activity"></a>Kritéria pro použití aktivity WF 3 s aktivitou spolupráce  
 Aby aktivita WF 3 mohla úspěšně běžet v rámci <xref:System.Activities.Statements.Interop> aktivity, musí být splněné následující kritérium:  
  
- Aktivita WF 3 musí být odvozena <xref:System.Workflow.ComponentModel.Activity?displayProperty=nameWithType>od.  
  
- Aktivita WF 3 musí být deklarována jako `public` a nemůže být `abstract`.  
  
- Aktivita WF 3 musí mít veřejný konstruktor bez parametrů.  
  
- Z důvodu omezení typů rozhraní, které <xref:System.Activities.Statements.Interop> může aktivita podporovat, <xref:System.Workflow.Activities.HandleExternalEventActivity> a <xref:System.Workflow.Activities.CallExternalMethodActivity> nelze je použít přímo, ale odvozené aktivity vytvořené pomocí nástroje aktivita komunikace pracovního postupu (WCA. exe) lze použít. Podrobnosti najdete v tématu o programovací model[ Windows Workflow Foundationch nástrojích](https://go.microsoft.com/fwlink/?LinkId=178889).  
  
## <a name="configuring-a-wf-3-activity-within-an-interop-activity"></a>Konfigurace aktivity WF 3 v rámci aktivity spolupráce  
 Aby bylo možné konfigurovat a předávat data do a z aktivity WF 3 v rámci hranice mezi operacemi, jsou vlastnosti aktivity WF 3 a vlastnosti metadat vystaveny <xref:System.Activities.Statements.Interop> aktivitou. Vlastnosti metadat aktivity WF 3 (například <xref:System.Workflow.ComponentModel.Activity.Name%2A>) jsou zpřístupněny <xref:System.Activities.Statements.Interop.ActivityMetaProperties%2A> prostřednictvím kolekce. Toto je kolekce párů název-hodnota používané k definování hodnot vlastností metadat aktivity WF 3. Vlastnost metadat je vlastnost se zálohovaná vlastností závislosti, pro kterou <xref:System.Workflow.ComponentModel.DependencyPropertyOptions.Metadata> je nastaven příznak.  
  
 Vlastnosti aktivity WF 3 jsou zpřístupněny prostřednictvím <xref:System.Activities.Statements.Interop.ActivityProperties%2A> kolekce. Toto je sada párů název-hodnota, kde každá hodnota je <xref:System.Activities.Argument> objekt, který slouží k definování argumentů pro vlastnosti aktivity WF 3. Vzhledem k tomu, že směr vlastnosti aktivity WF 3 nelze odvodit, je každá vlastnost rozdělena jako <xref:System.Activities.InArgument> / <xref:System.Activities.OutArgument> dvojice. V závislosti na použití vlastnosti může být vhodné zadat <xref:System.Activities.InArgument> položku <xref:System.Activities.OutArgument> , položku nebo obojí. Očekávaným názvem <xref:System.Activities.InArgument> položky v kolekci je název vlastnosti definovaný v aktivitě WF 3. Očekávaný název <xref:System.Activities.OutArgument> položky v kolekci je zřetězení názvu vlastnosti a řetězce "out".  
  
## <a name="limitations-of-using-a-wf-3-activity-within-an-interop-activity"></a>Omezení použití aktivity WF 3 v rámci aktivity spolupráce  
 Aktivity WF 3 poskytnuté systémem nemohou být přímo zabaleny do <xref:System.Activities.Statements.Interop> aktivity. Pro některé aktivity WF 3, například <xref:System.Workflow.Activities.DelayActivity>, je to proto, že existuje podobná aktivita WF 4,5. Pro jiné je to proto, že funkce aktivity není podporována. Mnoho aktivit WF 3 poskytovaných systémem se dá použít v rámci pracovních postupů zabalených <xref:System.Activities.Statements.Interop> aktivitou, a to v závislosti na následujících omezeních:  
  
1. <xref:System.ServiceModel.Activities.Send>a <xref:System.ServiceModel.Activities.Receive> nelze použít <xref:System.Activities.Statements.Interop> v aktivitě.  
  
2. <xref:System.Workflow.Activities.WebServiceInputActivity>, <xref:System.Workflow.Activities.WebServiceOutputActivity>a <xref:System.Workflow.Activities.WebServiceFaultActivity> nelzejepoužít<xref:System.Activities.Statements.Interop> v rámci aktivity.  
  
3. <xref:System.Workflow.Activities.InvokeWorkflowActivity>v rámci <xref:System.Activities.Statements.Interop> aktivity nelze použít.  
  
4. <xref:System.Workflow.ComponentModel.SuspendActivity>v rámci <xref:System.Activities.Statements.Interop> aktivity nelze použít.  
  
5. Aktivity související s kompenzací nelze v rámci <xref:System.Activities.Statements.Interop> aktivity použít.  
  
 Existují také určitá specifická chování pro pochopení týkající se používání aktivit WF 3 v rámci <xref:System.Activities.Statements.Interop> aktivity:  
  
1. Aktivity WF 3 obsažené v rámci <xref:System.Activities.Statements.Interop> aktivity jsou inicializovány <xref:System.Activities.Statements.Interop> při spuštění aktivity. V WF 4,5 neexistuje žádná inicializační fáze pro instanci pracovního postupu před jeho provedením.  
  
2. Modul runtime WF 4,5 neřídí stav instance pracovního postupu, když transakce začíná, bez ohledu na to, kde transakce začíná (uvnitř nebo vně <xref:System.Activities.Statements.Interop> aktivity).  
  
3. Záznamy o sledování pro aktivity v rámci <xref:System.Activities.Statements.Interop> aktivity služby WF 3 jsou k dispozici na WF 4,5 sledování účastníků jako <xref:System.Activities.Tracking.InteropTrackingRecord> objektů. <xref:System.Activities.Tracking.InteropTrackingRecord>je odvozený z <xref:System.Activities.Tracking.CustomTrackingRecord>.  
  
4. Vlastní aktivita WF 3 má přístup k datům pomocí front pracovních postupů v prostředí interaktivity stejným způsobem jako v modulu runtime pracovního postupu WF 3. Nevyžadují se žádné změny kódu vlastní aktivity. V hostiteli jsou data zařazená do fronty pracovního postupu WF 3 obnovením <xref:System.Activities.Bookmark>. Název záložky je řetězcový tvar <xref:System.IComparable> názvu fronty pracovního postupu.
