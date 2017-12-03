---
title: "Přehled pracovního postupu systému Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fc44adbe-1412-49ae-81af-0298be44aae6
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b74ecc3363e84d006d82ecb14accbf40de7e2738
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="windows-workflow-overview"></a>Přehled pracovního postupu systému Windows
Pracovní postup je sada elementární jednotek nazývaných *aktivity* , jsou uloženy jako model, který popisuje reálného procesu. Pracovní postupy zadejte označení pořadí provádění a závislé vztahy mezi částí krátké nebo dlouhotrvající práce. Tento pracovní projdou modelu od začátku do konce a aktivity mohou být prováděny, uživatelé nebo funkce systému.  
  
## <a name="workflow-run-time-engine"></a>Modul runtime pracovního postupu  
 Všechny spuštěné instance pracovního postupu je vytvářené a udržované pomocí modul runtime v procesu, musí hostitelský proces komunikuje prostřednictvím jednoho z následujících akcí:  
  
-   A <xref:System.Activities.WorkflowInvoker>, který volá pracovní postup jako metodu.  
  
-   A <xref:System.Activities.WorkflowApplication> explicitní kontrolu nad spuštění instance jednoho pracovního postupu.  
  
-   A <xref:System.ServiceModel.WorkflowServiceHost> pro interakce na základě zpráv ve scénářích s více instancemi.  
  
 Každá z těchto tříd zabalí na core runtime aktivity vyjádřené <xref:System.Activities.ActivityInstance> zodpovědná za spuštění aktivity. Může být několik <xref:System.Activities.ActivityInstance> objektů v rámci současné spuštění domény aplikace.  
  
 Každý z předchozí interakce objektů tři hostitele je vytvořen ze stromu aktivit, které jsou označovány jako program pracovního postupu. Pomocí těchto typů nebo vlastní hostitele, který zabalí <xref:System.Activities.ActivityInstance>, pracovní postupy můžete spustit v rámci libovolného procesu systému Windows včetně konzolové aplikace založené na formulářích aplikace služby systému Windows, [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] weby, a [!INCLUDE[indigo1](../../../includes/indigo1-md.md)]služby.  
  
 ![Součásti pracovního postupu v procesu hostitele](../../../docs/framework/windows-workflow-foundation/media/44c79d1d-178b-4487-87ed-3e33015a3842.gif "44c79d1d-178b-4487-87ed-3e33015a3842")  
Součásti pracovního postupu v procesu hostitele  
  
## <a name="interaction-between-workflow-components"></a>Interakce mezi součástmi pracovního postupu  
 Následující diagram ukazuje, jak součásti pracovního postupu vzájemné interakce.  
  
 ![Pracovní postup interakce](../../../docs/framework/windows-workflow-foundation/media/workflowinteraction.gif "WorkflowInteraction")  
  
 Na předchozím obrázku <xref:System.Activities.WorkflowInvoker.Invoke%2A> metodu <xref:System.Activities.WorkflowInvoker> třída se používá k vyvolání několik instancí pracovního postupu. <xref:System.Activities.WorkflowInvoker>slouží pro prosté pracovní postupy, které nepotřebují správy z hostitele; pracovní postupy, které je třeba Správa z hostitele (například <xref:System.Activities.Bookmark> obnovení) je třeba spustit pomocí <xref:System.Activities.WorkflowApplication.Run%2A> místo. Není potřeba čekat na jednu instanci pracovního postupu k dokončení před vyvoláním modul runtime podporuje současně spuštěno více instancí pracovního postupu.  Vyvolá pracovní postupy jsou následující:  
  
-   A <xref:System.Activities.Statements.Sequence> aktivity, která obsahuje <xref:System.Activities.Statements.WriteLine> podřízené aktivity. A <xref:System.Activities.Variable> nadřazené aktivity je vázána na <xref:System.Activities.InArgument> podřízené aktivity. [!INCLUDE[crabout](../../../includes/crabout-md.md)]na proměnné, argumentů a vazbu, najdete v části [proměnné a argumenty](../../../docs/framework/windows-workflow-foundation/variables-and-arguments.md).  
  
-   Vlastní aktivity volá `ReadLine`. <xref:System.Activities.OutArgument> z `ReadLine` aktivity se vrátí do volající <xref:System.Activities.WorkflowInvoker.Invoke%2A> metoda.  
  
-   Vlastní aktivity, která je odvozena z <xref:System.Activities.CodeActivity> abstraktní třídy. <xref:System.Activities.CodeActivity> Můžete přístup k funkcím runtime (například sledování a vlastnosti) pomocí <xref:System.Activities.CodeActivityContext> která je k dispozici jako parametr funkce <xref:System.Activities.CodeActivity.Execute%2A> metoda. [!INCLUDE[crabout](../../../includes/crabout-md.md)]Tyto funkce běhové najdete [pracovního postupu pro sledování a trasování](../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md) a [vlastnosti spuštění pracovního postupu](../../../docs/framework/windows-workflow-foundation/workflow-execution-properties.md).  
  
## <a name="see-also"></a>Viz také  
 [BizTalk Server 2006 nebo WF? Volba správného pracovního postupu nástroje pro svůj projekt](http://go.microsoft.com/fwlink/?LinkId=154901)
