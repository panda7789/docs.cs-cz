---
title: "Procedurální pracovních postupů"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 52401de9-9115-472d-8fd9-047af6a072b9
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: cd879d138a95c003ca0ffb12b3ce010534c3e158
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="procedural-workflows"></a><span data-ttu-id="114fd-102">Procedurální pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="114fd-102">Procedural Workflows</span></span>
<span data-ttu-id="114fd-103">Procedurální pracovní postupy používající řízení toku metody, které jsou podobné těm, které jsou součástí procedurální jazyky.</span><span class="sxs-lookup"><span data-stu-id="114fd-103">Procedural workflows use flow-control methods similar to those found in procedural languages.</span></span> <span data-ttu-id="114fd-104">Tyto konstrukce obsahují `While` a `If`.</span><span class="sxs-lookup"><span data-stu-id="114fd-104">These constructs include `While` and `If`.</span></span> <span data-ttu-id="114fd-105">Tyto pracovní postupy můžete volně sestavit pomocí jiné aktivity toku řízení, jako třeba <xref:System.Activities.Statements.Flowchart> a <xref:System.Activities.Statements.Sequence>.</span><span class="sxs-lookup"><span data-stu-id="114fd-105">These workflows can be freely composed using other flow control activities such as <xref:System.Activities.Statements.Flowchart> and <xref:System.Activities.Statements.Sequence>.</span></span>  
  
## <a name="controlling-execution-flow"></a><span data-ttu-id="114fd-106">Řízení toku provádění</span><span class="sxs-lookup"><span data-stu-id="114fd-106">Controlling Execution Flow</span></span>  
 <span data-ttu-id="114fd-107">Knihovna aktivit pracovního postupu má aktivity pro modelování většinu metod řízení toku procedurální jazyků.</span><span class="sxs-lookup"><span data-stu-id="114fd-107">The workflow activity library has activities for modeling most flow-control methods used in procedural languages.</span></span> <span data-ttu-id="114fd-108">Mezi ně patří:</span><span class="sxs-lookup"><span data-stu-id="114fd-108">These include:</span></span>  
  
-   <xref:System.Activities.Statements.While>  
  
-   <xref:System.Activities.Statements.DoWhile>  
  
-   <xref:System.Activities.Statements.ForEach%601>  
  
-   <xref:System.Activities.Statements.Parallel>  
  
-   <xref:System.Activities.Statements.ParallelForEach%601>  
  
-   <xref:System.Activities.Statements.If>  
  
-   <xref:System.Activities.Statements.Switch%601>  
  
-   <xref:System.Activities.Statements.Pick>  
  
 <span data-ttu-id="114fd-109">Pokud chcete používat aktivity toku řízení, přetažení z **aktivity** nástrojů do složených aktivit v okně návrháře.</span><span class="sxs-lookup"><span data-stu-id="114fd-109">To use flow control activities, drag and drop them from the **Activity** toolbox into a composite activity inside the designer window.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="114fd-110">Pokud se používá [!INCLUDE[dublin](../../../includes/dublin-md.md)] pracovní postupy hostitele ve webové farmě, AppFabric přesune mezi různými servery AppFabric instancí.</span><span class="sxs-lookup"><span data-stu-id="114fd-110">If using the [!INCLUDE[dublin](../../../includes/dublin-md.md)] to host workflows on a Web farm, AppFabric will move instances between different AppFabric servers.</span></span> <span data-ttu-id="114fd-111">To vyžaduje, aby mohly být sdílen mezi všemi uzly prostředky.</span><span class="sxs-lookup"><span data-stu-id="114fd-111">This requires that the resources are able to be shared between all nodes.</span></span>  <span data-ttu-id="114fd-112">Žádný výchozí aktivity pracovního postupu NET 4 neobsahuje žádné operace, které přístup k místním prostředkům.</span><span class="sxs-lookup"><span data-stu-id="114fd-112">None of the default NET 4 workflow activities contain any operations that access local resources.</span></span> <span data-ttu-id="114fd-113">Vzhledem k tomu, že AppFabric nenabízí žádné mechanismus označit jako nejširší pracovní postup, nesmí vývojář vytvořit vlastní aktivity, které nesplní, když je přesunut pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="114fd-113">Since AppFabric does not offer any mechanism to mark a workflow as immovable, a developer must not create custom activities that fail when a workflow is moved.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="114fd-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="114fd-114">See Also</span></span>  
 [<span data-ttu-id="114fd-115">Vývojový diagram pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="114fd-115">Flowchart Workflows</span></span>](../../../docs/framework/windows-workflow-foundation/flowchart-workflows.md)
