---
title: Řešení problémů s aplikací pomocí sledování
ms.date: 03/30/2017
ms.assetid: 8851adde-c3c2-4391-9523-d8eb831490af
ms.openlocfilehash: b07e850810734082568ddca9776a72575c986094
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837555"
---
# <a name="using-tracking-to-troubleshoot-applications"></a><span data-ttu-id="ee67b-102">Řešení problémů s aplikací pomocí sledování</span><span class="sxs-lookup"><span data-stu-id="ee67b-102">Using Tracking to Troubleshoot Applications</span></span>
<span data-ttu-id="ee67b-103">Programovací model Windows Workflow Foundation (WF) umožňuje sledovat informace související s pracovním postupem a poskytnout tak podrobné informace o spuštění programovací model Windows Workflow Foundation aplikace nebo služby.</span><span class="sxs-lookup"><span data-stu-id="ee67b-103">Windows Workflow Foundation (WF) enables you to track workflow-related information to give details into the execution of a Windows Workflow Foundation application or service.</span></span> <span data-ttu-id="ee67b-104">Programovací model Windows Workflow Foundation hostitelé můžou zachytit události pracovního postupu během provádění instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="ee67b-104">Windows Workflow Foundation hosts are able to capture workflow events during the execution of a workflow instance.</span></span> <span data-ttu-id="ee67b-105">Pokud váš pracovní postup generuje chyby nebo výjimky, můžete použít informace o sledování programovací model Windows Workflow Foundation k řešení potíží se zpracováním.</span><span class="sxs-lookup"><span data-stu-id="ee67b-105">If your workflow generates faults or exceptions, you can use the Windows Workflow Foundation tracking details to troubleshooting its processing.</span></span>  
  
## <a name="troubleshooting-a-wf-using-wf-tracking"></a><span data-ttu-id="ee67b-106">Řešení potíží s WF pomocí sledování WF</span><span class="sxs-lookup"><span data-stu-id="ee67b-106">Troubleshooting a WF using WF Tracking</span></span>  
 <span data-ttu-id="ee67b-107">Chcete-li zjistit chyby v rámci zpracování aktivity programovací model Windows Workflow Foundation, můžete povolit sledování pomocí sledovacího profilu, který se dotazuje na <xref:System.Activities.Tracking.ActivityStateRecord> se stavem Chyba.</span><span class="sxs-lookup"><span data-stu-id="ee67b-107">To detect faults within the processing of a Windows Workflow Foundation activity, you can enable tracking with a tracking profile that queries for an <xref:System.Activities.Tracking.ActivityStateRecord> with the state of Faulted.</span></span> <span data-ttu-id="ee67b-108">Odpovídající dotaz je uveden v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="ee67b-108">The corresponding query is specified in the following code.</span></span>  
  
```xml  
<activityStateQueries>  
              <activityStateQuery activityName="*">  
                <states>  
                  <state name="Faulted" />  
                </states>  
              </activityStateQuery>  
 </activityStateQueries>  
```  
  
 <span data-ttu-id="ee67b-109">Pokud je chyba šířena a zpracována v obslužné rutině selhání (například aktivita <xref:System.Activities.Statements.TryCatch>), lze ji zjistit pomocí <xref:System.Activities.Tracking.FaultPropagationRecord>.</span><span class="sxs-lookup"><span data-stu-id="ee67b-109">If a fault is propagated and handled within a fault handler (such as a <xref:System.Activities.Statements.TryCatch> activity) this can be detected using a <xref:System.Activities.Tracking.FaultPropagationRecord>.</span></span> <span data-ttu-id="ee67b-110"><xref:System.Activities.Tracking.FaultPropagationRecord> označuje zdrojovou aktivitu chyby a název obslužné rutiny chyb.</span><span class="sxs-lookup"><span data-stu-id="ee67b-110">The <xref:System.Activities.Tracking.FaultPropagationRecord> indicates the source activity of the fault and the name of the fault handler.</span></span> <span data-ttu-id="ee67b-111"><xref:System.Activities.Tracking.FaultPropagationRecord> obsahuje podrobnosti o chybě ve formě zásobníku výjimek pro chybu.</span><span class="sxs-lookup"><span data-stu-id="ee67b-111">The <xref:System.Activities.Tracking.FaultPropagationRecord> contains fault details in form of the exception stack for the fault.</span></span> <span data-ttu-id="ee67b-112">V následujícím příkladu se zobrazí dotaz pro přihlášení k odběru <xref:System.Activities.Tracking.FaultPropagationRecord>.</span><span class="sxs-lookup"><span data-stu-id="ee67b-112">The query to subscribe for a <xref:System.Activities.Tracking.FaultPropagationRecord> is shown in the following example.</span></span>  
  
