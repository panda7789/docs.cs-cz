---
title: Použití aktivit pracovních postupů .NET Framework 3.0 v rozhraní .NET Framework 4 pomocí aktivity interoperability
ms.date: 03/30/2017
ms.assetid: 71f112ba-abb0-46f7-b05f-a5d2eb9d0c5c
ms.openlocfilehash: de0a0474f0a996ce8c781064f56c03b483ca1bb9
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283197"
---
# <a name="using-net-framework-30-wf-activities-in-net-framework-4-with-the-interop-activity"></a>Použití aktivit pracovních postupů .NET Framework 3.0 v rozhraní .NET Framework 4 pomocí aktivity interoperability
Aktivita <xref:System.Activities.Statements.Interop> je aktivita [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] (WF 4,5), která zabalí aktivitu .NET Framework 3,5 (WF 3,5) v rámci pracovního postupu [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]. Aktivita WF 3 může být jedna koncová aktivita nebo celá struktura aktivit. Spuštění (včetně zrušení a zpracování výjimek) a trvalá aktivita .NET Framework 3,5 nastane v kontextu [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] instance pracovního postupu, která je spuštěna.  
  
> [!NOTE]
> Aktivita <xref:System.Activities.Statements.Interop> se nezobrazuje v sadě nástrojů návrháře pracovních postupů, pokud projekt pracovního postupu nemá nastavenou **cílovou architekturu** na hodnotu **.NET Framework 4,5**.  
  
## <a name="criteria-for-using-a-wf-3-activity-with-an-interop-activity"></a>Kritéria pro použití aktivity WF 3 s aktivitou spolupráce  
 Aby aktivita WF 3 mohla úspěšně běžet v rámci aktivity <xref:System.Activities.Statements.Interop>, musí být splněné následující kritéria:  
  
- Aktivita WF 3 musí být odvozena od <xref:System.Workflow.ComponentModel.Activity?displayProperty=nameWithType>.  
  
- Aktivita WF 3 musí být deklarována jako `public` a nelze ji `abstract`.  
  
- Aktivita WF 3 musí mít veřejný konstruktor bez parametrů.  
  
