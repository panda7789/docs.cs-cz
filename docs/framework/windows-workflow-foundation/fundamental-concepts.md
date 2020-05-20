---
title: Základní koncepce Windows Workflow
description: Tento článek popisuje některé koncepty vývoje pracovního postupu v .NET Framework 4.6.1, které nemusí být pro některé vývojáře známé.
ms.date: 03/30/2017
ms.assetid: 0e930e80-5060-45d2-8a7a-95c0690105d4
ms.openlocfilehash: 07498241280191fb62a35a559a3391f7148c05b9
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2020
ms.locfileid: "83419886"
---
# <a name="fundamental-windows-workflow-concepts"></a>Základní koncepce Windows Workflow
Vývoj pracovních postupů v nástroji [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] používá koncepty, které mohou být pro některé vývojáře novinkou. Toto téma popisuje některé z konceptů a způsob jejich implementace.  
  
## <a name="workflows-and-activities"></a>Pracovní postupy a aktivity  
 Pracovní postup je strukturovaná kolekce akcí, které modelují proces. Každá akce v pracovním postupu je modelována jako aktivita. Hostitel spolupracuje s pracovním postupem pomocí <xref:System.Activities.WorkflowInvoker> pro vyvolání pracovního postupu, jako by šlo o metodu, <xref:System.Activities.WorkflowApplication> pro explicitní kontrolu nad prováděním jedné instance pracovního postupu a <xref:System.ServiceModel.WorkflowServiceHost> pro interakce založené na zprávách ve scénářích s více instancemi. Vzhledem k tomu, že kroky pracovního postupu jsou definovány jako hierarchie aktivit, může být první aktivita v hierarchii určena k definování samotného pracovního postupu. Tento model hierarchie přebírá místo explicitního `SequentialWorkflow` a `StateMachineWorkflow` třídy z předchozích verzí. Aktivity samy jsou vyvíjeny jako kolekce jiných aktivit (za použití <xref:System.Activities.Activity> třídy jako základní, obvykle definované pomocí XAML) nebo jsou vlastní vytvořené pomocí <xref:System.Activities.CodeActivity> třídy, která může použít modul runtime pro přístup k datům nebo pomocí <xref:System.Activities.NativeActivity> třídy, která zpřístupňuje míru modulu runtime pracovního postupu pro autora aktivity. Aktivity vyvinuté pomocí <xref:System.Activities.CodeActivity> a <xref:System.Activities.NativeActivity> jsou vytvářeny pomocí jazyků kompatibilních s modulem CLR, jako je C#.  
  
## <a name="activity-data-model"></a>Datový model aktivity  
 Aktivity ukládají a sdílejí data pomocí typů uvedených v následující tabulce.  
  
|||  
|-|-|  
|Proměnná|Ukládá data do aktivity.|  
|Argument|Přesune data do aktivity a ven z ní.|  
|Výraz|Aktivita se zvýšenou návratovou hodnotou použitou v vazbách argumentů.|  
  
## <a name="workflow-runtime"></a>Modul runtime pracovního postupu  
 Modul runtime pracovního postupu je prostředí, ve kterém se pracovní postupy spouštějí. <xref:System.Activities.WorkflowInvoker>je nejjednodušší způsob, jak spustit pracovní postup. Hostitel používá <xref:System.Activities.WorkflowInvoker> pro následující:  
  
- K synchronnímu vyvolání pracovního postupu.  
  
- Zadání vstupu do nebo načtení výstupu z pracovního postupu.  
  
- Pro přidání rozšíření, která budou používána aktivitami.  
  
 <xref:System.Activities.ActivityInstance>je proxy server bezpečný pro přístup z více vláken, který můžou hostitelé použít k interakci s modulem runtime. Hostitel používá <xref:System.Activities.ActivityInstance> pro následující:  
  
- Pro získání instance jejich vytvořením nebo načtením z úložiště instance.  
  
- Oznámení o událostech životního cyklu instance.  
  
- Pro řízení provádění pracovního postupu.  
  
- Zadání vstupu do nebo načtení výstupu z pracovního postupu.  
  
- K signalizaci pokračování workflowu a předání hodnot do pracovního postupu.  
  
- Pro zachování dat pracovního postupu.  
  
- Pro přidání rozšíření, která budou používána aktivitami.  
  
 Aktivity získávají přístup k běhovému prostředí pracovního postupu pomocí příslušné <xref:System.Activities.ActivityContext> odvozené třídy, jako je například <xref:System.Activities.NativeActivityContext> nebo <xref:System.Activities.CodeActivityContext> . Používají se k překladu argumentů a proměnných, k plánování podřízených aktivit a k mnoha dalším účelům.  
  
## <a name="services"></a>Služby  
 Pracovní postupy představují přirozený způsob, jak implementovat a přistupovat k volně vázaným službám, a to pomocí aktivit zasílání zpráv. Aktivity zasílání zpráv jsou postaveny na WCF a jsou primárním mechanismem, který slouží k získávání dat do a z pracovního postupu. Můžete vytvářet aktivity zasílání zpráv dohromady a modelovat jakýkoli druh způsobu výměny zpráv, který chcete. Další informace najdete v tématu [aktivity zasílání zpráv](../wcf/feature-details/messaging-activities.md). Služby pracovních postupů jsou hostovány pomocí <xref:System.ServiceModel.Activities.WorkflowServiceHost> třídy. Další informace najdete v tématu věnovaném [hostování služby pracovního postupu](../wcf/feature-details/hosting-workflow-services-overview.md). Další informace o službách pracovních postupů najdete v tématu [služby pracovních postupů](../wcf/feature-details/workflow-services.md) .  
  
## <a name="persistence-unloading-and-long-running-workflows"></a>Trvalá, uvolňování a dlouhotrvající pracovní postupy  
 Pracovní postup Windows zjednodušuje vytváření dlouhodobě spuštěných reaktivních programů tím, že poskytuje:  
  
- Aktivity, které přistupují k externímu vstupu.  
  
- Možnost vytvářet <xref:System.Activities.Bookmark> objekty, které mohou být obnoveny pomocí naslouchacího procesu hostitele.  
  
- Možnost zachovat data pracovního postupu a uvolnit pracovní postup a pak znovu načíst a znovu aktivovat pracovní postup v reakci na obnovení <xref:System.Activities.Bookmark> objektů v konkrétním pracovním postupu.  
  
 Pracovní postup nepřetržitě spouští aktivity, dokud neexistují žádné další aktivity ke spuštění nebo dokud všechny aktuálně prováděné aktivity nečekají na vstup. V tomto druhém stavu je pracovní postup nečinný. Je běžné, že hostitel odvolá pracovní postupy, které prošly nečinné, a znovu je načte, aby bylo možné pokračovat v provádění při doručení zprávy. <xref:System.ServiceModel.Activities.WorkflowServiceHost>poskytuje funkce pro tuto funkci a poskytuje rozšiřitelnou zásadu uvolnění. Pro bloky spuštění, které používají nestálý stavová data nebo jiná data, která nelze zachovat, může aktivita indikovat hostiteli, že by neměl být trvale uložen pomocí <xref:System.Activities.NoPersistHandle> . Pracovní postup může také explicitně uchovávat data na trvalém paměťovém médiu pomocí <xref:System.Activities.Statements.Persist> aktivity.
