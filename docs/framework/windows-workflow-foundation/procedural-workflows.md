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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 9e8f517b68695457c2819612bbd092b5ea03c5f5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="procedural-workflows"></a><span data-ttu-id="20ceb-102">Procedurální pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="20ceb-102">Procedural Workflows</span></span>
<span data-ttu-id="20ceb-103">Procedurální pracovní postupy používající řízení toku metody, které jsou podobné těm, které jsou součástí procedurální jazyky.</span><span class="sxs-lookup"><span data-stu-id="20ceb-103">Procedural workflows use flow-control methods similar to those found in procedural languages.</span></span> <span data-ttu-id="20ceb-104">Tyto konstrukce obsahují `While` a `If`.</span><span class="sxs-lookup"><span data-stu-id="20ceb-104">These constructs include `While` and `If`.</span></span> <span data-ttu-id="20ceb-105">Tyto pracovní postupy můžete volně sestavit pomocí jiné aktivity toku řízení, jako třeba <xref:System.Activities.Statements.Flowchart> a <xref:System.Activities.Statements.Sequence>.</span><span class="sxs-lookup"><span data-stu-id="20ceb-105">These workflows can be freely composed using other flow control activities such as <xref:System.Activities.Statements.Flowchart> and <xref:System.Activities.Statements.Sequence>.</span></span>  
  
## <a name="controlling-execution-flow"></a><span data-ttu-id="20ceb-106">Řízení toku provádění</span><span class="sxs-lookup"><span data-stu-id="20ceb-106">Controlling Execution Flow</span></span>  
 <span data-ttu-id="20ceb-107">Knihovna aktivit pracovního postupu má aktivity pro modelování většinu metod řízení toku procedurální jazyků.</span><span class="sxs-lookup"><span data-stu-id="20ceb-107">The workflow activity library has activities for modeling most flow-control methods used in procedural languages.</span></span> <span data-ttu-id="20ceb-108">Mezi ně patří:</span><span class="sxs-lookup"><span data-stu-id="20ceb-108">These include:</span></span>  
  
-   <xref:System.Activities.Statements.While>  
  
-   <xref:System.Activities.Statements.DoWhile>  
  
-   <xref:System.Activities.Statements.ForEach%601>  
  
-   <xref:System.Activities.Statements.Parallel>  
  
-   <xref:System.Activities.Statements.ParallelForEach%601>  
  
-   <xref:System.Activities.Statements.If>  
  
-   <xref:System.Activities.Statements.Switch%601>  
  
-   <xref:System.Activities.Statements.Pick>  
  
 <span data-ttu-id="20ceb-109">Pokud chcete používat aktivity toku řízení, přetažení z **aktivity** nástrojů do složených aktivit v okně návrháře.</span><span class="sxs-lookup"><span data-stu-id="20ceb-109">To use flow control activities, drag and drop them from the **Activity** toolbox into a composite activity inside the designer window.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="20ceb-110">Pokud se používá [!INCLUDE[dublin](../../../includes/dublin-md.md)] pracovní postupy hostitele ve webové farmě, AppFabric přesune mezi různými servery AppFabric instancí.</span><span class="sxs-lookup"><span data-stu-id="20ceb-110">If using the [!INCLUDE[dublin](../../../includes/dublin-md.md)] to host workflows on a Web farm, AppFabric will move instances between different AppFabric servers.</span></span> <span data-ttu-id="20ceb-111">To vyžaduje, aby mohly být sdílen mezi všemi uzly prostředky.</span><span class="sxs-lookup"><span data-stu-id="20ceb-111">This requires that the resources are able to be shared between all nodes.</span></span>  <span data-ttu-id="20ceb-112">Žádný výchozí aktivity pracovního postupu NET 4 neobsahuje žádné operace, které přístup k místním prostředkům.</span><span class="sxs-lookup"><span data-stu-id="20ceb-112">None of the default NET 4 workflow activities contain any operations that access local resources.</span></span> <span data-ttu-id="20ceb-113">Vzhledem k tomu, že AppFabric nenabízí žádné mechanismus označit jako nejširší pracovní postup, nesmí vývojář vytvořit vlastní aktivity, které nesplní, když je přesunut pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="20ceb-113">Since AppFabric does not offer any mechanism to mark a workflow as immovable, a developer must not create custom activities that fail when a workflow is moved.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20ceb-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="20ceb-114">See Also</span></span>  
 [<span data-ttu-id="20ceb-115">Vývojový diagram pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="20ceb-115">Flowchart Workflows</span></span>](../../../docs/framework/windows-workflow-foundation/flowchart-workflows.md)
