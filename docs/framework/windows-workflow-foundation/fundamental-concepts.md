---
title: Koncepty pracovního postupu základní Windows
ms.date: 03/30/2017
ms.assetid: 0e930e80-5060-45d2-8a7a-95c0690105d4
ms.openlocfilehash: ce17e5436ecff1937db605450d187184df9104a5
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57703410"
---
# <a name="fundamental-windows-workflow-concepts"></a>Koncepty pracovního postupu základní Windows
Pracovní postup vývoje v [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] používá koncepty, které mohou být novým někteří vývojáři. Toto téma popisuje některé koncepty a jak jsou implementované.  
  
## <a name="workflows-and-activities"></a>Pracovních postupů a aktivit  
 Pracovní postup je strukturovaných kolekci akcí, který modeluje procesu. Všechny akce v pracovním postupu je modelovaná jako aktivita. Hostitel komunikuje s pracovním postupem s použitím <xref:System.Activities.WorkflowInvoker> pro volání pracovního postupu, jako by šlo o metodu, <xref:System.Activities.WorkflowApplication> pro explicitní kontrolu nad spouštěním instanci jednoho pracovního postupu a <xref:System.ServiceModel.WorkflowServiceHost> pro založenou na zprávách interakce ve více instancemi scénáře. Protože krokům pracovního postupu jsou definovány jako hierarchii aktivit, mohou být označeny nejvyšší aktivity v hierarchii k definování samotného pracovního postupu. Tento model hierarchie zaujímá místo explicitního `SequentialWorkflow` a `StateMachineWorkflow` třídy z předchozí verze. Aktivity samotných jsou vyvíjeny jako kolekce jiných aktivit (pomocí <xref:System.Activities.Activity> třídy jako základ, většinou definovaný pomocí XAML) nebo jsou vytvořené s použitím vlastní <xref:System.Activities.CodeActivity> třídy, které můžete použít modul runtime pro přístup k datům, nebo <xref:System.Activities.NativeActivity> třídu, která zveřejňuje škálu modulu runtime pracovního postupu k autorem aktivity. Aktivity vyvinuté pomocí <xref:System.Activities.CodeActivity> a <xref:System.Activities.NativeActivity> jsou vytvořeny pomocí jazyků kompatibilních s CLR, jako je C#.  
  
## <a name="activity-data-model"></a>Aktivita datového modelu  
 Aktivity ukládání a sdílení dat s použitím typů uvedené v následující tabulce.  
  
|||  
|-|-|  
|Proměnná|Ukládá data v nějaké aktivitě.|  
|Argument|Přesune data do a z aktivity.|  
|Výraz|Aktivita s se zvýšenými oprávněními návratovou hodnotu, která je použita ve vazbách argument.|  
  
## <a name="workflow-runtime"></a>Modul Runtime pracovního postupu  
 Modul runtime pracovního postupu je prostředí, ve kterém spuštění pracovních postupů. <xref:System.Activities.WorkflowInvoker> je nejjednodušší způsob, jak spustit pracovní postup. Hostitel používá <xref:System.Activities.WorkflowInvoker> pro následující:  
  
-   Chcete-li synchronně vyvolat pracovní postup.  
  
-   Chcete-li k zadání nebo načíst výstup z pracovního postupu.  
  
-   Přidání rozšíření používané aktivity.  
  
 <xref:System.Activities.ActivityInstance> je bezpečná pro vlákno proxy server, který hostitelů můžete využít při interakci s modulem runtime. Hostitel používá <xref:System.Activities.ActivityInstance> pro následující:  
  
-   Získat instanci po jeho vytvoření nebo načtení z úložiště instancí.  
  
-   Chcete-li oznámení o událostech životního cyklu instance.  
  
-   K řízení provádění pracovního postupu.  
  
-   Chcete-li k zadání nebo načíst výstup z pracovního postupu.  
  
-   Signalizuje, že pokračování pracovního postupu a předat hodnoty do pracovního postupu.  
  
-   Chcete-li zachovat data pracovního postupu.  
  
-   Přidání rozšíření používané aktivity.  
  
 Aktivity získat přístup k prostředí modulu runtime pracovního postupu pomocí vhodné <xref:System.Activities.ActivityContext> odvozené třídy, jako například <xref:System.Activities.NativeActivityContext> nebo <xref:System.Activities.CodeActivityContext>. To používají pro překlad proměnných a argumentů pro plánování podřízené aktivity a pro celou řadu dalších účelů.  
  
## <a name="services"></a>Služby  
 Pracovní postupy poskytují přirozený způsob, jak implementovat a přístup ke službám volně spárované pomocí aktivit zasílání zpráv. Zasílání zpráv aktivity jsou postavené na WCF a jsou primární mechanismus, který se používá k získání dat do a z pracovního postupu. Můžete vytvořit zasílání zpráv aktivity dohromady a modelovat jakýkoli druh vzoru výměny zpráv, který si přejete. Další informace najdete v tématu [zasílání zpráv aktivity](../wcf/feature-details/messaging-activities.md). Služby pracovních postupů jsou hostované pomocí <xref:System.ServiceModel.Activities.WorkflowServiceHost> třídy. Další informace najdete v tématu [přehled hostování služeb pracovních postupů](../wcf/feature-details/hosting-workflow-services-overview.md). Další informace o službách pracovního postupu najdete v části [služeb pracovních postupů](../wcf/feature-details/workflow-services.md)  
  
## <a name="persistence-unloading-and-long-running-workflows"></a>Trvalost, uvolňování a dlouhotrvající pracovní postupy  
 Pracovní postup Windows zjednodušuje vytváření reaktivních aplikací dlouho běžící tím, že poskytuje:  
  
-   Aktivity, které přistupují k externí vstup.  
  
-   Schopnost vytvářet <xref:System.Activities.Bookmark> objekty, které lze obnovit naslouchací proces hostitele.  
  
-   Možnost zachovat data pracovního postupu a uvolnění pracovního postupu a pak znovu načíst a znovu aktivovat pracovní postup v reakci na opětovné <xref:System.Activities.Bookmark> objektů v určitý pracovní postup.  
  
 Pracovní postup aktivity provádí nepřetržitě, dokud nejsou žádné další aktivity ke spuštění nebo dokud se všechny aktuálně prováděné činnosti jsou čekání na vstup. V tomto druhém stavu pracovního postupu nečinnosti. Je běžné, že hostitel uvolnit pracovní postupy, které přešly nečinnosti a znovu načte moct pokračovat v provádění při přijetí zprávy dorazí. <xref:System.ServiceModel.Activities.WorkflowServiceHost> poskytuje funkce pro tuto funkci a zásadu extensible uvolnění z paměti. Pro bloky spuštění, které používají data o stavu volatile nebo jiná data, která nelze nastavit jako trvalý, můžete označit aktivitu na hostitele, že by neměl být trvalé pomocí <xref:System.Activities.NoPersistHandle>. Pracovní postup můžete také explicitně zachovat svoje data do trvalého úložiště média s použitím <xref:System.Activities.Statements.Persist> aktivity.
