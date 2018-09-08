---
title: Přehled Windows Workflow
ms.date: 03/30/2017
ms.assetid: fc44adbe-1412-49ae-81af-0298be44aae6
ms.openlocfilehash: a516f454abc81ae8f6f1c15c815fe2b671ecd98f
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44196787"
---
# <a name="windows-workflow-overview"></a>Přehled Windows Workflow
Pracovní postup je sada elemental jednotky nazvané *aktivity* , které jsou uloženy jako model, který popisuje proces reálného světa. Pracovní postupy umožňují popsat pořadí spuštění a závislé vztahy mezi částmi krátkodobé nebo dlouho probíhající práce. Tato práce prochází modelu od začátku do konce a aktivity mohou být prováděny osobami nebo funkcemi systému.  
  
## <a name="workflow-run-time-engine"></a>Modul runtime pracovního postupu  
 Každou spuštěnou instanci pracovního postupu se vytvářejí a udržují modul runtime v procesu hostitelský proces komunikuje prostřednictvím jednoho z následujících akcí:  
  
-   A <xref:System.Activities.WorkflowInvoker>, která vyvolá pracovní postup jako metodu.  
  
-   A <xref:System.Activities.WorkflowApplication> explicitní kontrolu nad tím provádění instance jednoho pracovního postupu.  
  
-   A <xref:System.ServiceModel.WorkflowServiceHost> založenou na zprávách interakcí ve scénářích s více instancemi.  
  
 Každá z těchto tříd obtéká modul runtime aktivity core vyjádřené <xref:System.Activities.ActivityInstance> zodpovědná za spuštění aktivity. Může být několik <xref:System.Activities.ActivityInstance> objektů v rámci domény aplikace spuštěny souběžně.  
  
 Každý z předchozí tři hostitele objektů interakce je vytvořen ze stromu aktivit, které jsou uvedené jako aplikace pracovního postupu. Pomocí těchto typů nebo vlastního hostitele, která obaluje <xref:System.Activities.ActivityInstance>, pracovní postupy mohou být provedeny uvnitř jakýkoli proces Windows včetně konzolové aplikace založené na formulářích aplikací, služeb Windows [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] webové servery a (Windows Communication Foundation Služby WCF).  
  
 ![Komponenty pracovní postup v hostitelském procesu](../../../docs/framework/windows-workflow-foundation/media/44c79d1d-178b-4487-87ed-3e33015a3842.gif "44c79d1d-178b-4487-87ed-3e33015a3842")  
Komponenty pracovní postup v hostitelském procesu  
  
## <a name="interaction-between-workflow-components"></a>Interakce mezi komponentami pracovního postupu  
 Následující diagram ukazuje, jak komponenty pracovního postupu komunikovat mezi sebou.  
  
 ![Pracovní postup interakce](../../../docs/framework/windows-workflow-foundation/media/workflowinteraction.gif "WorkflowInteraction")  
  
 Na předchozím obrázku <xref:System.Activities.WorkflowInvoker.Invoke%2A> metodu <xref:System.Activities.WorkflowInvoker> třída se používá pro vyvolání několika instancí pracovních postupů. <xref:System.Activities.WorkflowInvoker> se používá pro zjednodušené pracovní postupy, které nepotřebují správy z hostitele; pracovní postupy, které je třeba Správa z hostitele (například <xref:System.Activities.Bookmark> obnovení) je třeba spustit pomocí <xref:System.Activities.WorkflowApplication.Run%2A> místo. Není to nutné čekat pro jednu instanci pracovního postupu k dokončení před vyvoláním modul runtime podporuje spuštění více instancí pracovního postupu současně.  Vyvolá pracovní postupy jsou následující:  
  
-   A <xref:System.Activities.Statements.Sequence> aktivitu, která obsahuje <xref:System.Activities.Statements.WriteLine> podřízené aktivity. A <xref:System.Activities.Variable> nadřazené aktivity je vázána na <xref:System.Activities.InArgument> podřízené aktivity. Další informace o proměnných, argumentů a vazbu, naleznete v tématu [proměnné a argumenty](../../../docs/framework/windows-workflow-foundation/variables-and-arguments.md).  
  
-   Volá se, vlastní aktivita `ReadLine`. <xref:System.Activities.OutArgument> z `ReadLine` aktivity je vrácena volající <xref:System.Activities.WorkflowInvoker.Invoke%2A> metody.  
  
-   Vlastní aktivitu, která je odvozena z <xref:System.Activities.CodeActivity> abstraktní třídy. <xref:System.Activities.CodeActivity> Můžete přístup k funkcím za běhu (například sledování a vlastnosti) pomocí <xref:System.Activities.CodeActivityContext> , který je k dispozici jako parametr <xref:System.Activities.CodeActivity.Execute%2A> metoda. Další informace o těchto funkcích za běhu, naleznete v tématu [pracovního postupu pro sledování a trasování](../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md) a [běhové vlastnosti pracovního postupu](../../../docs/framework/windows-workflow-foundation/workflow-execution-properties.md).  
  
## <a name="see-also"></a>Viz také  
 [BizTalk Server 2006 nebo pracovního postupu? Volba správného pracovního postupu nástroje pro váš projekt](https://go.microsoft.com/fwlink/?LinkId=154901)
