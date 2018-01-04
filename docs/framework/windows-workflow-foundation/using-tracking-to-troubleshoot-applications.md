---
title: "Řešení potíží s aplikací pomocí sledování"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8851adde-c3c2-4391-9523-d8eb831490af
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bb8971c344ff24120b5f85dceb518b0944bd5feb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="using-tracking-to-troubleshoot-applications"></a><span data-ttu-id="9f64d-102">Řešení potíží s aplikací pomocí sledování</span><span class="sxs-lookup"><span data-stu-id="9f64d-102">Using Tracking to Troubleshoot Applications</span></span>
[!INCLUDE[wf](../../../includes/wf-md.md)]<span data-ttu-id="9f64d-103">umožňuje sledovat informace týkající se pracovní postup uvést podrobnosti do provádění [!INCLUDE[wf2](../../../includes/wf2-md.md)] aplikaci nebo službě.</span><span class="sxs-lookup"><span data-stu-id="9f64d-103"> enables you to track workflow-related information to give details into the execution of a [!INCLUDE[wf2](../../../includes/wf2-md.md)] application or service.</span></span> [!INCLUDE[wf2](../../../includes/wf2-md.md)]<span data-ttu-id="9f64d-104">hostitelé dokážou zachytit pracovního postupu události během zpracování instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="9f64d-104"> hosts are able to capture workflow events during the execution of a workflow instance.</span></span> <span data-ttu-id="9f64d-105">Pokud pracovní postup generuje chyby nebo výjimky, můžete použít [!INCLUDE[wf2](../../../includes/wf2-md.md)] sledování podrobnosti o řešení problémů s jeho zpracování.</span><span class="sxs-lookup"><span data-stu-id="9f64d-105">If your workflow generates faults or exceptions, you can use the [!INCLUDE[wf2](../../../includes/wf2-md.md)] tracking details to troubleshooting its processing.</span></span>  
  
## <a name="troubleshooting-a-wf-using-wf-tracking"></a><span data-ttu-id="9f64d-106">Řešení potíží WF pomocí sledování WF</span><span class="sxs-lookup"><span data-stu-id="9f64d-106">Troubleshooting a WF using WF Tracking</span></span>  
 <span data-ttu-id="9f64d-107">Ke zjištění chyb v rámci zpracování [!INCLUDE[wf2](../../../includes/wf2-md.md)] aktivita, můžete povolit sledování s sledování profil, který se dotazuje na <xref:System.Activities.Tracking.ActivityStateRecord> v chybném stavu.</span><span class="sxs-lookup"><span data-stu-id="9f64d-107">To detect faults within the processing of a [!INCLUDE[wf2](../../../includes/wf2-md.md)] activity, you can enable tracking with a tracking profile that queries for an <xref:System.Activities.Tracking.ActivityStateRecord> with the state of Faulted.</span></span> <span data-ttu-id="9f64d-108">Odpovídající dotaz je zadána v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="9f64d-108">The corresponding query is specified in the following code.</span></span>  
  
```xml  
<activityStateQueries>  
              <activityStateQuery activityName="*">  
                <states>  
                  <state name="Faulted" />  
                </states>  
              </activityStateQuery>  
 </activityStateQueries>  
```  
  
 <span data-ttu-id="9f64d-109">Pokud je chybu rozšířen a zpracovávaných v rámci obslužná rutina chyb (například <xref:System.Activities.Statements.TryCatch> aktivity) to lze zjistit pomocí <xref:System.Activities.Tracking.FaultPropagationRecord>.</span><span class="sxs-lookup"><span data-stu-id="9f64d-109">If a fault is propagated and handled within a fault handler (such as a <xref:System.Activities.Statements.TryCatch> activity) this can be detected using a <xref:System.Activities.Tracking.FaultPropagationRecord>.</span></span> <span data-ttu-id="9f64d-110"><xref:System.Activities.Tracking.FaultPropagationRecord> Označuje zdrojové aktivity poruchy a název obslužné rutiny selhání.</span><span class="sxs-lookup"><span data-stu-id="9f64d-110">The <xref:System.Activities.Tracking.FaultPropagationRecord> indicates the source activity of the fault and the name of the fault handler.</span></span> <span data-ttu-id="9f64d-111"><xref:System.Activities.Tracking.FaultPropagationRecord> Obsahuje podrobné informace o chybě v podobě zásobník výjimek poruchy. Dotaz pro přihlášení k odběru pro <xref:System.Activities.Tracking.FaultPropagationRecord> je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="9f64d-111">The <xref:System.Activities.Tracking.FaultPropagationRecord> contains fault details in form of the exception stack for the fault.The query to subscribe for a <xref:System.Activities.Tracking.FaultPropagationRecord> is shown in the following example.</span></span>  
  