- Z důvodu omezení typů rozhraní, které může aktivita <xref:System.Activities.Statements.Interop> podporovat, <xref:System.Workflow.Activities.HandleExternalEventActivity> a <xref:System.Workflow.Activities.CallExternalMethodActivity> nelze použít přímo, ale odvozené aktivity vytvořené pomocí nástroje aktivita komunikace pracovního postupu (WCA. exe) lze použít. Podrobnosti najdete v tématu o programovací model[ Windows Workflow Foundationch nástrojích](https://go.microsoft.com/fwlink/?LinkId=178889).  
  
## <a name="configuring-a-wf-3-activity-within-an-interop-activity"></a>Konfigurace aktivity WF 3 v rámci aktivity spolupráce  
 Aby bylo možné konfigurovat a předávat data do a z aktivity WF 3 v rámci hranice mezioperace, vlastnosti aktivity WF 3 a vlastnosti metadat jsou zpřístupněny <xref:System.Activities.Statements.Interop> aktivitou. Vlastnosti metadat aktivity WF 3 (například <xref:System.Workflow.ComponentModel.Activity.Name%2A>) jsou zpřístupněny prostřednictvím kolekce <xref:System.Activities.Statements.Interop.ActivityMetaProperties%2A>. Toto je kolekce párů název-hodnota používané k definování hodnot vlastností metadat aktivity WF 3. Vlastnost metadat je vlastnost se zálohovaná vlastností závislosti, pro kterou je nastaven příznak <xref:System.Workflow.ComponentModel.DependencyPropertyOptions.Metadata>.  
  
 Vlastnosti aktivity WF 3 jsou zpřístupněny prostřednictvím kolekce <xref:System.Activities.Statements.Interop.ActivityProperties%2A>. Toto je sada párů název-hodnota, kde každá hodnota je objekt <xref:System.Activities.Argument>, který slouží k definování argumentů pro vlastnosti aktivity WF 3. Vzhledem k tomu, že směr vlastnosti aktivity WF 3 nelze odvodit, je každá vlastnost rozdělena jako <xref:System.Activities.InArgument>/<xref:System.Activities.OutArgument> páry. V závislosti na využití této vlastnosti může být vhodné zadat <xref:System.Activities.InArgument> položku, <xref:System.Activities.OutArgument> položku nebo obojí. Očekávaným názvem položky <xref:System.Activities.InArgument> v kolekci je název vlastnosti definovaný v aktivitě WF 3. Očekávaný název položky <xref:System.Activities.OutArgument> v kolekci je zřetězení názvu vlastnosti a řetězce "out".  
  
## <a name="limitations-of-using-a-wf-3-activity-within-an-interop-activity"></a>Omezení použití aktivity WF 3 v rámci aktivity spolupráce  
 Aktivity WF 3 poskytnuté systémem nemohou být přímo zabaleny do aktivity <xref:System.Activities.Statements.Interop>. U některých aktivit WF 3, jako je například <xref:System.Workflow.Activities.DelayActivity>, je to proto, že existuje podobná aktivita WF 4,5. Pro jiné je to proto, že funkce aktivity není podporována. Mnoho aktivit služby WF 3 poskytovaných systémem se dá použít v rámci pracovních postupů zabalených aktivitou <xref:System.Activities.Statements.Interop>, a to v závislosti na následujících omezeních:  
  
1. v aktivitě <xref:System.Activities.Statements.Interop> nelze použít <xref:System.ServiceModel.Activities.Send> a <xref:System.ServiceModel.Activities.Receive>.  
  
2. v rámci <xref:System.Activities.Statements.Interop> aktivity nelze použít <xref:System.Workflow.Activities.WebServiceInputActivity>, <xref:System.Workflow.Activities.WebServiceOutputActivity>a <xref:System.Workflow.Activities.WebServiceFaultActivity>.  
  
3. v rámci aktivity <xref:System.Activities.Statements.Interop> nelze použít <xref:System.Workflow.Activities.InvokeWorkflowActivity>.  
  
4. v rámci aktivity <xref:System.Activities.Statements.Interop> nelze použít <xref:System.Workflow.ComponentModel.SuspendActivity>.  
  
5. Aktivity související s kompenzací nelze použít v rámci aktivity <xref:System.Activities.Statements.Interop>.  
  
 Existují také určitá specifická chování pro pochopení týkající se používání aktivit WF 3 v rámci <xref:System.Activities.Statements.Interop> aktivity:  
  
1. Aktivity WF 3 obsažené v aktivitě <xref:System.Activities.Statements.Interop> jsou inicializovány při spuštění aktivity <xref:System.Activities.Statements.Interop>. V WF 4,5 neexistuje žádná inicializační fáze pro instanci pracovního postupu před jeho provedením.  
  
2. Modul runtime WF 4,5 neřídí stav instance pracovního postupu, když transakce začíná, bez ohledu na to, kde transakce začíná (uvnitř nebo vně aktivity <xref:System.Activities.Statements.Interop>).  
  
3. Záznamy o sledování pro aktivity v rámci aktivity <xref:System.Activities.Statements.Interop> jsou k dispozici na WF 4,5 sledování účastníků jako <xref:System.Activities.Tracking.InteropTrackingRecord> objektů. <xref:System.Activities.Tracking.InteropTrackingRecord> je odvozená <xref:System.Activities.Tracking.CustomTrackingRecord>.  
  
4. Vlastní aktivita WF 3 má přístup k datům pomocí front pracovních postupů v prostředí interaktivity stejným způsobem jako v modulu runtime pracovního postupu WF 3. Nevyžadují se žádné změny kódu vlastní aktivity. V hostiteli jsou data zařazená do fronty pracovního postupu WF 3 obnovením <xref:System.Activities.Bookmark>. Název záložky je formát řetězce názvu fronty pracovního postupu <xref:System.IComparable>.
