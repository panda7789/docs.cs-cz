---
title: Knihovna aktivit
ms.date: 03/30/2017
ms.assetid: 5323e9d4-71d6-47eb-bfa6-31feac62044d
ms.openlocfilehash: fae2a94b5e5e776625aa7f26700980640b66afd4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142898"
---
# <a name="activity-library"></a><span data-ttu-id="06043-102">Knihovna aktivit</span><span class="sxs-lookup"><span data-stu-id="06043-102">Activity Library</span></span>
<span data-ttu-id="06043-103">Tato část obsahuje ukázky, které ukazují pokročilé vlastní aktivity v základu pracovního postupu systému Windows (WF).</span><span class="sxs-lookup"><span data-stu-id="06043-103">This section contains samples that demonstrate advanced custom activities in Windows Workflow Foundation (WF).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="06043-104">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="06043-104">In This Section</span></span>

 [<span data-ttu-id="06043-105">Vlastní aktivita SendMail</span><span class="sxs-lookup"><span data-stu-id="06043-105">SendMail Custom Activity</span></span>](sendmail-custom-activity.md)  
 <span data-ttu-id="06043-106">Ukazuje, jak vytvořit vlastní aktivitu, <xref:System.Activities.AsyncCodeActivity> která je odvozena od odesílání pošty pomocí protokolu SMTP pro použití v rámci aplikace pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="06043-106">Demonstrates how to create a custom activity that derives from <xref:System.Activities.AsyncCodeActivity> to send mail using SMTP for use within a workflow application.</span></span>  
  
 [<span data-ttu-id="06043-107">Aktivita ThrottledParallelForEach</span><span class="sxs-lookup"><span data-stu-id="06043-107">Throttled Parallel ForEach</span></span>](throttled-parallel-foreach.md)  
 <span data-ttu-id="06043-108">Ukazuje, jak `ThrottleParallelForEach` aktivita je <xref:System.Activities.Statements.ParallelForEach%601> podobná aktivity s jedinou výjimkou, která umožňuje nastavení faktoru souběžnosti omezit počet souběžných větví spustit.</span><span class="sxs-lookup"><span data-stu-id="06043-108">Demonstrates how the `ThrottleParallelForEach` activity is similar to the <xref:System.Activities.Statements.ParallelForEach%601> activity with the one exception that it allows setting a concurrency factor to restrict the number of simultaneous branches to execute.</span></span>
  
 [<span data-ttu-id="06043-109">Aktivity přístupu k databázi</span><span class="sxs-lookup"><span data-stu-id="06043-109">Database Access Activities</span></span>](database-access-activities.md)  
 <span data-ttu-id="06043-110">Ukazuje, jak vytvořit aktivity, které umožňují přístup k databázím načíst nebo upravit informace a použít [ADO.NET](../../data/adonet/index.md) pro přístup k databázi.</span><span class="sxs-lookup"><span data-stu-id="06043-110">Demonstrates how to create activities that allow accessing databases to retrieve or modify information and use [ADO.NET](../../data/adonet/index.md) to access the database.</span></span>  
  
 [<span data-ttu-id="06043-111">Externalizovaná aktivita Policy v rozhraní .NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="06043-111">Externalized Policy Activity in .NET Framework 4.5</span></span>](externalized-policy-activity-in-net-framework-4-5.md)  
 <span data-ttu-id="06043-112">Ukazuje, jak aktivita ExternalizedPolicy4 umožňuje spuštění existujících objektů Windows Workflow Foundation v <xref:System.Workflow.Activities.Rules.RuleSet> rozhraní .NET [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] Framework 3.5 (WF 3.5) v systému Windows Workflow Foundation v (WF 4.5) přímo pomocí modulu pravidel, který je dodáván v wf 3.5.</span><span class="sxs-lookup"><span data-stu-id="06043-112">Demonstrates how the ExternalizedPolicy4 activity allows executing existing Windows Workflow Foundation in .NET Framework 3.5 (WF 3.5) <xref:System.Workflow.Activities.Rules.RuleSet> objects in Windows Workflow Foundation in [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] (WF 4.5) directly by using the rules engine that is shipped in WF 3.5.</span></span>
  
 [<span data-ttu-id="06043-113">Neobecná aktivita ForEach</span><span class="sxs-lookup"><span data-stu-id="06043-113">Non-Generic ForEach</span></span>](non-generic-foreach.md)  
 <span data-ttu-id="06043-114">Ukazuje, jak vytvořit neobecnou verzi <xref:System.Activities.Statements.ForEach%601> aktivity.</span><span class="sxs-lookup"><span data-stu-id="06043-114">Demonstrates how to create a non-generic version of the <xref:System.Activities.Statements.ForEach%601> activity.</span></span>  
  
 [<span data-ttu-id="06043-115">Neobecná aktivita ParallelForEach</span><span class="sxs-lookup"><span data-stu-id="06043-115">Non-Generic ParallelForEach</span></span>](non-generic-parallelforeach.md)  
 <span data-ttu-id="06043-116">Ukazuje, jak vytvořit neobecnou verzi <xref:System.Activities.Statements.ParallelForEach%601> aktivity.</span><span class="sxs-lookup"><span data-stu-id="06043-116">Demonstrates how to create a non-generic version of the <xref:System.Activities.Statements.ParallelForEach%601> activity.</span></span>  
  
 [<span data-ttu-id="06043-117">Získání WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="06043-117">Get WorkflowInstanceId</span></span>](get-workflowinstanceid.md)  
 <span data-ttu-id="06043-118">Ukazuje, jak používat vlastní `GetWorkflowInstanceId`aktivitu , chcete-li vrátit ID instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="06043-118">Demonstrates how to use the custom activity, `GetWorkflowInstanceId`, to return the workflow instance ID.</span></span>
