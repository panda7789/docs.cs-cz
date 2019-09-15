---
title: Řešení problémů s aplikací pomocí sledování
ms.date: 03/30/2017
ms.assetid: 8851adde-c3c2-4391-9523-d8eb831490af
ms.openlocfilehash: b64b92de9cb36807a2bf1eb7ff57f9f6e1a07156
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2019
ms.locfileid: "70988937"
---
# <a name="using-tracking-to-troubleshoot-applications"></a><span data-ttu-id="1bc2c-102">Řešení problémů s aplikací pomocí sledování</span><span class="sxs-lookup"><span data-stu-id="1bc2c-102">Using Tracking to Troubleshoot Applications</span></span>
<span data-ttu-id="1bc2c-103">Programovací model Windows Workflow Foundation (WF) umožňuje sledovat informace související s pracovním postupem a poskytnout tak podrobné informace o spuštění programovací model Windows Workflow Foundation aplikace nebo služby.</span><span class="sxs-lookup"><span data-stu-id="1bc2c-103">Windows Workflow Foundation (WF) enables you to track workflow-related information to give details into the execution of a Windows Workflow Foundation application or service.</span></span> <span data-ttu-id="1bc2c-104">Programovací model Windows Workflow Foundation hostitelé můžou zachytit události pracovního postupu během provádění instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="1bc2c-104">Windows Workflow Foundation hosts are able to capture workflow events during the execution of a workflow instance.</span></span> <span data-ttu-id="1bc2c-105">Pokud váš pracovní postup generuje chyby nebo výjimky, můžete použít informace o sledování programovací model Windows Workflow Foundation k řešení potíží se zpracováním.</span><span class="sxs-lookup"><span data-stu-id="1bc2c-105">If your workflow generates faults or exceptions, you can use the Windows Workflow Foundation tracking details to troubleshooting its processing.</span></span>  
  
## <a name="troubleshooting-a-wf-using-wf-tracking"></a><span data-ttu-id="1bc2c-106">Řešení potíží s WF pomocí sledování WF</span><span class="sxs-lookup"><span data-stu-id="1bc2c-106">Troubleshooting a WF using WF Tracking</span></span>  
 <span data-ttu-id="1bc2c-107">Chcete-li zjistit chyby v rámci zpracování aktivity programovací model Windows Workflow Foundation, můžete povolit sledování pomocí sledovacího profilu, který <xref:System.Activities.Tracking.ActivityStateRecord> se dotazuje pro stav s chybou.</span><span class="sxs-lookup"><span data-stu-id="1bc2c-107">To detect faults within the processing of a Windows Workflow Foundation activity, you can enable tracking with a tracking profile that queries for an <xref:System.Activities.Tracking.ActivityStateRecord> with the state of Faulted.</span></span> <span data-ttu-id="1bc2c-108">Odpovídající dotaz je uveden v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="1bc2c-108">The corresponding query is specified in the following code.</span></span>  
  
```xml  
<activityStateQueries>  
              <activityStateQuery activityName="*">  
                <states>  
                  <state name="Faulted" />  
                </states>  
              </activityStateQuery>  
 </activityStateQueries>  
```  
  
 <span data-ttu-id="1bc2c-109">Pokud je chyba šířena a zpracována v obslužné rutině chyby (například <xref:System.Activities.Statements.TryCatch> aktivita), lze ji zjistit <xref:System.Activities.Tracking.FaultPropagationRecord>pomocí.</span><span class="sxs-lookup"><span data-stu-id="1bc2c-109">If a fault is propagated and handled within a fault handler (such as a <xref:System.Activities.Statements.TryCatch> activity) this can be detected using a <xref:System.Activities.Tracking.FaultPropagationRecord>.</span></span> <span data-ttu-id="1bc2c-110"><xref:System.Activities.Tracking.FaultPropagationRecord> Určuje zdrojovou aktivitu chyby a název obslužné rutiny chyby.</span><span class="sxs-lookup"><span data-stu-id="1bc2c-110">The <xref:System.Activities.Tracking.FaultPropagationRecord> indicates the source activity of the fault and the name of the fault handler.</span></span> <span data-ttu-id="1bc2c-111"><xref:System.Activities.Tracking.FaultPropagationRecord> Obsahuje podrobnosti o chybě ve formě zásobníku výjimek pro chybu.</span><span class="sxs-lookup"><span data-stu-id="1bc2c-111">The <xref:System.Activities.Tracking.FaultPropagationRecord> contains fault details in form of the exception stack for the fault.</span></span> <span data-ttu-id="1bc2c-112">V následujícím příkladu se zobrazí dotaz <xref:System.Activities.Tracking.FaultPropagationRecord> pro přihlášení k odběru.</span><span class="sxs-lookup"><span data-stu-id="1bc2c-112">The query to subscribe for a <xref:System.Activities.Tracking.FaultPropagationRecord> is shown in the following example.</span></span>  
  
