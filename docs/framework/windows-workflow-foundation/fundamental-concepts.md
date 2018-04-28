---
title: Základní Windows Workflow koncepty
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0e930e80-5060-45d2-8a7a-95c0690105d4
caps.latest.revision: 27
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: faeb05045049e9a53babf754f1ec058c6aac2f05
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="fundamental-windows-workflow-concepts"></a>Základní Windows Workflow koncepty
Vývoj pro pracovní postup v [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] používá koncepty, které může být nový někteří vývojáři. Toto téma popisuje některé koncepty a jak jsou implementované.  
  
## <a name="workflows-and-activities"></a>Pracovní postupy a aktivity  
 Pracovní postup je strukturovaných sadu akcí modelů proces. Každá akce v pracovním postupu je modelovaná jako aktivita. Hostitel komunikuje s pracovního postupu pomocí <xref:System.Activities.WorkflowInvoker> pro vyvolání pracovního postupu, jako by šlo metodu, <xref:System.Activities.WorkflowApplication> explicitní kontrolu nad spuštění instance jednoho pracovního postupu, a <xref:System.ServiceModel.WorkflowServiceHost> pro interakce na základě zpráv v s více instancemi scénáře. Protože kroky pracovního postupu jsou definovány jako hierarchie aktivit, nejhornější aktivity v hierarchii můžete tyto definovat samotného pracovního postupu. Tento model hierarchie přebírá místo explicitní `SequentialWorkflow` a `StateMachineWorkflow` třídy z předchozích verzí. Aktivity sami jsou vyvinutý jako kolekce jiných aktivit (pomocí <xref:System.Activities.Activity> třída jako základní, obvykle definovány pomocí jazyka XAML) nebo jsou vytvořené pomocí vlastním <xref:System.Activities.CodeActivity> třídy, která můžete použít modul runtime pro přístup k datům, nebo pomocí <xref:System.Activities.NativeActivity> třída, která zpřístupňuje šířky modulu runtime pracovního postupu autorovi aktivity. Aktivity vyvinuté pomocí <xref:System.Activities.CodeActivity> a <xref:System.Activities.NativeActivity> se vytváří pomocí standardem CLR jazyků, například C#.  
  
## <a name="activity-data-model"></a>Aktivita datový Model  
 Aktivity ukládat a sdílet data pomocí typy uvedené v následující tabulce.  
  
|||  
|-|-|  
|Proměnná|Ukládá data v aktivitě.|  
|Argument|Přesouvá data do a z aktivity.|  
|Výraz|Aktivitu se zvýšenými oprávněními návratovou hodnotu, která používá v argumentu vazby.|  
  
## <a name="workflow-runtime"></a>Modulu Runtime pracovního postupu  
 Modul runtime pracovního postupu je prostředí, ve kterém se spustit pracovní postupy. <xref:System.Activities.WorkflowInvoker> je nejjednodušší způsob, jak spustit pracovní postup. Hostitel používá <xref:System.Activities.WorkflowInvoker> pro následující:  
  
-   Chcete-li synchronně vyvolat pracovního postupu.  
  
-   K zadání nebo načíst výstup z pracovního postupu.  
  
-   Chcete-li přidat rozšíření má být používána aktivity.  
  
 <xref:System.Activities.ActivityInstance> je bezpečné pro přístup z více vláken proxy serverem, který hostitelů můžete použít k interakci s modulem runtime. Hostitel používá <xref:System.Activities.ActivityInstance> pro následující:  
  
-   Získat instanci její vytvoření nebo načtení z úložiště instance.  
  
-   Oznámení životního cyklu událostí instance.  
  
-   K řízení provádění pracovního postupu.  
  
-   K zadání nebo načíst výstup z pracovního postupu.  
  
-   Signal pokračování pracovní postup a předejte hodnoty do pracovního postupu.  
  
-   Chcete-li zachovat data pracovního postupu.  
  
-   Chcete-li přidat rozšíření má být používána aktivity.  
  
 Aktivity získat přístup k prostředí runtime pracovního postupu pomocí odpovídající <xref:System.Activities.ActivityContext> odvozené třídy, jako například <xref:System.Activities.NativeActivityContext> nebo <xref:System.Activities.CodeActivityContext>. To používají pro překlad argumenty a proměnné pro plánování podřízené aktivity a mnoha dalším účelům.  
  
## <a name="services"></a>Služby  
 Pracovní postupy poskytují přirozené způsob, jak implementovat a získat přístup ke službám volně vázány pomocí zasílání zpráv aktivit. Zasílání zpráv aktivity jsou postaveny na [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] a primární mechanizmus použít k získání dat do a z pracovního postupu. Můžete vytvořit zasílání zpráv aktivity společně pro modelování jakýkoli druh vzorce výměny zpráv, které chcete. Další informace najdete v tématu najdete v části [zasílání zpráv aktivity](../../../docs/framework/wcf/feature-details/messaging-activities.md). Služby pracovních postupů jsou hostované pomocí <xref:System.ServiceModel.Activities.WorkflowServiceHost> třídy. Další informace najdete v tématu [přehled hostování služeb pracovních postupů](../../../docs/framework/wcf/feature-details/hosting-workflow-services-overview.md). [!INCLUDE[crabout](../../../includes/crabout-md.md)] pracovní postup služby najdete v tématu [služeb pracovních postupů](../../../docs/framework/wcf/feature-details/workflow-services.md)  
  
## <a name="persistence-unloading-and-long-running-workflows"></a>Trvalost, uvolnění a dlouhodobé pracovních postupů  
 Pracovní postup prostředí Windows zjednodušuje vytváření dlouhodobé reaktivní programy tím, že poskytuje:  
  
-   Aktivity, které přístup k externí vstup.  
  
-   Schopnost vytvářet <xref:System.Activities.Bookmark> objekty, které lze obnovit pomocí naslouchací proces hostitele.  
  
-   Možnost zachovat data pracovního postupu a uvolnění pracovního postupu a pak znovu načíst a znovu aktivovat pracovní postup v reakci na obnovení <xref:System.Activities.Bookmark> objekty v určitý pracovní postup.  
  
 Pracovní postup nepřetržitě provádí aktivity, dokud nejsou žádné další aktivity nebo dokud všechny aktuálně prováděné aktivity, které čekají na vstup. V tomto stavu pozdější nečinný pracovního postupu. Je běžné pro hostitele se uvolnit pracovní postupy, které šly nečinnosti a načíst znovu, je pro pokračování v provádění při zpráva dorazí. <xref:System.ServiceModel.Activities.WorkflowServiceHost> poskytuje funkce pro tuto funkci a poskytuje zásadu extensible uvolnění. Pro bloky spuštění, které používají data o stavu volatile nebo další data, která nelze nastavit jako trvalý, můžete označit aktivitu na hostitele, že by neměl být trvalé pomocí <xref:System.Activities.NoPersistHandle>. Pracovní postup můžete také explicitně zachovat svá data do trvalého úložiště média pomocí <xref:System.Activities.Statements.Persist> aktivity.
