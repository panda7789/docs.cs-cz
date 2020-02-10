---
title: Knihovna aktivit
ms.date: 03/30/2017
ms.assetid: 5323e9d4-71d6-47eb-bfa6-31feac62044d
ms.openlocfilehash: ce65bf8e7adad6acefd7aac6d69c3f836b94be29
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/09/2020
ms.locfileid: "77094693"
---
# <a name="activity-library"></a><span data-ttu-id="b87ac-102">Knihovna aktivit</span><span class="sxs-lookup"><span data-stu-id="b87ac-102">Activity Library</span></span>
<span data-ttu-id="b87ac-103">V této části najdete ukázky, které ukazují rozšířené vlastní aktivity v programovací model Windows Workflow Foundation (WF).</span><span class="sxs-lookup"><span data-stu-id="b87ac-103">This section contains samples that demonstrate advanced custom activities in Windows Workflow Foundation (WF).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b87ac-104">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="b87ac-104">In This Section</span></span>

 [<span data-ttu-id="b87ac-105">Vlastní aktivita SendMail</span><span class="sxs-lookup"><span data-stu-id="b87ac-105">SendMail Custom Activity</span></span>](sendmail-custom-activity.md)  
 <span data-ttu-id="b87ac-106">Ukazuje, jak vytvořit vlastní aktivitu, která je odvozena z <xref:System.Activities.AsyncCodeActivity> k odeslání e-mailu pomocí protokolu SMTP pro použití v rámci aplikace pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="b87ac-106">Demonstrates how to create a custom activity that derives from <xref:System.Activities.AsyncCodeActivity> to send mail using SMTP for use within a workflow application.</span></span>  
  
 [<span data-ttu-id="b87ac-107">Aktivita ThrottledParallelForEach</span><span class="sxs-lookup"><span data-stu-id="b87ac-107">Throttled Parallel ForEach</span></span>](throttled-parallel-foreach.md)  
 <span data-ttu-id="b87ac-108">Ukazuje, jak je aktivita `ThrottleParallelForEach` podobná aktivitě <xref:System.Activities.Statements.ParallelForEach%601> s jedinou výjimkou, kterou umožňuje nastavit faktor souběžnosti k omezení počtu souběžných větví, které mají být spuštěny.</span><span class="sxs-lookup"><span data-stu-id="b87ac-108">Demonstrates how the `ThrottleParallelForEach` activity is similar to the <xref:System.Activities.Statements.ParallelForEach%601> activity with the one exception that it allows setting a concurrency factor to restrict the number of simultaneous branches to execute.</span></span>
  
 [<span data-ttu-id="b87ac-109">Aktivity přístupu k databázi</span><span class="sxs-lookup"><span data-stu-id="b87ac-109">Database Access Activities</span></span>](database-access-activities.md)  
 <span data-ttu-id="b87ac-110">Ukazuje, jak vytvořit aktivity, které umožňují přístup k databázím načíst nebo upravit informace a používat [ADO.NET](../../data/adonet/index.md) pro přístup k databázi.</span><span class="sxs-lookup"><span data-stu-id="b87ac-110">Demonstrates how to create activities that allow accessing databases to retrieve or modify information and use [ADO.NET](../../data/adonet/index.md) to access the database.</span></span>  
  
 [<span data-ttu-id="b87ac-111">Externalizovaná aktivita Policy v rozhraní .NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="b87ac-111">Externalized Policy Activity in .NET Framework 4.5</span></span>](externalized-policy-activity-in-net-framework-4-5.md)  
 <span data-ttu-id="b87ac-112">Ukazuje, jak aktivita ExternalizedPolicy4 umožňuje spouštět existující programovací model Windows Workflow Foundation v .NET Framework 3,5 (WF 3,5) <xref:System.Workflow.Activities.Rules.RuleSet> objektů v programovací model Windows Workflow Foundation v [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] (WF 4,5) přímo pomocí modulu pravidel, který je dodán v WF 3,5.</span><span class="sxs-lookup"><span data-stu-id="b87ac-112">Demonstrates how the ExternalizedPolicy4 activity allows executing existing Windows Workflow Foundation in .NET Framework 3.5 (WF 3.5) <xref:System.Workflow.Activities.Rules.RuleSet> objects in Windows Workflow Foundation in [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] (WF 4.5) directly by using the rules engine that is shipped in WF 3.5.</span></span> 
  
 [<span data-ttu-id="b87ac-113">Neobecná aktivita ForEach</span><span class="sxs-lookup"><span data-stu-id="b87ac-113">Non-Generic ForEach</span></span>](non-generic-foreach.md)  
 <span data-ttu-id="b87ac-114">Ukazuje, jak vytvořit neobecnou verzi aktivity <xref:System.Activities.Statements.ForEach%601>.</span><span class="sxs-lookup"><span data-stu-id="b87ac-114">Demonstrates how to create a non-generic version of the <xref:System.Activities.Statements.ForEach%601> activity.</span></span>  
  
 [<span data-ttu-id="b87ac-115">Neobecná aktivita ParallelForEach</span><span class="sxs-lookup"><span data-stu-id="b87ac-115">Non-Generic ParallelForEach</span></span>](non-generic-parallelforeach.md)  
 <span data-ttu-id="b87ac-116">Ukazuje, jak vytvořit neobecnou verzi aktivity <xref:System.Activities.Statements.ParallelForEach%601>.</span><span class="sxs-lookup"><span data-stu-id="b87ac-116">Demonstrates how to create a non-generic version of the <xref:System.Activities.Statements.ParallelForEach%601> activity.</span></span>  
  
 [<span data-ttu-id="b87ac-117">Získání WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="b87ac-117">Get WorkflowInstanceId</span></span>](get-workflowinstanceid.md)  
 <span data-ttu-id="b87ac-118">Ukazuje, jak použít vlastní aktivitu `GetWorkflowInstanceId`k vrácení ID instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="b87ac-118">Demonstrates how to use the custom activity, `GetWorkflowInstanceId`, to return the workflow instance ID.</span></span>