```xml  
<faultPropagationQueries>  
              <faultPropagationQuery faultSourceActivityName ="*" faultHandlerActivityName="*"/>  
 </faultPropagationQueries>  
```  
  
 <span data-ttu-id="1bc2c-113">Pokud chyba není zpracována v pracovním postupu, výsledkem je Neošetřená výjimka instance pracovního postupu a instance pracovního postupu byla přerušena.</span><span class="sxs-lookup"><span data-stu-id="1bc2c-113">If a fault is not handled within the workflow it results in an unhandled exception at the workflow instance and the workflow instance is aborted.</span></span> <span data-ttu-id="1bc2c-114">Pro pochopení podrobností o neošetřené výjimce musí profil sledování zadat dotaz na záznam `state name="UnhandledException"` instance pracovního postupu, jak je uvedeno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="1bc2c-114">To understand the details of the unhandled exception, the tracking profile must query the workflow instance record with `state name="UnhandledException"` as specified in the following example.</span></span>  
  
```xml  
<workflowInstanceQueries>  
              <workflowInstanceQuery>  
                <states>  
                  <state name="UnhandledException" />  
                </states>  
              </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
 <span data-ttu-id="1bc2c-115">Když instance pracovního postupu nalezne neošetřenou výjimku, <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord> objekt se vygeneruje, pokud je povolené sledování programovací model Windows Workflow Foundation.</span><span class="sxs-lookup"><span data-stu-id="1bc2c-115">When a workflow instance encounters an unhandled exception, a <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord> object is emitted if Windows Workflow Foundation tracking has been enabled.</span></span>  
  
 <span data-ttu-id="1bc2c-116">Tento záznam sledování obsahuje podrobnosti o chybě ve formě zásobníku výjimek.</span><span class="sxs-lookup"><span data-stu-id="1bc2c-116">This tracking record contains the fault details in the form of the exception stack.</span></span> <span data-ttu-id="1bc2c-117">Obsahuje podrobnosti o zdroji chyby (například aktivity), která byla způsobena chybou a vznikla v neošetřené výjimce. Chcete-li se přihlásit k odběru událostí selhání z programovací model Windows Workflow Foundation, povolte sledování přidáním účastníka sledování.</span><span class="sxs-lookup"><span data-stu-id="1bc2c-117">It has details of the source of the fault (for example, the activity) that faulted and resulted in the unhandled exception.To subscribe to fault events from a Windows Workflow Foundation, enable tracking by adding a tracking participant.</span></span> <span data-ttu-id="1bc2c-118">Nakonfigurujte tohoto účastníka se sledovacím profilem, `ActivityStateQuery (state="Faulted")`který <xref:System.Activities.Tracking.FaultPropagationRecord>se dotazuje na, a `WorkflowInstanceQuery (state="UnhandledException")`.</span><span class="sxs-lookup"><span data-stu-id="1bc2c-118">Configure this participant with a tracking profile that queries for `ActivityStateQuery (state="Faulted")`, <xref:System.Activities.Tracking.FaultPropagationRecord>, and `WorkflowInstanceQuery (state="UnhandledException")`.</span></span>  
  
 <span data-ttu-id="1bc2c-119">Pokud je povoleno sledování pomocí účastníka sledování ETW, události selhání se generují do relace ETW.</span><span class="sxs-lookup"><span data-stu-id="1bc2c-119">If tracking is enabled using the ETW tracking participant, the fault events are emitted to an ETW session.</span></span> <span data-ttu-id="1bc2c-120">Události lze zobrazit pomocí Prohlížeč událostí prohlížeč událostí.</span><span class="sxs-lookup"><span data-stu-id="1bc2c-120">The events can be viewed using the Event Viewer event viewer.</span></span> <span data-ttu-id="1bc2c-121">Tuto možnost najdete pod uzlem **Prohlížeč událostí > protokoly aplikací a služeb – > Microsoft-> Windows-> aplikační server – aplikace** v analytickém kanálu.</span><span class="sxs-lookup"><span data-stu-id="1bc2c-121">This can be found under the node **Event Viewer->Applications and Services Logs->Microsoft->Windows->Application Server-Applications** in the analytic channel.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1bc2c-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1bc2c-122">See also</span></span>

- [<span data-ttu-id="1bc2c-123">Monitorování Windows Server App Fabric</span><span class="sxs-lookup"><span data-stu-id="1bc2c-123">Windows Server App Fabric Monitoring</span></span>](https://go.microsoft.com/fwlink/?LinkId=201273)
- [<span data-ttu-id="1bc2c-124">Monitorování aplikací pomocí prostředků infrastruktury aplikace</span><span class="sxs-lookup"><span data-stu-id="1bc2c-124">Monitoring Applications with App Fabric</span></span>](https://go.microsoft.com/fwlink/?LinkId=201275)