```xml  
<faultPropagationQueries>  
              <faultPropagationQuery faultSourceActivityName ="*" faultHandlerActivityName="*"/>  
 </faultPropagationQueries>  
```  
  
 <span data-ttu-id="ee67b-113">Pokud chyba není zpracována v pracovním postupu, výsledkem je Neošetřená výjimka instance pracovního postupu a instance pracovního postupu byla přerušena.</span><span class="sxs-lookup"><span data-stu-id="ee67b-113">If a fault is not handled within the workflow it results in an unhandled exception at the workflow instance and the workflow instance is aborted.</span></span> <span data-ttu-id="ee67b-114">Pro pochopení podrobností o neošetřené výjimce musí profil sledování zadat dotaz na záznam instance pracovního postupu s `state name="UnhandledException"`, jak je uvedeno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="ee67b-114">To understand the details of the unhandled exception, the tracking profile must query the workflow instance record with `state name="UnhandledException"` as specified in the following example.</span></span>  
  
```xml  
<workflowInstanceQueries>  
              <workflowInstanceQuery>  
                <states>  
                  <state name="UnhandledException" />  
                </states>  
              </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
 <span data-ttu-id="ee67b-115">Když instance pracovního postupu narazí na neošetřenou výjimku, vygeneruje se <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord> objekt, pokud je povolené sledování programovací model Windows Workflow Foundation.</span><span class="sxs-lookup"><span data-stu-id="ee67b-115">When a workflow instance encounters an unhandled exception, a <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord> object is emitted if Windows Workflow Foundation tracking has been enabled.</span></span>  
  
 <span data-ttu-id="ee67b-116">Tento záznam sledování obsahuje podrobnosti o chybě ve formě zásobníku výjimek.</span><span class="sxs-lookup"><span data-stu-id="ee67b-116">This tracking record contains the fault details in the form of the exception stack.</span></span> <span data-ttu-id="ee67b-117">Obsahuje podrobnosti o zdroji chyby (například aktivity), která byla způsobena chybou a vznikla v neošetřené výjimce. Chcete-li se přihlásit k odběru událostí selhání z programovací model Windows Workflow Foundation, povolte sledování přidáním účastníka sledování.</span><span class="sxs-lookup"><span data-stu-id="ee67b-117">It has details of the source of the fault (for example, the activity) that faulted and resulted in the unhandled exception.To subscribe to fault events from a Windows Workflow Foundation, enable tracking by adding a tracking participant.</span></span> <span data-ttu-id="ee67b-118">Nakonfigurujte tohoto účastníka se sledovacím profilem, který se dotazuje na `ActivityStateQuery (state="Faulted")`, <xref:System.Activities.Tracking.FaultPropagationRecord>a `WorkflowInstanceQuery (state="UnhandledException")`.</span><span class="sxs-lookup"><span data-stu-id="ee67b-118">Configure this participant with a tracking profile that queries for `ActivityStateQuery (state="Faulted")`, <xref:System.Activities.Tracking.FaultPropagationRecord>, and `WorkflowInstanceQuery (state="UnhandledException")`.</span></span>  
  
 <span data-ttu-id="ee67b-119">Pokud je povoleno sledování pomocí účastníka sledování ETW, události selhání se generují do relace ETW.</span><span class="sxs-lookup"><span data-stu-id="ee67b-119">If tracking is enabled using the ETW tracking participant, the fault events are emitted to an ETW session.</span></span> <span data-ttu-id="ee67b-120">Události lze zobrazit pomocí Prohlížeč událostí prohlížeč událostí.</span><span class="sxs-lookup"><span data-stu-id="ee67b-120">The events can be viewed using the Event Viewer event viewer.</span></span> <span data-ttu-id="ee67b-121">Tuto možnost najdete pod uzlem **Prohlížeč událostí > protokoly aplikací a služeb – > Microsoft-> Windows-> aplikační server – aplikace** v analytickém kanálu.</span><span class="sxs-lookup"><span data-stu-id="ee67b-121">This can be found under the node **Event Viewer->Applications and Services Logs->Microsoft->Windows->Application Server-Applications** in the analytic channel.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee67b-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ee67b-122">See also</span></span>

- <span data-ttu-id="ee67b-123">[Monitorování Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677251(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="ee67b-123">[Windows Server App Fabric Monitoring](https://docs.microsoft.com/previous-versions/appfabric/ee677251(v=azure.10))</span></span>
- <span data-ttu-id="ee67b-124">[Monitorování aplikací pomocí prostředků infrastruktury aplikace](https://docs.microsoft.com/previous-versions/appfabric/ee677276(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="ee67b-124">[Monitoring Applications with App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677276(v=azure.10))</span></span>
