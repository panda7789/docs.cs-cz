---
title: Procedurální pracovní postupy
ms.date: 03/30/2017
ms.assetid: 52401de9-9115-472d-8fd9-047af6a072b9
ms.openlocfilehash: d1edd73b2276d0a3918b61c8da2d04769d09e7c8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69956107"
---
# <a name="procedural-workflows"></a><span data-ttu-id="e591c-102">Procedurální pracovní postupy</span><span class="sxs-lookup"><span data-stu-id="e591c-102">Procedural Workflows</span></span>
<span data-ttu-id="e591c-103">Procedurální pracovní postupy používají metody řízení toku podobné těm, které byly nalezeny v procedurálních jazycích.</span><span class="sxs-lookup"><span data-stu-id="e591c-103">Procedural workflows use flow-control methods similar to those found in procedural languages.</span></span> <span data-ttu-id="e591c-104">Tyto konstrukce zahrnují `While` a `If`.</span><span class="sxs-lookup"><span data-stu-id="e591c-104">These constructs include `While` and `If`.</span></span> <span data-ttu-id="e591c-105">Tyto pracovní postupy mohou být volně tvořeny pomocí jiných aktivit řízení toku <xref:System.Activities.Statements.Flowchart> , <xref:System.Activities.Statements.Sequence>jako jsou a.</span><span class="sxs-lookup"><span data-stu-id="e591c-105">These workflows can be freely composed using other flow control activities such as <xref:System.Activities.Statements.Flowchart> and <xref:System.Activities.Statements.Sequence>.</span></span>  
  
## <a name="controlling-execution-flow"></a><span data-ttu-id="e591c-106">Řízení toku spuštění</span><span class="sxs-lookup"><span data-stu-id="e591c-106">Controlling Execution Flow</span></span>  
 <span data-ttu-id="e591c-107">Knihovna aktivit pracovního postupu obsahuje aktivity pro modelování většiny metod řízení toku používaných v procedurálních jazycích.</span><span class="sxs-lookup"><span data-stu-id="e591c-107">The workflow activity library has activities for modeling most flow-control methods used in procedural languages.</span></span> <span data-ttu-id="e591c-108">Zde jsou některé z nich:</span><span class="sxs-lookup"><span data-stu-id="e591c-108">These include:</span></span>  
  
- <xref:System.Activities.Statements.While>  
  
- <xref:System.Activities.Statements.DoWhile>  
  
- <xref:System.Activities.Statements.ForEach%601>  
  
- <xref:System.Activities.Statements.Parallel>  
  
- <xref:System.Activities.Statements.ParallelForEach%601>  
  
- <xref:System.Activities.Statements.If>  
  
- <xref:System.Activities.Statements.Switch%601>  
  
- <xref:System.Activities.Statements.Pick>  
  
 <span data-ttu-id="e591c-109">Chcete-li používat aktivity řízení toku, přetáhněte je z panelu nástrojů **aktivity** do složené aktivity uvnitř okna návrháře.</span><span class="sxs-lookup"><span data-stu-id="e591c-109">To use flow control activities, drag and drop them from the **Activity** toolbox into a composite activity inside the designer window.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e591c-110">Pokud používáte funkce hostování Windows serveru AppFabric k hostování pracovních postupů ve webové farmě, technologie AppFabric přesune instance mezi různými servery AppFabric.</span><span class="sxs-lookup"><span data-stu-id="e591c-110">If using the hosting features of Windows Server AppFabric to host workflows on a Web farm, AppFabric will move instances between different AppFabric servers.</span></span> <span data-ttu-id="e591c-111">To vyžaduje, aby se prostředky mohly sdílet mezi všemi uzly.</span><span class="sxs-lookup"><span data-stu-id="e591c-111">This requires that the resources are able to be shared between all nodes.</span></span>  <span data-ttu-id="e591c-112">Žádná z výchozích aktivit pracovního postupu NET 4 neobsahuje žádné operace, které přistupují k místním prostředkům.</span><span class="sxs-lookup"><span data-stu-id="e591c-112">None of the default NET 4 workflow activities contain any operations that access local resources.</span></span> <span data-ttu-id="e591c-113">Vzhledem k tomu, že technologie AppFabric nenabízí žádný mechanismus pro označení pracovního postupu jako nemovitého, nemůže vývojář vytvořit vlastní aktivity, které selžou při přesunu pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="e591c-113">Since AppFabric does not offer any mechanism to mark a workflow as immovable, a developer must not create custom activities that fail when a workflow is moved.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e591c-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e591c-114">See also</span></span>

- [<span data-ttu-id="e591c-115">Pracovní postupy vývojového diagramu</span><span class="sxs-lookup"><span data-stu-id="e591c-115">Flowchart Workflows</span></span>](flowchart-workflows.md)
