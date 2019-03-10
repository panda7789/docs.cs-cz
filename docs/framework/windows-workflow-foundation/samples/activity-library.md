---
title: Knihovna aktivit
ms.date: 03/30/2017
ms.assetid: 5323e9d4-71d6-47eb-bfa6-31feac62044d
ms.openlocfilehash: b701d382c25644181b23f3c0f0cd8e019b8d37d1
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57709833"
---
# <a name="activity-library"></a><span data-ttu-id="d83e2-102">Knihovna aktivit</span><span class="sxs-lookup"><span data-stu-id="d83e2-102">Activity Library</span></span>
<span data-ttu-id="d83e2-103">Tato část obsahuje ukázky, které předvádějí pokročilých vlastních aktivit Windows Workflow Foundation (WF).</span><span class="sxs-lookup"><span data-stu-id="d83e2-103">This section contains samples that demonstrate advanced custom activities in Windows Workflow Foundation (WF).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d83e2-104">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="d83e2-104">In This Section</span></span>

 [<span data-ttu-id="d83e2-105">Vlastní aktivita SendMail</span><span class="sxs-lookup"><span data-stu-id="d83e2-105">SendMail Custom Activity</span></span>](sendmail-custom-activity.md)  
 <span data-ttu-id="d83e2-106">Ukazuje, jak vytvořit vlastní aktivitu, která je odvozena z <xref:System.Activities.AsyncCodeActivity> k odesílání e-mailu pomocí protokolu SMTP pro použití v rámci aplikace pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="d83e2-106">Demonstrates how to create a custom activity that derives from <xref:System.Activities.AsyncCodeActivity> to send mail using SMTP for use within a workflow application.</span></span>  
  
 [<span data-ttu-id="d83e2-107">Aktivita ThrottledParallelForEach</span><span class="sxs-lookup"><span data-stu-id="d83e2-107">Throttled Parallel ForEach</span></span>](throttled-parallel-foreach.md)  
 <span data-ttu-id="d83e2-108">Ukazuje, jak `ThrottleParallelForEach` aktivity se podobá <xref:System.Activities.Statements.ParallelForEach%601> činnost s jednou výjimkou, že umožňuje nastavení faktor souběžnost chcete omezit počet souběžných větve ke spuštění.</span><span class="sxs-lookup"><span data-stu-id="d83e2-108">Demonstrates how the `ThrottleParallelForEach` activity is similar to the <xref:System.Activities.Statements.ParallelForEach%601> activity with the one exception that it allows setting a concurrency factor to restrict the number of simultaneous branches to execute.</span></span>
  
 [<span data-ttu-id="d83e2-109">Aktivity přístupu k databázi</span><span class="sxs-lookup"><span data-stu-id="d83e2-109">Database Access Activities</span></span>](database-access-activities.md)  
 <span data-ttu-id="d83e2-110">Ukazuje, jak vytvořit aktivity, které umožňují přístup k databázím nebo upravte informace a použití [ADO.NET](https://go.microsoft.com/fwlink/?LinkId=166081) pro přístup k databázi.</span><span class="sxs-lookup"><span data-stu-id="d83e2-110">Demonstrates how to create activities that allow accessing databases to retrieve or modify information and use [ADO.NET](https://go.microsoft.com/fwlink/?LinkId=166081) to access the database.</span></span>  
  
 [<span data-ttu-id="d83e2-111">Externalizovaná aktivita Policy v rozhraní .NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="d83e2-111">Externalized Policy Activity in .NET Framework 4.5</span></span>](externalized-policy-activity-in-net-framework-4-5.md)  
 <span data-ttu-id="d83e2-112">Ukazuje, jak aktivity ExternalizedPolicy4 umožňuje provádění stávající Windows Workflow Foundation v [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] (WF 3.5) <xref:System.Workflow.Activities.Rules.RuleSet> objekty v modelu Windows Workflow Foundation v [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] (WF 4.5) přímo pomocí pravidla modul, který je poskytuje WF 3.5.</span><span class="sxs-lookup"><span data-stu-id="d83e2-112">Demonstrates how the ExternalizedPolicy4 activity allows executing existing Windows Workflow Foundation in [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] (WF 3.5) <xref:System.Workflow.Activities.Rules.RuleSet> objects in Windows Workflow Foundation in [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] (WF 4.5) directly by using the rules engine that is shipped in WF 3.5.</span></span> 
  
 [<span data-ttu-id="d83e2-113">Neobecná aktivita ForEach</span><span class="sxs-lookup"><span data-stu-id="d83e2-113">Non-Generic ForEach</span></span>](non-generic-foreach.md)  
 <span data-ttu-id="d83e2-114">Ukazuje, jak vytvořit obecné verzi <xref:System.Activities.Statements.ForEach%601> aktivity.</span><span class="sxs-lookup"><span data-stu-id="d83e2-114">Demonstrates how to create a non-generic version of the <xref:System.Activities.Statements.ForEach%601> activity.</span></span>  
  
 [<span data-ttu-id="d83e2-115">Neobecná aktivita ParallelForEach</span><span class="sxs-lookup"><span data-stu-id="d83e2-115">Non-Generic ParallelForEach</span></span>](non-generic-parallelforeach.md)  
 <span data-ttu-id="d83e2-116">Ukazuje, jak vytvořit obecné verzi <xref:System.Activities.Statements.ParallelForEach%601> aktivity.</span><span class="sxs-lookup"><span data-stu-id="d83e2-116">Demonstrates how to create a non-generic version of the <xref:System.Activities.Statements.ParallelForEach%601> activity.</span></span>  
  
 [<span data-ttu-id="d83e2-117">Získání WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="d83e2-117">Get WorkflowInstanceId</span></span>](get-workflowinstanceid.md)  
 <span data-ttu-id="d83e2-118">Ukazuje, jak použít vlastní aktivitu, `GetWorkflowInstanceId`, který vrátí ID instance pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="d83e2-118">Demonstrates how to use the custom activity, `GetWorkflowInstanceId`, to return the workflow instance ID.</span></span>
