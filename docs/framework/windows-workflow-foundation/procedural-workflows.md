---
title: Procedurální pracovní postupy
ms.date: 03/30/2017
ms.assetid: 52401de9-9115-472d-8fd9-047af6a072b9
ms.openlocfilehash: fcf50296a8ce3e7e2e0631057467af8a8efd9215
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57715708"
---
# <a name="procedural-workflows"></a><span data-ttu-id="ed65f-102">Procedurální pracovní postupy</span><span class="sxs-lookup"><span data-stu-id="ed65f-102">Procedural Workflows</span></span>
<span data-ttu-id="ed65f-103">Procedurální pracovní postupy používající řízení toku metody podobné těm v jazycích procedury.</span><span class="sxs-lookup"><span data-stu-id="ed65f-103">Procedural workflows use flow-control methods similar to those found in procedural languages.</span></span> <span data-ttu-id="ed65f-104">Tyto konstrukce obsahují `While` a `If`.</span><span class="sxs-lookup"><span data-stu-id="ed65f-104">These constructs include `While` and `If`.</span></span> <span data-ttu-id="ed65f-105">Tyto pracovní postupy mohou být složené volně, například pomocí další aktivity toku řízení <xref:System.Activities.Statements.Flowchart> a <xref:System.Activities.Statements.Sequence>.</span><span class="sxs-lookup"><span data-stu-id="ed65f-105">These workflows can be freely composed using other flow control activities such as <xref:System.Activities.Statements.Flowchart> and <xref:System.Activities.Statements.Sequence>.</span></span>  
  
## <a name="controlling-execution-flow"></a><span data-ttu-id="ed65f-106">Řízení toku provádění</span><span class="sxs-lookup"><span data-stu-id="ed65f-106">Controlling Execution Flow</span></span>  
 <span data-ttu-id="ed65f-107">Knihovna aktivit pracovního postupu má aktivity pro modelování Většina metod řízení toku procedury jazyků.</span><span class="sxs-lookup"><span data-stu-id="ed65f-107">The workflow activity library has activities for modeling most flow-control methods used in procedural languages.</span></span> <span data-ttu-id="ed65f-108">Zde jsou některé z nich:</span><span class="sxs-lookup"><span data-stu-id="ed65f-108">These include:</span></span>  
  
-   <xref:System.Activities.Statements.While>  
  
-   <xref:System.Activities.Statements.DoWhile>  
  
-   <xref:System.Activities.Statements.ForEach%601>  
  
-   <xref:System.Activities.Statements.Parallel>  
  
-   <xref:System.Activities.Statements.ParallelForEach%601>  
  
-   <xref:System.Activities.Statements.If>  
  
-   <xref:System.Activities.Statements.Switch%601>  
  
-   <xref:System.Activities.Statements.Pick>  
  
 <span data-ttu-id="ed65f-109">Použití aktivity toku řízení přetažení z **aktivity** nástrojů do složených aktivit uvnitř okna návrháře.</span><span class="sxs-lookup"><span data-stu-id="ed65f-109">To use flow control activities, drag and drop them from the **Activity** toolbox into a composite activity inside the designer window.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ed65f-110">Pokud se používá [!INCLUDE[dublin](../../../includes/dublin-md.md)] hostitele pracovní postupy ve webové farmě, AppFabric přesune instance mezi různými servery AppFabric.</span><span class="sxs-lookup"><span data-stu-id="ed65f-110">If using the [!INCLUDE[dublin](../../../includes/dublin-md.md)] to host workflows on a Web farm, AppFabric will move instances between different AppFabric servers.</span></span> <span data-ttu-id="ed65f-111">To vyžaduje, že prostředky budou moct sdílet mezi všemi uzly.</span><span class="sxs-lookup"><span data-stu-id="ed65f-111">This requires that the resources are able to be shared between all nodes.</span></span>  <span data-ttu-id="ed65f-112">Žádný výchozí aktivity pracovního postupu NET 4 neobsahuje žádné operace, které přístup k místním prostředkům.</span><span class="sxs-lookup"><span data-stu-id="ed65f-112">None of the default NET 4 workflow activities contain any operations that access local resources.</span></span> <span data-ttu-id="ed65f-113">Protože AppFabric nenabízí každý použitý mechanizmus k označení pracovního postupu jako nemovitostí, vývojář nesmí vytvořit vlastní aktivity, které nesplní při přesunu pracovní postup.</span><span class="sxs-lookup"><span data-stu-id="ed65f-113">Since AppFabric does not offer any mechanism to mark a workflow as immovable, a developer must not create custom activities that fail when a workflow is moved.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed65f-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ed65f-114">See also</span></span>
- [<span data-ttu-id="ed65f-115">Pracovní postupy vývojového diagramu</span><span class="sxs-lookup"><span data-stu-id="ed65f-115">Flowchart Workflows</span></span>](flowchart-workflows.md)