```xml  
<faultPropagationQueries>  
              <faultPropagationQuery faultSourceActivityName ="*" faultHandlerActivityName="*"/>  
 </faultPropagationQueries>  
```  
  
 <span data-ttu-id="9f64d-112">Pokud není chybu zpracovávaných v rámci pracovního postupu, který je výsledkem k neošetřené výjimce v instanci pracovního postupu a instance pracovního postupu byla přerušena.</span><span class="sxs-lookup"><span data-stu-id="9f64d-112">If a fault is not handled within the workflow it results in an unhandled exception at the workflow instance and the workflow instance is aborted.</span></span> <span data-ttu-id="9f64d-113">Profil sledování musí zjistit podrobnosti o neošetřené výjimce dotaz na záznam instance pracovního postupu s `state name="UnhandledException"` jak je uvedeno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="9f64d-113">To understand the details of the unhandled exception, the tracking profile must query the workflow instance record with `state name="UnhandledException"` as specified in the following example.</span></span>  
  
```xml  
<workflowInstanceQueries>  
              <workflowInstanceQuery>  
                <states>  
                  <state name="UnhandledException" />  
                </states>  
              </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
 <span data-ttu-id="9f64d-114">Když dojde k neošetřené výjimce instanci pracovního postupu <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord> objektu je vygenerované Pokud [!INCLUDE[wf2](../../../includes/wf2-md.md)] bylo povoleno sledování.</span><span class="sxs-lookup"><span data-stu-id="9f64d-114">When a workflow instance encounters an unhandled exception, a <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord> object is emitted if [!INCLUDE[wf2](../../../includes/wf2-md.md)] tracking has been enabled.</span></span>  
  
 <span data-ttu-id="9f64d-115">Tento záznam sledování obsahuje v podrobnostech o chybě ve formě zásobník výjimek.</span><span class="sxs-lookup"><span data-stu-id="9f64d-115">This tracking record contains the fault details in the form of the exception stack.</span></span> <span data-ttu-id="9f64d-116">Obsahuje podrobnosti o zdroj selhání (například aktivita), který došlo k chybě a výsledkem neošetřených výjimek. Přihlásit k odběru událostí selhání z [!INCLUDE[wf2](../../../includes/wf2-md.md)], povolit sledování přidáním účastník sledování.</span><span class="sxs-lookup"><span data-stu-id="9f64d-116">It has details of the source of the fault (for example, the activity) that faulted and resulted in the unhandled exception.To subscribe to fault events from a [!INCLUDE[wf2](../../../includes/wf2-md.md)], enable tracking by adding a tracking participant.</span></span> <span data-ttu-id="9f64d-117">Tento účastník nakonfigurovat sledování profil, který se dotazuje na `ActivityStateQuery (state="Faulted")`, <xref:System.Activities.Tracking.FaultPropagationRecord>, a `WorkflowInstanceQuery (state="UnhandledException")`.</span><span class="sxs-lookup"><span data-stu-id="9f64d-117">Configure this participant with a tracking profile that queries for `ActivityStateQuery (state="Faulted")`, <xref:System.Activities.Tracking.FaultPropagationRecord>, and `WorkflowInstanceQuery (state="UnhandledException")`.</span></span>  
  
 <span data-ttu-id="9f64d-118">Pokud je povoleno sledování pomocí účastník sledování trasování událostí pro Windows, jsou události chyby vygenerované relaci trasování událostí pro Windows.</span><span class="sxs-lookup"><span data-stu-id="9f64d-118">If tracking is enabled using the ETW tracking participant, the fault events are emitted to an ETW session.</span></span> <span data-ttu-id="9f64d-119">Události lze zobrazit pomocí prohlížeče událostí Prohlížeč událostí.</span><span class="sxs-lookup"><span data-stu-id="9f64d-119">The events can be viewed using the Event Viewer event viewer.</span></span> <span data-ttu-id="9f64d-120">To lze nalézt v uzlu **Prohlížeč událostí -> aplikace a protokoly služby -> Microsoft -> Windows -> serveru aplikace – aplikace** v analytické kanál.</span><span class="sxs-lookup"><span data-stu-id="9f64d-120">This can be found under the node **Event Viewer->Applications and Services Logs->Microsoft->Windows->Application Server-Applications** in the analytic channel.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f64d-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="9f64d-121">See Also</span></span>  
 [<span data-ttu-id="9f64d-122">Windows Server App Fabric monitorování</span><span class="sxs-lookup"><span data-stu-id="9f64d-122">Windows Server App Fabric Monitoring</span></span>](http://go.microsoft.com/fwlink/?LinkId=201273)  
 [<span data-ttu-id="9f64d-123">Monitorování aplikací pomocí App Fabric</span><span class="sxs-lookup"><span data-stu-id="9f64d-123">Monitoring Applications with App Fabric</span></span>](http://go.microsoft.com/fwlink/?LinkId=201275)
